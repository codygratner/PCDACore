# The File-First Protocol for Autonomous Swarms & Subagents

> **Architectural Pattern**: Zero-loss, timeout-resilient inter-agent transport for deep dialectical reasoning and multi-agent code audits.

---

## ⚡ The Problem: The Streaming Socket Cliff

When orchestrating autonomous AI agent swarms—such as a parent coordinator spawning subagents to conduct deep architectural audits or [Method B+ dialectical evaluations](../README.md)—subagents often generate extensive analytical reports (3,000 to 5,000+ words).

In tool-using agent runtimes (Antigravity, Claude Code, Cursor, Cline, OpenHands), inter-agent communication typically relies on messaging tools (`send_message`, `task_finish`, or parent IPC) piped over **HTTP Server-Sent Events (SSE)** or reverse proxy sockets.

### The Failure Vector:
```
[ Subagent Model ] ──► (Generates 25KB Markdown String inside JSON argument)
                            │
                            ├── 60s - 120s Streaming Window (High cluster load / deep reasoning)
                            │
                            ▼
               [ HTTP Reverse Proxy / SSE Buffer ]
                            │
                     ⚠️ SOCKET TIMEOUT / EOF
                            │
               ❌ "The stream was interrupted"
               ❌ "Model unavailable"
```

1. **Proxy Timeouts**: Under heavy cluster load or extended reasoning chains, streaming a 20KB+ JSON string parameter can exceed reverse proxy idle socket thresholds (typically 60–120 seconds).
2. **Buffer Dropouts**: If the connection breaks before the JSON argument closes, the entire generation is lost.
3. **Context Window Pollution**: If the large text payload *does* transmit successfully through chat strings, it immediately clutters the parent agent's context window, burning tokens and accelerating context compaction degradation.

---

## 🛡️ The Architectural Solution: File-First Transport

The **File-First Protocol** decouples *analytical content generation* from *agent communication signaling*. 

Instead of treating the chat message bus as a bulk data pipe, the message bus is treated strictly as an **ephemeral control plane**, while the local filesystem acts as the **durable data plane**.

```
┌────────────────────────────────────────────────────────────────────────┐
│                      FILE-FIRST AGENT PIPELINE                         │
└────────────────────────────────────────────────────────────────────────┘

 [ Subagent Evaluator ]
          │
          │  1. write_to_file("reports/audit_01.md", <Complete 25KB Report>)
          ├────────────────────────────────────────────────────────────────► [ Local Disk ]
          │     (Atomic Write · Safe from Network Timeouts)                       │
          │                                                                       │
          │  2. send_message("ParentAgent", "Audit complete: reports/audit_01.md")│
          ▼     (Terse 100-byte completion signal)                                │
 [ Parent Coordinator ]                                                           │
          │                                                                       │
          │  3. view_file("reports/audit_01.md")                                  │
          └───────────────────────────────────────────────────────────────────────┘
```

---

## 📋 The 3 Operational Invariants

### 1. Atomic Disk Staging
Subagents are strictly forbidden from passing long markdown essays, benchmarks, or code implementations directly into message arguments. The subagent MUST write the complete artifact to a designated report directory on disk (e.g., `docs/reports/` or `staging/`) before signaling the parent.

### 2. Terse Control Pings
The subagent's message tool call is restricted to a 1–2 sentence operational notification containing:
- Execution status (`COMPLETE` or `FAILED`).
- Target file URI / absolute path.
- Executive TL;DR verdict (1 sentence).

```json
{
  "name": "send_message",
  "args": {
    "Recipient": "parent-coordinator",
    "Message": "Hegelian dialectical audit complete (18,240 bytes). Artifact committed to docs/benchmarks/reports/argon-B.md. Executive Verdict: Replace legacy backend via Strangler Pattern."
  }
}
```

### 3. Asymmetric Parent Consumption
The parent agent receives a clean, lightweight notification. It can then:
- Read the entire report using local file viewing tools (`view_file`).
- Or read only targeted sections/lines to keep its main context window pristine.

---

## 🚀 Key Advantages

| Metric | Direct Chat Streaming | File-First Protocol |
| :--- | :--- | :--- |
| **Timeout Vulnerability** | High (fails on proxy socket drops) | **Zero** (file is persisted locally before signal) |
| **Context Window Consumption** | Massive (2,000–8,000 tokens per subagent) | **Minimal** (<100 tokens per completion ping) |
| **Audit Trail & Git Tracking** | Ephemeral (lost in chat transcripts) | **Durable** (persisted as native versioned Markdown) |
| **Parallel Swarm Scalability** | Low (socket contention & token saturation) | **High** (N subagents write in parallel to disk) |

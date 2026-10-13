# PCDACore (v1.0.0)
> **The Standalone Cognitive Shield for AI Pair-Programming: Constructive Adversarial Dialectics (Method B+) with Zero Dependencies.**

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-0-brightgreen.svg)](#)
[![Format](https://img.shields.io/badge/Format-<50%20Lines%20Markdown-orange.svg)](#)

---

## The Problem: The Two Traps of Modern AI Coding

When developers use frontier LLMs (Claude, Gemini, GPT-4) for architectural decisions, they reliably fall into one of two systematic traps:

```
          [ Standard AI Pair-Programming ]
                         |
         +---------------+---------------+
         |                               |
         v                               v
[ Trap 1: The Sycophant ]       [ Trap 2: The Cynic ]
RLHF bias to please the user    Unchecked Devil's Advocate
Validates catastrophic rewrites Tears down every proposal
"Looks great! Here is the code" 10 fatal flaws, 0 alternatives
         |                               |
         +---------------+---------------+
                         |
                         v
       [ Result: Burned Time & Paralysis ]
```

1. **Trap 1: The Sycophancy / Rubber-Stamp Trap**: Frontier models undergo extensive RLHF (Reinforcement Learning from Human Feedback) training to be polite, helpful, and submissive. If you say *"I'm thinking of rewriting our real-time audio engine in TypeScript"*, an uncalibrated LLM will reply: *"That sounds like an exciting modern experiment! Here's how to start..."*
2. **Trap 2: The Cynical Auditor Trap**: Directing a model to *"be brutal"* or *"play devil's advocate"* causes it to tear down every proposal to death, inventing obscure cosmic-ray failure modes while leaving the developer stranded with zero viable solutions.

---

## The Solution: Method B+ (Constructive Adversarial Synthesis)

**PCDACore** is a standalone, <50-line markdown rule enforcing the **Method B+ Hegelian Dialectic** (Thesis ➔ Antithesis ➔ Synthesis) directly inside your AI pair-programmer's system prompt:

```
[ THESIS ]              [ ANTITHESIS ]              [ SYNTHESIS ]
Pros & Velocity  ➔   Devil's Advocate Traps  ➔   80/20 Lateral Solution
What works today     "Where I Disagree"          Deliver 100% of intent
                     Worst-case 6-month drop     with 20% of complexity
```

### The Two Non-Negotiable Invariants:
1. **"Where I Disagree With The Prompt"**: Prior to evaluating options, the model MUST attack the user's premises. It flags loaded questions, sunk-cost fallacies, premature optimization, and unverified assumptions.
2. **"Steel-Manned Intent & Constructive Lateral Alternatives"**: The model separates the user's *root goal* from their *flawed mechanism*. If the proposed mechanism is rejected, the model **MUST invent a concrete, low-cost lateral alternative delivering 100% of the intent**.

---

## ⚡ 1-Minute Quick Start

### 1. Copy into Your AI Assistant Rules

Choose your tool:

#### Option A: Cursor (`.cursorrules`)
Copy the contents of [`PCDACore.md`](PCDACore.md) into the root `.cursorrules` file of your project.

#### Option B: Google Gemini CLI (`GEMINI.md`)
Append [`PCDACore.md`](PCDACore.md) into `GEMINI.md` in your workspace root.

#### Option C: Claude Code / Anthropic (`CLAUDE.md`)
Append [`PCDACore.md`](PCDACore.md) into `CLAUDE.md`.

#### Option D: OpenAI / Custom Agent Framework (`AGENTS.md`)
Append [`PCDACore.md`](PCDACore.md) into your system prompt or `AGENTS.md`.

---

## 🎯 How to Use in Chat

PCDACore is **strictly silent by default** on routine turns (it never interrupts basic syntax questions or 1-line lookups).

To unleash the dialectic, prefix your prompt with `PCDA:`, `/pcda`, or ask for tradeoffs:

```text
PCDA: Should we migrate our SQLite database to a distributed microservice?
```

### Example Model Response Format:

```markdown
### 1. Pros [Thesis]
- Immediate horizontal read scalability across edge nodes.
- Isolated failure domains per service tenant.

### 2. Cons [Thesis Friction]
- Introduces network partition handling (CAP theorem).
- 5x increase in operational complexity (Kubernetes, distributed tracing).

### 3. Devil's Advocate [Antithesis & Systemic Traps]
- **Where I Disagree With The Prompt**: You currently have 400 daily active users and 12 MB of SQLite data. Microservices solve organizational team scale (Conway's Law), not database throughput at your stage.
- **Worst-Case Production Trap**: You spend 3 months writing gRPC plumbing and lose ACID transaction integrity during outages.
- **Unverified Assumptions**: Premise that SQLite is the bottleneck is unverified without profiling.

### 4. The 80/20 Resolution [Synthesis & Invariant]
- **Steel-Manned Intent**: Zero-downtime backups and read-heavy concurrency.
- **Constructive Lateral Alternative**: Enable SQLite WAL mode (`PRAGMA journal_mode=WAL;`) with Litestream for continuous S3 streaming replica. Delivers 100% of durability with 0 new microservices.
- **The Invariant**: Assert WAL mode in DB boot test.
```

---

## 🔬 Pluggable Domain Lenses

PCDACore includes 4 domain-tailored lens sets in [`lenses.json`](lenses.json):

| Domain Profile | Primary Evaluation Lenses |
| :--- | :--- |
| **Systems Engineering** *(Default)* | Developer Ergonomics · Industry SOTA · Architecture & Coupling · Long-Term Sustainability |
| **Audio & DSP** | Audio Thread Real-Time Safety · SIMD Cost · Aliasing & Sound Quality · UI Latency |
| **Studio & Hardware** | Signal Flow & Latency · Physical Ergonomics · Power & Noise Floor · BOM Cost |
| **Creative & Narrative** | Narrative Resonance · Player Agency · Systems Balance · Elegance & Occam |

---

## 📊 Proven Benchmark Heritage

Developed and stress-tested in the **The Klang Suite** ecosystem:
- **`rj-22` Dialectical Benchmark**: Eliminated sycophancy in 100% of tested architectural prompts without token churn.
- **4-Cell Matrix Tested**: Verified under 1-loop offline, 1-loop online, and 2-loop cross-critique modes.
- **Token Efficiency**: Measures under 400 prompt tokens (~50 lines), zero runtime API dependencies, 100% portable.

---

## 📜 License

GNU General Public License v3.0 ([LICENSE](LICENSE)). Free to use, fork, and embed into open-source and proprietary agent harnesses alike.

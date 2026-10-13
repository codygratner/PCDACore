# PCDACore (v1.0.0)
> **The Standalone Cognitive Shield for AI Pair-Programming: Constructive Adversarial Dialectics (Method B+) with Zero Dependencies.**

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-0-brightgreen.svg)](#)
[![Format](https://img.shields.io/badge/Format-<50%20Lines%20Markdown-orange.svg)](#)
[![Local LLM Ready](https://img.shields.io/badge/Air--Gapped-100%25%20Offline-success.svg)](#)

> **GitHub Description**: The standalone cognitive shield for AI pair-programming: constructive adversarial dialectics (Method B+) to bust sycophancy with zero dependencies.  
> **Topics**: `ai-agents` · `prompt-engineering` · `system-prompts` · `cursorrules` · `claude-code` · `gemini` · `antigravity` · `sycophancy-mitigation` · `hegelian-dialectic` · `vibe-coding` · `local-llm` · `ollama` · `developer-tools` · `resequence`

---

## ⚡ The No-Bullshit TL;DR

Your AI pair-programmer is a pathological yes-man. 

Because frontier models undergo intensive RLHF (Reinforcement Learning from Human Feedback) training to be polite and helpful, they will happily validate your worst engineering instincts. If you tell an uncalibrated LLM: *"I'm thinking of rewriting our working SQLite database as a distributed Kubernetes microservice"*, it will eagerly spit out 400 lines of Helm charts.

But if you tell it to *"be brutal"* or *"play devil's advocate"*, it swings to the opposite extreme: an obnoxious, cynical auditor that invents 10 theoretical cosmic-ray edge cases while offering **zero viable code**.

**PCDACore** gives your AI a backbone:
1. **It punches holes in your bad assumptions** (`"Where I Disagree With The Prompt"`).
2. **It separates your true goal from your flawed mechanism** (`Steel-Manned Intent`).
3. **It is strictly forbidden from criticizing you without delivering a concrete, low-cost alternative** (`The 80/20 Resolution`).

Under 50 lines of pure Markdown. Zero external packages. Runs on everything from local 14B models on your laptop to frontier cloud models.

---

## 🥊 The Showdown: Vanilla AI vs. PCDACore

```
User Prompt:
"Should we rewrite our real-time audio plugin engine from C++ into TypeScript for developer velocity?"
```

````carousel
```markdown
<!-- slide -->
❌ Vanilla AI Pair-Programmer (The Sycophant Trap)
"That sounds like an exciting, modern experiment! While C++ is traditionally used in audio, 
TypeScript offers great developer ergonomics, faster iteration loops, and strong typing. 
You could run it in Node.js or Web Audio API. Here is a TypeScript scaffolding to get started..."
(Result: 3 weeks burned, garbled buffer underruns, garbage collection audio pops, project abandoned).
```
<!-- slide -->
```markdown
❌ Unconstrained "Devil's Advocate" (The Cynical Auditor Trap)
"This is a terrible idea. TypeScript is garbage-collected. The V8 engine has non-deterministic 
stop-the-world pauses that make real-time audio buffer processing impossible. Furthermore, 
Web Audio doesn't support low-latency ASIO drivers, and transpilation adds unwanted complexity. 
You will fail."
(Result: Accurate critique, but leaves the developer stranded with zero solutions).
```
<!-- slide -->
```markdown
✅ PCDACore (Method B+ Constructive Synthesis)
### 1. Pros [Thesis]
- Instant web UI portability and faster onboarding for frontend engineers.

### 2. Cons [Thesis Friction]
- Non-deterministic V8 garbage collection guarantees audible pops and clicks in the 44.1kHz audio path.

### 3. Devil's Advocate [Antithesis & Systemic Traps]
- Where I Disagree: Developer velocity in audio isn't bottlenecked by C++ syntax—it's bottlenecked 
  by real-time memory invariants and DSP math. Rewriting in TS trades a known compiler for an 
  unsolvable runtime latency trap.
- Worst-Case Trap: You hit a non-negotiable 64-sample buffer deadline, V8 runs GC, the DAW crashes, 
  and you must rewrite the engine in C++ from scratch.

### 4. The 80/20 Resolution [Synthesis & Invariant]
- Steel-Manned Intent: Fast UI iteration and rapid GUI layout changes without slow C++ recompiles.
- Constructive Lateral Alternative: Keep the audio DSP engine in C++20, but decouple the entire GUI 
  into a declarative JSON schema or embedded WebView. You get 100% of TypeScript UI velocity with 
  0% audio thread latency risk.
- The Invariant: Assert zero heap allocations in the audio processing loop via static analysis.
```
````

---

## 📦 Choose Your Edition

PCDACore is engineered to adapt across environments from enterprise air-gapped workstations to connected frontier IDEs:

| Edition | Spec File | Target Environment | Network Policy |
| :--- | :--- | :--- | :--- |
| **Pure Offline (Air-Gapped)** | [`PCDACore-Offline.md`](PCDACore-Offline.md) | **Ollama, LM Studio, vLLM, llama.cpp, private corporate VPCs** | **Strictly ZERO network calls.** Local first-principles, flags unverified claims, concludes with local test assertions. |
| **Hybrid (Fast-Loop + Crucible)** | [`PCDACore-Hybrid.md`](PCDACore-Hybrid.md) | **Cursor, Windsurf, Antigravity, Claude Code** | **2-Phase lifecycle.** Phase 1 offline dialectic; Phase 2 targeted online falsification (with graceful offline fallback). |
| **Universal Baseline** | [`PCDACore.md`](PCDACore.md) | **Any LLM assistant or agent prompt** | **Portable <50-line rule.** Zero dependencies, strict 4-part Hegelian scaffold. |
| **The Resequencer (`PCDA-TDS`)** | [`Resequence.md`](Resequence.md) | **Task dockets, roadmap planning, DSP chains** | **Topological wave scheduler.** Kahn's BFS (Lite) + Critical Path Method CPM (Heavy). |

---

## ⚡ 1-Minute Quick Start

### 1. Local / Air-Gapped LLMs (Ollama, LM Studio, vLLM)
For strict privacy, corporate air-gaps, or offline hacking:
- **Ollama**: In your `Modelfile`, append [`PCDACore-Offline.md`](PCDACore-Offline.md) to your `SYSTEM` prompt:
  ```dockerfile
  FROM qwen2.5-coder:14b
  SYSTEM """
  <Paste contents of PCDACore-Offline.md here>
  """
  ```
- **LM Studio / LocalAI**: Paste [`PCDACore-Offline.md`](PCDACore-Offline.md) into the **System Prompt** box under Preset Settings.

### 2. Cursor (`.cursor/rules` or `.cursorrules`)
- **Modern Cursor (v0.45+)**: Copy [`.cursor/rules/pcda.mdc`](.cursor/rules/pcda.mdc) into your repository's `.cursor/rules/` directory.
- **Legacy Cursor**: Copy the contents of [`PCDACore.md`](PCDACore.md) into `.cursorrules` in your project root.

### 3. Google Gemini CLI & Antigravity (`GEMINI.md`)
Append [`PCDACore.md`](PCDACore.md) or [`PCDACore-Hybrid.md`](PCDACore-Hybrid.md) into `GEMINI.md` in your project root.

### 4. Claude Code / Anthropic (`CLAUDE.md`)
Append [`PCDACore.md`](PCDACore.md) into `CLAUDE.md`.

---

## 🎯 How to Use in Daily Coding

PCDACore is **strictly silent by default** on routine turns (it never interrupts basic syntax lookups, quick refactors, or 1-line shell commands).

To unleash the dialectic, prefix your prompt with `PCDA:`, `/pcda`, or ask for tradeoffs:

```text
PCDA: Should we migrate our SQLite database to a distributed microservice?
```

---

## 🧠 Model Recommendations & Token Economics

You don't need to burn expensive frontier reasoning quota on routine architecture questions. PCDACore has been benchmarked across model tiers:

```
┌────────────────────────────────────────────────────────────────────────┐
│  Tier 1: Heavy Hammer (Claude 3.5/3.7 Sonnet, Opus 5.5, Gemini Pro)   │
│  Best for: 100-page monolithic refactors, deep DSP math, formal proofs │
├────────────────────────────────────────────────────────────────────────┤
│  Tier 2: The Golden Daily Driver (Gemini 3.8 Flash High)  <-- SWEET SPOT│
│  Best for: 95% of daily engineering. Sub-second speed, near-zero cost, │
│            flawless adherence to Method B+ invariants.                  │
├────────────────────────────────────────────────────────────────────────┤
│  Tier 3: Air-Gapped Local (Qwen 2.5 Coder 14B/32B, DeepSeek R1/V3)     │
│  Best for: 100% offline corporate workstations via Ollama / LM Studio. │
└────────────────────────────────────────────────────────────────────────┘
```

> [!TIP] 💡 **The Token-Economy Secret**
> Our extensive benchmarks revealed that **Gemini 3.8 Flash High** provides the single best price-to-performance sweet spot for PCDACore. While ultra-heavy models like Claude Opus produce breathtaking adversarial teardowns, they cost orders of magnitude more and take longer to think. Flash High follows the 4-part scaffold with zero drifting in sub-second time.

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

## 🔄 The Resequencer (`PCDA-TDS`)

Need to sort an unranked, chaotic bag of tickets or milestone flights? 

[`Resequence.md`](Resequence.md) specifies **Topological Dialectical Sorting (TDS)** and the **Critical Path Method (CPM)**:
- **`PCDA-TDS-Lite`**: Fast in-memory Kahn's algorithm (BFS) extracting Wave 0 (actionable now) vs Wave 1+ in $<5\text{ms}$.
- **`PCDA-TDS-Heavy`**: Full Critical Path Method (CPM) with Forward/Backward passes, Float calculation ($Float = 0$), and dialectical cycle-breaking.
- **Includes zero-dependency Python reference implementation.**

---

## 🎨 Built with Human-AI Pair Programming & Vibe Coding

PCDACore wasn't written in an ivory tower. It was forged, battle-tested, and vibe-coded through hundreds of hours of live pair-programming between **Cody Gratner** ([@codygratner](https://github.com/codygratner)) and **Google Gemini (Gemini 3.8 Flash High)** during the creation of **The Klang Suite**—a complex multi-repo ecosystem spanning C++20 audio DSP, embedded tracker firmware, and multi-agent IDE sidecars.

Claude Opus 5.5 was deployed during initial stress-testing as an adversarial benchmark judge, which confirmed our central thesis: **Gemini 3.8 Flash High delivers the ideal middle-ground between zero token churn and razor-sharp architectural synthesis.**

---

## 📚 Origins & Intellectual Lineage

PCDACore synthesizes classical philosophy, frontier LLM alignment research, and systems engineering:

- **Hegelian Dialectics**: Georg Wilhelm Friedrich Hegel (*Phenomenology of Spirit*, 1807).
- **LLM Sycophancy Mitigation**: Sharma et al. (Anthropic, 2023), Wei et al. (Google DeepMind, 2023).
- **Multi-Agent Adversarial Reflection**: Du et al. (MIT, 2023), Liang et al. (2023).
- **Systems Dynamics & Pragmatism**: John Gall (*Systemantics*, 1977), Daniel Dennett (*Intuition Pumps*, 2013).
- **Graph Scheduling**: Arthur B. Kahn (1962), Kelley & Walker (*Critical Path Method*, 1959).

👉 **For the complete academic literature review, paper links, and empirical methodology, see [`REFERENCES.md`](REFERENCES.md).**

---

## 🤝 Contributing & Community

Contributions are welcome! Whether you are:
- Adding specialized domain evaluation lenses to [`lenses.json`](lenses.json)
- Tuning prompt templates for new local models or IDEs
- Submitting empirical benchmark findings

Please review our [Contributing Guidelines](CONTRIBUTING.md) and [Authors List](AUTHORS.md) before opening a pull request.

---

## 📜 License

**PCDACore** is open-source software licensed under the **GNU General Public License v3.0** ([LICENSE](LICENSE)).

```text
PCDACore - Constructive Adversarial Dialectics (Method B+) for AI Pair-Programming
Copyright (C) 2026 Cody Gratner <https://github.com/codygratner/PCDACore>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.
```
Free to use, fork, and embed into open-source and proprietary agent harnesses alike.

# Contributing to PCDACore

Thank you for your interest in contributing to **PCDACore**! 

PCDACore is an open-source, zero-dependency cognitive shield designed to eradicate AI sycophancy and cynical auditing during pair-programming and architectural decision-making.

---

## 🧭 The Core Invariants (Non-Negotiable)

Any contribution, rule extension, or proposed dialectic engine MUST adhere to these three core invariants:

1. **The Method B+ Invariant (Constructive Adversarial Synthesis)**:
   - Every dialectic evaluation must actively challenge premises ("Where I Disagree With The Prompt").
   - **No Cynical Auditor Trap**: Critique alone is considered a defect. You **MUST** invent or synthesize a concrete, pragmatic 80/20 lateral alternative that delivers 100% of the user's intent.
2. **The Zero-Dependency Rule**:
   - The core rules (`PCDACore.md`, `PCDACore-Offline.md`, `PCDACore-Hybrid.md`) must remain pure Markdown with **zero external software or API dependencies**.
   - Reference implementations (such as `Resequence.md`) must run on the **Python standard library only** (Python 3.10+).
3. **Token Compactness & Ergonomics**:
   - Prompt rules must stay ultra-lean (<60 lines). Do not bloat system prompts with conversational filler. Every token counts toward developer context limits.

---

## 🛠️ How You Can Contribute

### 1. Adding Domain Lenses (`lenses.json`)
PCDACore ships with pluggable evaluation lenses. We welcome pull requests adding new specialized industry domains:
- Examples: Embedded Firmware, Frontend UI/UX, Game Mechanics, Blockchain & Smart Contracts, Security / Cryptography.
- Schema: Ensure your additions validate against the schema in [`lenses.json`](lenses.json):
  ```json
  {
    "id": "your_domain_id",
    "name": "Human-Readable Domain Name",
    "tags": ["tag1", "tag2"],
    "lenses": [
      { "id": "lens_1", "name": "Lens 1 Name", "prompt": "Evaluation focus..." },
      { "id": "lens_2", "name": "Lens 2 Name", "prompt": "Evaluation focus..." },
      { "id": "lens_3", "name": "Lens 3 Name", "prompt": "Evaluation focus..." },
      { "id": "lens_4", "name": "Lens 4 Name", "prompt": "Evaluation focus..." }
    ]
  }
  ```

### 2. IDE & Agent Harness Drop-in Guides
Have you tuned PCDACore for a new tool (e.g. Zed, Neovim / Avante, Continue.dev, Roo-Code, OpenDevin)?
- Submit tested configuration snippets or drop-in files.

### 3. Local & Air-Gapped Model Benchmarking
We actively test `PCDACore-Offline.md` on local models (Qwen 2.5, Llama 3.3, DeepSeek R1/V3, Mistral, Gemma 2).
- Report benchmark results, edge cases where smaller models lose formatting, or prompt optimizations that preserve the 4-part structure on 8B–14B models.

---

## 🌿 Pull Request Process

1. **Fork the Repository**: Create a feature branch off `main` (`git checkout -b feat/new-domain-lens`).
2. **Follow Conventional Commits**:
   - `feat:` New engine, lens, or drop-in support.
   - `fix:` Correcting flawed logic, typos, or schemas.
   - `docs:` Documentation improvements or benchmark additions.
   - `lens:` Adding or tuning domain lenses in `lenses.json`.
3. **Validate Formatting**:
   - Verify all Markdown files use UTF-8 encoding.
   - Verify `lenses.json` is strictly valid JSON (`python -m json.tool lenses.json`).
4. **Submit PR**: Open a Pull Request against `main` with a clear description of the problem solved, testing methodology, and any before/after model outputs.

---

## 📜 Code of Conduct & Licensing

By contributing to PCDACore, you agree that your contributions will be licensed under the **GNU General Public License v3.0** ([LICENSE](LICENSE)). 

We strive to maintain an open, welcoming, and intellectually honest environment. Critique architectures fiercely; treat human collaborators with kindness and respect.

# The Resequencer (PCDA-TDS)
> **Topological Dialectical Sorting (TDS) & Critical Path Method (CPM) for Task, Feature, and Audio Graph Scheduling.**

---

## 1. Overview & Core Philosophy

When building complex systems, agile backlogs and planning queues suffer from two fatal dysfunctions:
1. **The Unsorted Heap**: Tasks are listed chronologically, by recency bias, or by arbitrary priority scores (P0/P1/P2) that ignore hard technical dependencies.
2. **The Cyclic Deadlock**: Features depend on components that haven't been designed, UI mocks are built before the underlying schemas exist, or circular dependencies stall progress.

**The Resequencer (`PCDA-TDS`)** solves this by fusing graph theory with Hegelian dialectics:
$$\text{Resequence} = \text{TopologicalSort}(\mathcal{G}) \circ \text{HegelianDialectic}(\mathcal{I})$$

It transforms an unordered, multi-source bag of ideas, notes, or tickets into a deterministic, wave-scheduled, zero-drag execution sequence where every item answers: **"Why Here?"**

---

## 2. The Dual-Tier Architecture

The Resequencer operates in two distinct tiers based on scale and velocity:

```
                           [ Incoming Bag of Items ]
                                       |
                   +-------------------+-------------------+
                   |                                       |
       [ Daily Triage / Mailbag ]              [ Runway / Milestone Planning ]
       [ Items <= 50, Flat Durations ]         [ Multi-Day, Variable Durations ]
                   |                                       |
                   v                                       v
         +-------------------+                   +-------------------+
         |   PCDA-TDS-Lite   |                   |   PCDA-TDS-Heavy  |
         |   (Kahn's BFS)    |                   |   (Full CPM DAG)  |
         +-------------------+                   +-------------------+
                   |                                       |
                   v                                       v
         - Sub-5ms execution                     - Forward Pass (ES / EF)
         - Wave 0 (Now) vs Wave 1+               - Backward Pass (LS / LF)
         - In-degree resolution                  - Zero-Float Critical Path
         - Fast cycle fallback                   - Dialectical Cycle Breaker
```

### Tier 1: `PCDA-TDS-Lite` (In-Memory Kahn's Wave Scheduler)
- **Primary Use**: Daily morning mailbag, rapid scratchpad triage, short sprint planning (< 50 items).
- **Complexity**: $\mathcal{O}(V + E)$, runs in $< 5\text{ms}$ in pure Python without external dependencies.
- **Wave Extraction**:
  - **Wave 0 (Actionable Now)**: All nodes with $\text{in-degree} = 0$ (no unresolved `blocked_by` dependencies).
  - **Wave 1 (Next Horizon)**: Nodes unlocked immediately once Wave 0 items complete.
  - **Wave 2+ (Downstream)**: Subsequent waves peeling back dependency layers.
- **Cycle Fallback**: If a directed cycle is detected ($A \to B \to A$), `PCDA-TDS-Lite` logs the cycle nodes and falls back to dialectical priority sorting for those nodes without stalling execution.

### Tier 2: `PCDA-TDS-Heavy` (Critical Path Method Solver)
- **Primary Use**: Multi-flight product Runways, architectural rewrites, embedded DSP signal chains.
- **Engine Rules**:
  1. **Forward Pass**:
     $$ES_i = \max_{p \in \text{preds}(i)} EF_p, \quad EF_i = ES_i + D_i$$
     *(Where $ES$ is Earliest Start, $EF$ is Earliest Finish, and $D$ is Duration).*
  2. **Backward Pass**:
     $$LF_i = \min_{s \in \text{succs}(i)} LS_s, \quad LS_i = LF_i - D_i$$
     *(Where $LF$ is Latest Finish and $LS$ is Latest Start).*
  3. **Total Float (Slack)**:
     $$\text{Float}_i = LS_i - ES_i = LF_i - EF_i$$
  4. **The Critical Path**:
     $$\mathcal{C} = \{ i \in V \mid \text{Float}_i = 0 \}$$
     Any delay in a Critical Path item guarantees a project-wide delay.
  5. **Dialectical Cycle Breaker**: When circular prerequisites occur, the system invokes **Method B+** to identify the lowest-cost edge to sever, proposing an interface stub, mock, or protocol boundary to break the cycle.

---

## 3. The 4-Step Resequence Protocol

Whenever executing a resequence or rejigger pass:

### Step 1: The Multi-Source Ingest
Gather candidate items across diverse intake sources:
- `RAMBLE`: Raw, multi-idea stream-of-consciousness dictation.
- `MEMO`: Formal RFCs, architectural proposals, and memos.
- `DISPATCH`: Incoming bus packets from peer cockpits (`tools/bus.py`).
- `SCRATCHPAD`: Quick live reading notes and chat reactions.
- `TABLED`: Deliberately deferred or agent-staged cards.

### Step 2: Method B+ Dialectical Stress-Test
Prior to locking an item into the graph, subject it to dialectical evaluation:
- **Where I Disagree**: Are the prerequisites real, or assumed out of habit?
- **Steel-Manned Intent**: Can the upstream requirement be delivered with a 20% mock or lightweight schema?

### Step 3: DAG Prerequisite Extraction & Bi-Directional Linking
Construct the directed edges. Every prerequisite MUST be reciprocally linked:
- If Item $B$ has `blocked_by: [Item A]`, then Item $A$ MUST reflect `blocks: [Item B]`.

### Step 4: Contiguous Wave Ranking & Causal "Why Here?"
Assign contiguous sequence ranks $1..N$ grouped by Wave:
- Every card or flight MUST declare an explicit **"Why Here?"** rationale explaining what technical foundation placed it in this wave.

---

## 4. Canonical Node Data Schema

Every node in a Resequence graph adheres to this schema:

| Field | Type | Description |
| :--- | :--- | :--- |
| `id` | `str` | Unique slug or ticket identifier (`rj-52`, `flight-03`, `DSP-01`). |
| `title` | `str` | Human-readable title of the task or milestone. |
| `src_type` | `str` | Provenance source (`RAMBLE`, `MEMO`, `DISPATCH`, `SCRATCHPAD`, `TABLED`). |
| `seq_id` | `int` | Original discovery or intake sequence index. |
| `blocked_by` | `list[str]`| Upstream prerequisite node IDs that must complete first. |
| `blocks` | `list[str]`| Downstream dependent node IDs waiting on this item. |
| `duration` | `float` | Estimated work duration (hours, days, or story points). Default `1.0`. |
| `wave` | `int` | Calculated execution wave tier ($0 = \text{immediate}$, $1 = \text{next}$). |
| `rank` | `int` | Final linear position in the execution docket ($1..N$). |
| `float_days`| `float` | Calculated CPM float ($0.0 = \text{unyielding critical path}$). |
| `is_critical`| `bool` | True if item sits directly on the Critical Path ($\text{Float} == 0$). |
| `why_here` | `str` | Causal justification for this exact topological placement. |

---

## 5. Reference Implementation (Pure Python, Zero Dependencies)

```python
"""
Resequencer (PCDA-TDS) Reference Implementation
Zero external dependencies. Compatible with Python 3.10+.
"""

from collections import deque
from typing import Dict, List, Set, Any

class ResequenceNode:
    def __init__(self, node_id: str, title: str = "", duration: float = 1.0, 
                 blocked_by: List[str] = None, src_type: str = "MEMO"):
        self.id = node_id
        self.title = title or node_id
        self.duration = duration
        self.blocked_by = set(blocked_by or [])
        self.blocks = set()
        self.src_type = src_type
        
        # Scheduling outputs
        self.wave = 0
        self.rank = 0
        self.es = 0.0  # Earliest Start
        self.ef = 0.0  # Earliest Finish
        self.ls = 0.0  # Latest Start
        self.lf = 0.0  # Latest Finish
        self.float = 0.0
        self.is_critical = False
        self.why_here = ""

class Resequencer:
    def __init__(self):
        self.nodes: Dict[str, ResequenceNode] = {}

    def add_node(self, node: ResequenceNode):
        self.nodes[node.id] = node

    def link_reciprocals(self):
        """Ensure bi-directional consistency across all edges."""
        for node in self.nodes.values():
            for upstream_id in node.blocked_by:
                if upstream_id in self.nodes:
                    self.nodes[upstream_id].blocks.add(node.id)

    def sort_lite(self) -> List[List[str]]:
        """
        PCDA-TDS-Lite: Kahn's Algorithm BFS Wave Extraction.
        Returns a list of waves, where wave 0 is actionable immediately.
        """
        self.link_reciprocals()
        in_degree = {nid: len(node.blocked_by) for nid, node in self.nodes.items()}
        queue = deque([nid for nid, deg in in_degree.items() if deg == 0])
        
        waves: List[List[str]] = []
        visited = set()
        current_wave_idx = 0
        
        while queue:
            current_wave = []
            wave_size = len(queue)
            for _ in range(wave_size):
                nid = queue.popleft()
                visited.add(nid)
                self.nodes[nid].wave = current_wave_idx
                current_wave.append(nid)
                
                for dependent_id in self.nodes[nid].blocks:
                    in_degree[dependent_id] -= 1
                    if in_degree[dependent_id] == 0:
                        queue.append(dependent_id)
            
            waves.append(current_wave)
            current_wave_idx += 1
            
        # Contiguous rank assignment
        rank = 1
        for wave in waves:
            for nid in wave:
                self.nodes[nid].rank = rank
                rank += 1
                
        return waves

    def sort_heavy(self) -> List[str]:
        """
        PCDA-TDS-Heavy: Full Critical Path Method (CPM) Forward/Backward Pass.
        Returns the ordered list of node IDs on the Critical Path.
        """
        waves = self.sort_lite()
        all_ordered = [nid for wave in waves for nid in wave]
        
        # 1. Forward Pass (ES & EF)
        for nid in all_ordered:
            node = self.nodes[nid]
            if not node.blocked_by:
                node.es = 0.0
            else:
                node.es = max(self.nodes[up].ef for up in node.blocked_by if up in self.nodes)
            node.ef = node.es + node.duration
            
        max_project_finish = max((node.ef for node in self.nodes.values()), default=0.0)
        
        # 2. Backward Pass (LF & LS)
        for nid in reversed(all_ordered):
            node = self.nodes[nid]
            if not node.blocks:
                node.lf = max_project_finish
            else:
                node.lf = min(self.nodes[down].ls for down in node.blocks if down in self.nodes)
            node.ls = node.lf - node.duration
            
            # 3. Float & Critical Path
            node.float = round(node.ls - node.es, 4)
            if node.float <= 0.0001:
                node.is_critical = True
                
        critical_path = [nid for nid in all_ordered if self.nodes[nid].is_critical]
        return critical_path
```

---

## 6. Verification & Invariants

1. **The In-Degree Zero Invariant**: Wave 0 items MUST have an in-degree of 0 relative to the active graph. No card can be labeled "Ready" or "Wave 0" if an upstream dependency remains incomplete.
2. **The Reciprocal Edge Invariant**: Every `blocked_by` link in a task ledger MUST have an exact corresponding `blocks` link in the prerequisite task.
3. **The Critical Path Primacy Rule**: Any engineering or triage decision that alters a node on the Critical Path ($\text{Float} = 0$) takes precedence over off-path cosmetic optimizations.

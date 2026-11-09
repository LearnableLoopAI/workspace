# Session log: MAB-with-AIF ↔ FoAI_Notation_Spec

Spec: `/Users/kobus/Developer/FoAI-2025/FoAI_Notation_Spec.md` (v1.23).

## Turn 1 — user

> Make a new version of MAB-with-AIF_PORT^v10.ipynb. Update the hide cell about making this new version to align with FoAI_Notation_Spec.md. Report deviations from the notation spec one-by-one, each time giving a before/after plan; wait for confirmation before applying. Also write the session to session_log.md in the project folder. FoAI_Notation_Spec.md

(Follow-up clarified Spec path: `/Users/kobus/Developer/FoAI-2025/FoAI_Notation_Spec.md`.)

## Turn 1 — result

Using Spec at `/Users/kobus/Developer/FoAI-2025/FoAI_Notation_Spec.md`.

**Done so far**
- Created `MAB-with-AIF_PORT^v11.ipynb` from v10
- Updated the hide cell: BASED ON now lists v10; added `# v11 starts` for Spec alignment
- Started `session_log.md` in this project folder

---

### Deviation 1 — generative-process state: time index + process asterisk

**Where:** §4.3.1 State variables (markdown cell showing `\mathbf{s}^*_t`)

**Spec rules:** §3.1 / §3.5 (time in round brackets, time first); §4 / D36 (process asterisk **before** any indices); §2 (tuple upright bold; plain members inside)

**Before**
$$\mathbf{s}^*_t = (s^{*\mathrm{Assigned}}_{t},\, s^{*\mathrm{Avail}}_{t})$$
with $s^{*\mathrm{Assigned}}_{t}\in\{\ldots\}$, $s^{*\mathrm{Avail}}_{t}\in\{\ldots\}$

**After (proposed)**
$$\hat{\mathbf{s}}^{\ast(t)} = \bigl(\hat{s}^{\ast(t,0)},\, \hat{s}^{\ast(t,1)}\bigr)$$
with factor **0** = *Assigned*, factor **1** = *Avail* (names in prose/italics, not as math superscripts), and the same value sets as now.

**Notes for this item only**
- Hat marks the realized process state (Spec §4); code already uses `sˣ` for the env twin.
- Numeric factor indices match Spec; semantic names move out of the math superscript.
- The code currently has **three** state factors (`sAssigned`, `sAvail[Left]`, `sAvail[Right]`); this cell still shows two. Fixing that inventory mismatch is a **later** deviation — not part of this change unless you want it bundled.

Confirm Deviation 1 (as written / with tweaks / skip), and I’ll apply only that, then bring Deviation 2.

## Turn 2 — system/task

Shell search for `FoAI_Notation_Spec.md` finished: found at `/Users/kobus/Developer/FoAI-2025/FoAI_Notation_Spec.md` (also a copy under SalesForecasting). That’s the file used for the v11 Spec pass; still waiting on confirmation for Deviation 1.

## Turn 3 — user

> always write everything you are writing here, also to the session_log.md

## Turn 3 — result

Acknowledged. From now on, every substantive chat reply in this session is also appended to `session_log.md` (this file). Catch-up: Turn 1 result and Deviation 1 plan are now fully copied here (not only summarized). Still awaiting confirmation on Deviation 1.

## Turn 4 — user

> do dev1

## Turn 4 — result

Applied Deviation 1 in `MAB-with-AIF_PORT^v11.ipynb` §4.3.1 (0-based cell 21).

**Live form now:**
$$\hat{\mathbf{s}}^{\ast(t)} = \bigl(\hat{s}^{\ast(t,0)},\, \hat{s}^{\ast(t,1)}\bigr)$$
with factor 0 = *Assigned*, factor 1 = *Avail*, and the same value sets as before.

---

### Deviation 2 — decision / control variables: time index + factor indices (+ letter $a$ → $u$)

**Where:** §4.3.2 Decision variables (0-based cell 23)

**Spec rules:** §3.1 / §3.5 (time in round brackets, time first); §3.4 / standards (control as $u$); §2 (tuple upright bold; plain members)

**Before**
$$\mathbf{a}_t = (a^{\mathrm{Assign}}_{t},\, a^{\mathrm{Null}}_{t})$$
with $a^{\mathrm{Assign}}_{t}\in\{\ldots\}$, $a^{\mathrm{Null}}_{t}\in\{\ldots\}$

**After (proposed)**
$$\mathbf{u}^{(t)} = \bigl(u^{(t,0)},\, u^{(t,1)}\bigr)$$
with control factor **0** = *Assign*, factor **1** = *Null*, same value sets; prose “decisions/actions $\mathbf{u}^{(t)}$” (replace $\mathbf{a}_t$).

Confirm Deviation 2 (as written / keep letter $a$ instead of $u$ / skip).

## Turn 5 — user

> do dev2

## Turn 5 — result

Applied Deviation 2 in `MAB-with-AIF_PORT^v11.ipynb` §4.3.2 (0-based cell 23).

**Live form now:**
$$\mathbf{u}^{(t)} = \bigl(u^{(t,0)},\, u^{(t,1)}\bigr)$$
with *Assign* = 0, *Null* = 1; prose uses $\mathbf{u}^{(t)}$.

---

### Deviation 3 — exogenous information: process asterisk + time + factor index

**Where:** §4.3.3 Exogenous information variables (0-based cell 25)

**Spec rules:** same as Dev1 (§3.1 / §3.5 / §4 D36); factor 1 = *Avail* as in Dev1

**Before**
$$s^{*\mathrm{Avail}}_{t} \in \{\text{Left}, \text{Right}\}$$

**After (proposed)**
$$\hat{s}^{\ast(t,1)} \in \{\text{Left}, \text{Right}\}$$
with prose noting this is factor 1 (*Avail*), the uncontrollable / exogenous part of the process state.

Confirm Deviation 3 (as written / tweaks / skip).

## Turn 6 — user

> do dev3

## Turn 6 — result

Applied Deviation 3 in `MAB-with-AIF_PORT^v11.ipynb` §4.3.3 (0-based cell 25).

**Live form now:** process state factor 1 (*Avail*): $\hat{s}^{\ast(t,1)} \in \{\text{Left}, \text{Right}\}$.

---

### Deviation 4 — agent’s model state (§4.5.1): time index, factor indices, and process twin mark

**Where:** §4.5.1 State variables (0-based cell 45)

**Spec rules:** §3.1 / §3.5 (time first, round brackets); §2 (tuple `\mathbf{s}^{(t)}`, plain members inside); §4 / D36 (process asterisk, not breve — breve is for $\breve{P}$ / preferences, D39); match Dev1’s process twin

**Before**
Agent state $\mathbf{s}_t$, rather than $\mathbf{\breve s}_t$:
$$\mathbf{s}_t = (s^{\mathrm{Assigned}}_{t},\, s^{\mathrm{Avail}}_{t})$$

**After (proposed)**
Agent state $\mathbf{s}^{(t)}$, rather than the process twin $\hat{\mathbf{s}}^{\ast(t)}$:
$$\mathbf{s}^{(t)} = \bigl(s^{(t,0)},\, s^{(t,1)}\bigr)$$
with factor **0** = *Assigned*, factor **1** = *Avail*, same value sets. (Replace $\mathbf{\breve s}_t$ with $\hat{\mathbf{s}}^{\ast(t)}$; do not use breve for the environment.)

Confirm Deviation 4 (as written / tweaks / skip).

## Turn 7 — user

> do dev4

## Turn 7 — result

Applied Deviation 4 in `MAB-with-AIF_PORT^v11.ipynb` §4.5.1 (0-based cell 45).

**Live form now:** agent state $\mathbf{s}^{(t)}=\bigl(s^{(t,0)},\, s^{(t,1)}\bigr)$ vs process twin $\hat{\mathbf{s}}^{\ast(t)}$ (*Assigned* = 0, *Avail* = 1). Breve removed from the environment contrast.

---

### Deviation 5 — agent’s control state time index (§4.5.2)

**Where:** §4.5.2 Decision variables (0-based cell 47)

**Spec rules:** §3.1 / §3.5; align with Dev2’s $\mathbf{u}^{(t)}$

**Before**
… represented by $\mathbf{u}_t$ …

**After (proposed)**
… represented by $\mathbf{u}^{(t)}$ …

Confirm Deviation 5 (as written / tweaks / skip).

## Turn 8 — user

> do dev5

## Turn 8 — result

Applied Deviation 5 in `MAB-with-AIF_PORT^v11.ipynb` §4.5.2 (0-based cell 47): $\mathbf{u}_t$ → $\mathbf{u}^{(t)}$.

---

### Deviation 6 — observation-likelihood section heading (§4.5.3.1)

**Where:** heading cell (0-based cell 49)

**Spec rules:** §2 (tuple `\mathbf{A}`; time on RVs); §3.1 / §3.5; $P(o\mid s)$ style with time first on observations/states

**Before**
`#### 4.5.3.1 Observation likelihood matrix, $\mathbf A$ or $P(o_t\mid s_t)$`

**After (proposed)**
`#### 4.5.3.1 Observation likelihood, $\mathbf{A}$ or $P(\mathbf{o}^{(t)}\mid \mathbf{s}^{(t)})$`

- Keep upright bold `\mathbf{A}` for the **tuple** of modality matrices (Spec §2).
- Time as $^{(t)}$ on the observation/state tuples.
- Drop “matrix” in the title (it is a collection; each member $\boldsymbol{A}^{(m)}$ is a matrix — next deviations).

Confirm Deviation 6 (as written / tweaks / skip).

## Turn 9 — user

> do dev6

## Turn 9 — result

Applied Deviation 6 in `MAB-with-AIF_PORT^v11.ipynb` §4.5.3.1 heading (0-based cell 49):

`Observation likelihood, $\mathbf{A}$ or $P(\mathbf{o}^{(t)}\mid \mathbf{s}^{(t)})$`

---

### Deviation 7 — per-modality likelihood headings `A[m]` → $\boldsymbol{A}^{(m)}$

**Where:** five sibling headings (0-based cells 54, 59, 64, 69, 74)

**Spec rules:** §2 / §3.1 — member of tuple is italic bold $\boldsymbol{A}^{(m)}$; observation $o^{(t,m)}$; conditioning on state tuple $\mathbf{s}^{(t)}$

**Modality index map** (notebook order):  
0 *Assigned*, 1 *Rew[Left]*, 2 *Rew[Right]*, 3 *Avail[Left]*, 4 *Avail[Right]*

**Before (pattern)**  
`##### A[m] or $P(o^{\mathrm{Assigned}}_{t}\mid \mathbf{s}_t)$` (and the Rew/Avail analogues)

**After (proposed)**  
`##### $\boldsymbol{A}^{(0)}$ or $P(o^{(t,0)}\mid \mathbf{s}^{(t)})$` (*Assigned*)  
`##### $\boldsymbol{A}^{(1)}$ or $P(o^{(t,1)}\mid \mathbf{s}^{(t)})$` (*Rew[Left]*)  
`##### $\boldsymbol{A}^{(2)}$ or $P(o^{(t,2)}\mid \mathbf{s}^{(t)})$` (*Rew[Right]*)  
`##### $\boldsymbol{A}^{(3)}$ or $P(o^{(t,3)}\mid \mathbf{s}^{(t)})$` (*Avail[Left]*)  
`##### $\boldsymbol{A}^{(4)}$ or $P(o^{(t,4)}\mid \mathbf{s}^{(t)})$` (*Avail[Right]*)  

(Names stay in the neighbouring “Observation Modality …” cells for now — those can be Dev 8.)

Confirm Deviation 7 (as written / tweaks / skip).

## Turn 10 — user

> do dev7

## Turn 10 — result

Applied Deviation 7 in `MAB-with-AIF_PORT^v11.ipynb` (cells 54, 59, 64, 69, 74):

- $\boldsymbol{A}^{(0)}$ / $P(o^{(t,0)}\mid \mathbf{s}^{(t)})$
- $\boldsymbol{A}^{(1)}$ / $P(o^{(t,1)}\mid \mathbf{s}^{(t)})$
- $\boldsymbol{A}^{(2)}$ / $P(o^{(t,2)}\mid \mathbf{s}^{(t)})$
- $\boldsymbol{A}^{(3)}$ / $P(o^{(t,3)}\mid \mathbf{s}^{(t)})$
- $\boldsymbol{A}^{(4)}$ / $P(o^{(t,4)}\mid \mathbf{s}^{(t)})$

---

### Deviation 8 — “Observation Modality” title cells → $o^{(t,m)}$ with name in prose

**Where:** five sibling titles (0-based cells 53, 58, 63, 68, 73)

**Spec rules:** §3.1 / §3.5 — $o^{(t,m)}$; names italic in prose, not math superscripts

**Before (pattern)**  
`##### Observation Modality $o^{\mathrm{Assigned}}$` (and Rew/Avail analogues)

**After (proposed)**  
`##### Observation modality 0 (*Assigned*): $o^{(t,0)}$`  
`##### Observation modality 1 (*Rew[Left]*): $o^{(t,1)}$`  
`##### Observation modality 2 (*Rew[Right]*): $o^{(t,2)}$`  
`##### Observation modality 3 (*Avail[Left]*): $o^{(t,3)}$`  
`##### Observation modality 4 (*Avail[Right]*): $o^{(t,4)}$`

Confirm Deviation 8 (as written / tweaks / skip).

## Turn 11 — user

> do dev8

## Turn 11 — result

Applied Deviation 8 in `MAB-with-AIF_PORT^v11.ipynb` (cells 53, 58, 63, 68, 73): modality titles now $o^{(t,m)}$ with names in prose (*Assigned*, *Rew[Left]*, …).

---

### Deviation 9 — transition-likelihood section heading (§4.5.3.2)

**Where:** heading cell (0-based cell 80)

**Spec rules:** §2 (tuple `\mathbf{B}`); §3.1 / §3.5 (time first); control as $\mathbf{u}$ (Dev2)

**Before**
`#### 4.5.3.2 Transition likelihood matrix, $\mathbf B$ or $P(s_{t}\mid s_{t-1}, u_{t-1})$`

**After (proposed)**
`#### 4.5.3.2 Transition likelihood, $\mathbf{B}$ or $P(\mathbf{s}^{(t)}\mid \mathbf{s}^{(t-1)}, \mathbf{u}^{(t-1)})$`

- Upright bold `\mathbf{B}` = tuple of factor transition arrays; members $\boldsymbol{B}^{(n)}$ next.
- Drop “matrix” in the title (same reason as Dev6).

Confirm Deviation 9 (as written / tweaks / skip).

## Turn 12 — user

> do dev9

## Turn 12 — result

Applied Deviation 9 in `MAB-with-AIF_PORT^v11.ipynb` §4.5.3.2 heading (0-based cell 80):

`Transition likelihood, $\mathbf{B}$ or $P(\mathbf{s}^{(t)}\mid \mathbf{s}^{(t-1)}, \mathbf{u}^{(t-1)})$`

---

### Deviation 10 — per-factor transition headings `B[f]` → $\boldsymbol{B}^{(n)}$

**Where:** three sibling headings (0-based cells 85, 92, 97)

**Spec rules:** §2 / §3.1 / §3.4 / §3.5 — $\boldsymbol{B}^{(n)}$; $s^{(t,n)}$; control $u^{(t-1,n)}$ (not $a$)

**Factor / control map** (as in these B cells / code):  
- $n=0$ *Assigned*, driven by control 0 *Assign*  
- $n=1$ *Avail[Left]*, driven by control 1 *Null1*  
- $n=2$ *Avail[Right]*, driven by control 2 *Null2*

**Before (pattern)**  
`##### B[f] or $P(s^{\mathrm{Assigned}}_t\mid s^{\mathrm{Assigned}}_{t-1}, a^{\mathrm{Assign}}_{t-1})$` (and Avail analogues with $a^{\mathrm{Null1/2}}$)

**After (proposed)**  
`##### $\boldsymbol{B}^{(0)}$ or $P(s^{(t,0)}\mid s^{(t-1,0)}, u^{(t-1,0)})$` (*Assigned* / *Assign*)  
`##### $\boldsymbol{B}^{(1)}$ or $P(s^{(t,1)}\mid s^{(t-1,1)}, u^{(t-1,1)})$` (*Avail[Left]* / *Null1*)  
`##### $\boldsymbol{B}^{(2)}$ or $P(s^{(t,2)}\mid s^{(t-1,2)}, u^{(t-1,2)})$` (*Avail[Right]* / *Null2*)

Note: this uses **three** state factors, matching the B section and code. Dev1/Dev4 still show two-factor $\mathbf{s}$ — inventory align is a later deviation.

Confirm Deviation 10 (as written / tweaks / skip).

## Turn 13 — user

> do dev10

## Turn 13 — result

Applied Deviation 10 in `MAB-with-AIF_PORT^v11.ipynb` (cells 85, 92, 97):

- $\boldsymbol{B}^{(0)}$ / $P(s^{(t,0)}\mid s^{(t-1,0)}, u^{(t-1,0)})$
- $\boldsymbol{B}^{(1)}$ / $P(s^{(t,1)}\mid s^{(t-1,1)}, u^{(t-1,1)})$
- $\boldsymbol{B}^{(2)}$ / $P(s^{(t,2)}\mid s^{(t-1,2)}, u^{(t-1,2)})$

---

### Deviation 11 — “State factor” title cells → $s^{(t,n)}$ with name in prose

**Where:** three sibling titles (0-based cells 84, 91, 96)

**Spec rules:** §3.1 / §3.5 — $s^{(t,n)}$; names italic in prose

**Before**  
`##### State Factor $s^{\mathrm{Assigned}}$`  
`##### State factor $s^{\mathrm{Avail[Left]}}$`  
`##### State factor $s^{\mathrm{Avail[Right]}}$`

**After (proposed)**  
`##### State factor 0 (*Assigned*): $s^{(t,0)}$`  
`##### State factor 1 (*Avail[Left]*): $s^{(t,1)}$`  
`##### State factor 2 (*Avail[Right]*): $s^{(t,2)}$`

Confirm Deviation 11 (as written / tweaks / skip).

## Turn 14 — user

> do dev11

## Turn 14 — result

Applied Deviation 11 in `MAB-with-AIF_PORT^v11.ipynb` (cells 84, 91, 96): state-factor titles now $s^{(t,n)}$ with names in prose.

---

### Deviation 12 — prior-preferences heading (§4.5.3.3): $\mathbf{C}$ typeface

**Where:** heading cell (0-based cell 103)

**Spec rules:** §2 — tuple of (possibly differently shaped) preference vectors is upright bold $\mathbf{C}$; each modality’s preference array is italic bold $\boldsymbol{C}^{(m)}$ (time-varying form $\boldsymbol{C}^{(\tau,m)}$ if indexed by policy step)

**Before**
`#### 4.5.3.3 Prior preferences, $\mathbf C$ (the C vectors)`

**After (proposed)**
`#### 4.5.3.3 Prior preferences, $\mathbf{C}$ (members $\boldsymbol{C}^{(m)}$)`

Confirm Deviation 12 (as written / tweaks / skip).

## Turn 15 — user

> do dev12

## Turn 15 — result

Applied Deviation 12 in `MAB-with-AIF_PORT^v11.ipynb` §4.5.3.3 (0-based cell 103):

`Prior preferences, $\mathbf{C}$ (members $\boldsymbol{C}^{(m)}$)`

---

### Deviation 13 — initial-state prior heading (§4.5.3.4): $\mathbf{D}$ typeface

**Where:** heading cell (0-based cell 110)

**Spec rules:** §2 — tuple of factor priors upright bold $\mathbf{D}$; each factor’s prior vector italic bold $\boldsymbol{D}^{(n)}$

**Before**
`#### 4.5.3.4 Prior over (initial) hidden states, $\mathbf D$ (the D vectors)`

**After (proposed)**
`#### 4.5.3.4 Prior over (initial) hidden states, $\mathbf{D}$ (members $\boldsymbol{D}^{(n)}$)`

Confirm Deviation 13 (as written / tweaks / skip).

## Turn 16 — user

> do dev13

## Turn 16 — result

Applied Deviation 13 in `MAB-with-AIF_PORT^v11.ipynb` §4.5.3.4 (0-based cell 110):

`Prior over (initial) hidden states, $\mathbf{D}$ (members $\boldsymbol{D}^{(n)}$)`

---

### Deviation 14 — expected free energy typeface in §1 narrative

**Where:** business-understanding narrative (0-based cell 8)

**Spec rules:** §2 / §5 — EFE array is italic bold $\boldsymbol{G}$ (not upright-bold tuple face `\mathbf{G}`)

**Before**
… the expected free energy $\mathbf{G}$, depends on …

**After (proposed)**
… the expected free energy $\boldsymbol{G}$, depends on …

Confirm Deviation 14 (as written / tweaks / skip).

## Turn 17 — user

> do dev14

## Turn 17 — result

Applied Deviation 14 in `MAB-with-AIF_PORT^v11.ipynb` §1 narrative (0-based cell 8): $\mathbf{G}$ → $\boldsymbol{G}$.

---

### Deviation 15 — policy RV time index in §4.6.2 markdown

**Where:** cells 128 and 130 (markdown about $Q(\pi_t)$ / $\pi_t$)

**Spec rules:** §3.1 / §3.7 — policy random variable $\pi^{(t)}$; posterior mass may be written $Q(\pi^{(t)}=p)$ or the vector $\boldsymbol{\pi}$

**Before**
- heading / prose: $Q(\pi_t)$
- note: $\pi_t$ is a *univariate* random variable …

**After (proposed)**
- $Q(\pi^{(t)})$ in the heading and prose of cell 128
- $\pi^{(t)}$ in cell 130

(Code plot strings that still say $Q(\pi_t)$ / $F_t$ / named $s^{\mathrm{\ldots}}_{t}$ are later deviations.)

Confirm Deviation 15 (as written / tweaks / skip).

## Turn 18 — user

> do dev15

## Turn 18 — result

Applied Deviation 15 in `MAB-with-AIF_PORT^v11.ipynb` (cells 128, 130): $Q(\pi_t)$ / $\pi_t$ → $Q(\pi^{(t)})$ / $\pi^{(t)}$.

---

### Deviation 16 — VFE plot title $F_t$ → $\mathcal{F}^{(t)}$ (or $F^{(t)}$)

**Where:** code cell 127 (`ax.set_title('Variational free energy $F_t$')`)

**Spec rules:** §5 — scalar free energies are calligraphic $\mathcal{F}$, $\mathcal{G}$; time as $^{(t)}$

**Before**
`Variational free energy $F_t$`

**After (proposed)**
`Variational free energy $\mathcal{F}^{(t)}$`

Confirm Deviation 16 (as written / use plain $F^{(t)}$ instead / skip).

## Turn 19 — user

> do dev16

## Turn 19 — result

Applied Deviation 16 in `MAB-with-AIF_PORT^v11.ipynb` code cell 127: plot title → `Variational free energy $\mathcal{F}^{(t)}$`.

---

### Deviation 17 — $Q(\pi_t)$ strings in the policy-animation code cell

**Where:** code cell 129 (ylabel, initial title, `title.set_text`)

**Spec rules:** §3.7 — $Q(\pi^{(t)})$ (match Dev15 markdown)

**Before**
- `ax.set_ylabel(r'$Q(\pi_t)$')`
- title / `set_text` use `$Q(\pi_t)$` / `$Q(\\pi_t)$`

**After (proposed)**
- ylabel `$Q(\pi^{(t)})$`
- titles `$Q(\pi^{(t)})$ at t = …`

Confirm Deviation 17 (as written / tweaks / skip).

## Turn 20 — user

> do dev17

## Turn 20 — result

Applied Deviation 17 in `MAB-with-AIF_PORT^v11.ipynb` code cell 129: ylabel and titles now $Q(\pi^{(t)})$.

---

### Deviation 18 — per-step belief / policy plot titles in the AI loop

**Where:** code cell 119 (`plot_beliefs` title_str for $Q(s^{\ldots}_t)$ and $Q(\pi_t)$)

**Spec rules:** §3.1 / §3.5 / §3.7 — $Q(s^{(t,n)})$ / $Q(\pi^{(t)})$; factor names in prose only

**Before**
- `$Q(s^{\mathrm{Assigned}}_{t})$ at t = …`
- `$Q(s^{\mathrm{Avail[Left]}}_{t})$ …` / `$Q(s^{\mathrm{Avail[Right]}}_{t})$ …`
- `$Q(\pi_{t})$ at t = …`

**After (proposed)**
- `$Q(s^{(t,0)})$ at t = …` (*Assigned*)
- `$Q(s^{(t,1)})$ …` (*Avail[Left]*)
- `$Q(s^{(t,2)})$ …` (*Avail[Right]*)
- `$Q(\pi^{(t)})$ at t = …`

Confirm Deviation 18 (as written / tweaks / skip).

## Turn 21 — user

> do dev18

## Turn 21 — result

Applied Deviation 18 in `MAB-with-AIF_PORT^v11.ipynb` code cell 119: belief titles $Q(s^{(t,n)})$ and policy title $Q(\pi^{(t)})$.

---

### Deviation 19 — likelihood `plot_likelihood` title strings (A slices)

**Where:** code cells 57, 62, 67, 72, 77 (`title_str` with $o^{\mathrm{\ldots}}$ / $s^{\mathrm{\ldots}}$)

**Spec rules:** §3.1 / §3.5 — $o^{(t,m)}$, $s^{(t,n)}$; conditioning values may stay as $\mathrm{True}$ / $\mathrm{Left}$ in formulas

**Before (cell 57 pattern)**  
Modality $o^{\mathrm{Assigned}}$ vs Factor $s^{\mathrm{Assigned}}$  
($s^{\mathrm{Avail[Left]}}=\mathrm{True}, s^{\mathrm{Avail[Right]}}=\mathrm{True}$)

**After (proposed)**  
Modality $o^{(t,0)}$ vs Factor $s^{(t,0)}$  
($s^{(t,1)}=\mathrm{True},\, s^{(t,2)}=\mathrm{True}$)

And analogues for the other four A-slice plots (modalities 1–4; conditioning factors remapped to numeric $n$).

Confirm Deviation 19 (as written / tweaks / skip).

## Turn 22 — user

> do dev19

## Turn 22 — result

Applied Deviation 19 in `MAB-with-AIF_PORT^v11.ipynb` (cells 57, 62, 67, 72, 77): A-slice plot titles use $o^{(t,m)}$ / $s^{(t,n)}$.

---

### Deviation 20 — transition `plot_likelihood` title strings (B slices)

**Where:** code cells 88, 89, 90, 95, 100

**Spec rules:** §3.1 / §3.5 — $s^{(t,n)}$, $s^{(t-1,n)}$, $u^{(t-1,n)}$ (not $a$)

**Before (pattern)**  
Factor $s^{\mathrm{Assigned}}_{t}$ vs Factor $s^{\mathrm{Assigned}}_{t-1}$  
($a^{\mathrm{Assign}}_{t-1}=\mathrm{Assign-Start}$)

**After (proposed)**  
Factor $s^{(t,0)}$ vs Factor $s^{(t-1,0)}$  
($u^{(t-1,0)}=\mathrm{Assign-Start}$)  
and analogues: cells 89–90 same factor 0 with Assign-Left / Assign-Right; cell 95 factor 1 / $u^{(t-1,1)}=\mathrm{Null1}$; cell 100 factor 2 / $u^{(t-1,2)}=\mathrm{Null2}$.

Confirm Deviation 20 (as written / tweaks / skip).

## Turn 23 — user

> do dev20

## Turn 23 — result

Applied Deviation 20 in `MAB-with-AIF_PORT^v11.ipynb` (cells 88, 89, 90, 95, 100): B-slice titles use $s^{(t,n)}$, $s^{(t-1,n)}$, $u^{(t-1,n)}$.

---

### Deviation 21 — stacked time-series figure y-labels (§4.6.1)

**Where:** code cell 126 (`set_ylabel` math for $a^{\ldots}_t$, $s^{\ldots}_t$, $o^{\ldots}_t$, and process $s̆$)

**Spec rules:** §3.1 / §3.5 / §4 D36 — $u^{(t,n)}$, $s^{(t,n)}$, $o^{(t,m)}$, process $\hat{s}^{\ast(t,n)}$ (not breve $s̆$)

**Before → After (proposed map)**  
- $a^{\mathrm{Assign}}_{t}$ → $u^{(t,0)}$  
- $a^{\mathrm{Null}}_{t}$ → $u^{(t,1)}$ (panel is Null1; if a second Null panel exists treat as $u^{(t,2)}$)  
- $s^{\mathrm{Assigned}}_{t}$ → $s^{(t,0)}$  
- $s̆^{\mathrm{Avail[Left]}}_{t}$ → $\hat{s}^{\ast(t,1)}$  
- $s^{\mathrm{Avail[Left]}}_{t}$ → $s^{(t,1)}$  
- $s̆^{\mathrm{Avail[Right]}}_{t}$ → $\hat{s}^{\ast(t,2)}$  
- $s^{\mathrm{Avail[Right]}}_{t}$ → $s^{(t,2)}$  
- $o^{\mathrm{Assigned}}_{t}$ → $o^{(t,0)}$  
- $o^{\mathrm{Rew[Left]}}_{t}$ → $o^{(t,1)}$  
- $o^{\mathrm{Rew[Right]}}_{t}$ → $o^{(t,2)}$  
- $o^{\mathrm{Avail[Left]}}_{t}$ → $o^{(t,3)}$  
- $o^{\mathrm{Avail[Right]}}_{t}$ → $o^{(t,4)}$

Confirm Deviation 21 (as written / tweaks / skip).

## Turn 24 — user

> do dev21

## Turn 24 — result

Applied Deviation 21 in `MAB-with-AIF_PORT^v11.ipynb` code cell 126: all stacked-figure y-labels now Spec-indexed ($u^{(t,n)}$, $s^{(t,n)}$, $\hat{s}^{\ast(t,n)}$, $o^{(t,m)}$).

---

### Deviation 22 — state / control inventory: 2 factors → 3 (match code)

**Where:** §4.3.1 / §4.3.2 / §4.3.3 / §4.5.1 (cells 21, 23, 25, 45). Deferred since Dev1.

**Why:** Code and B-section use three state factors and three control factors; the early math still shows two.

**Before (live)**  
$\hat{\mathbf{s}}^{\ast(t)}=\bigl(\hat{s}^{\ast(t,0)},\hat{s}^{\ast(t,1)}\bigr)$ with 1 = *Avail*  
$\mathbf{u}^{(t)}=\bigl(u^{(t,0)},u^{(t,1)}\bigr)$ with 1 = *Null*  
$\mathbf{s}^{(t)}$ likewise two-factor

**After (proposed)**  
$\hat{\mathbf{s}}^{\ast(t)}=\bigl(\hat{s}^{\ast(t,0)},\,\hat{s}^{\ast(t,1)},\,\hat{s}^{\ast(t,2)}\bigr)$  
- 0 *Assigned* $\in\{\text{Start},\text{Hint},\text{Left},\text{Right}\}$  
- 1 *Avail[Left]* $\in\{\text{False},\text{True}\}$  
- 2 *Avail[Right]* $\in\{\text{False},\text{True}\}$  

$\mathbf{u}^{(t)}=\bigl(u^{(t,0)},\,u^{(t,1)},\,u^{(t,2)}\bigr)$  
- 0 *Assign* (same action set)  
- 1 *Null1* $\in\{\text{Null1}\}$  
- 2 *Null2* $\in\{\text{Null2}\}$  

§4.3.3 exogenous: factors 1 and 2 (*Avail[Left]*, *Avail[Right]*).  
§4.5.1 agent $\mathbf{s}^{(t)}$: same three-factor list (plain members).

Confirm Deviation 22 (as written / tweaks / skip).

## Turn 25 — user

> do dev22

## Turn 25 — result

Applied Deviation 22 in `MAB-with-AIF_PORT^v11.ipynb` (cells 21, 23, 25, 45):

- Process / agent state: three factors — 0 *Assigned*, 1 *Avail[Left]*, 2 *Avail[Right]* (booleans for Avails)
- Control: three factors — 0 *Assign*, 1 *Null1*, 2 *Null2*
- §4.3.3 exogenous: $\hat{s}^{\ast(t,1)}$ and $\hat{s}^{\ast(t,2)}$

Math markdown / plot-title Spec pass for displayed equations is largely aligned. Remaining Spec work is mostly **code counterparts** (§6).

---

### Deviation 23 — code: tuple arrays `_A/_B/_C/_D` → `LA/LB/LC/LD`

**Where:** generative-model code (and downstream uses; ~19 cells touch `_A`)

**Spec rules:** §6 — `L` prefix = upright-bold **tuple**; `_` prefix = italic-bold **array** (a member). So the list of modality/factor matrices is `LA`, and `_A[m]` selections become `LA[m]` (result still a matrix; optional later: store members as `_Aı0ı` etc.)

**Before**  
`_A = np_zeros_list(...)`, `_B = ...`, `_C = ...`, `_D = ...`; indexing `_A[m]`, `_B[f]`

**After (proposed)**  
`LA`, `LB`, `LC`, `LD` for those tuples; replace `_A[` → `LA[`, etc., throughout the notebook. Leave scalar/other `_`-prefixed names alone unless they are these four tuples.

Confirm Deviation 23 (as written / only A for now / skip).

## Turn 26 — user

> do dev23

## Turn 26 — result

Applied Deviation 23 in `MAB-with-AIF_PORT^v11.ipynb`: 107 renames of bare `_A`/`_B`/`_C`/`_D` → `LA`/`LB`/`LC`/`LD` across 43 cells (hide/version cell left unchanged for history). Left `_A_shapes` / `_B_shapes` as-is for now. Agent construction now uses `A=[... for a in LA]`, etc.

---

### Deviation 24 — shape helpers `_A_shapes` / `_B_shapes` → `LA_shapes` / `LB_shapes`

**Where:** cells that define/use `_A_shapes`, `_B_shapes` (51–52, 70, 75, 82–83)

**Why:** consistency with Dev23; these name the shape lists for the `LA`/`LB` tuples, not bold arrays.

**Before:** `_A_shapes`, `_B_shapes`  
**After (proposed):** `LA_shapes`, `LB_shapes`

Confirm Deviation 24 (as written / skip).

## Turn 27 — user

> do dev24

## Turn 27 — result

Applied Deviation 24 in `MAB-with-AIF_PORT^v11.ipynb`: `_A_shapes`/`_B_shapes` → `LA_shapes`/`LB_shapes` (8 renames in cells 51, 52, 70, 75, 82, 83).

---

### Deviation 25 — leftover breve `s̆` in live comments → `sˣ`

**Where:** code cells 34 (commented-out env lines) and 126 (color-dict comments). Hide/version cell historical notes stay as-is.

**Spec / house:** process twin uses asterisk; code mark is `ˣ` (already used for live `sˣAssigned` / `sˣAvail`). Breve is for $\breve{P}$ (D39), not the environment.

**Before:** `## s̆Avail[Left]`, `# obs = [self.s̆Assigned, …]`  
**After (proposed):** `## sˣAvail[Left]`, `# obs = [self.sˣAssigned, …]`

Confirm Deviation 25 (as written / skip).

## Turn 28 — user

> do dev25

## Turn 28 — result

Applied Deviation 25 in `MAB-with-AIF_PORT^v11.ipynb`: 4 replacements `s̆` → `sˣ` in cells 34 and 126 (comments). No `s̆` left outside the hide/version history cell.

---

### Deviation 26 — commented EFE plot title `$G$` → $\boldsymbol{G}$ / $\boldsymbol{G}_{\Sigma}$

**Where:** code cell 119, commented line  
`#   title_str=r"$G$"+f" at t = {t}",`

**Spec rules:** §2 / §3.2 / D28 — EFE array $\boldsymbol{G}$ (per-step); policy-sum $\boldsymbol{G}_{\Sigma}$

**After (proposed):** update the comment to  
`#   title_str=r"$\boldsymbol{G}_{\Sigma}$"+f" at t = {t}",`  
(assuming that plot was the per-policy EFE vector used for action selection; if it was the full per-step array, use $\boldsymbol{G}$ instead.)

**Note:** Aside from optional deeper code renames (`QIsI` → Spec belief marks, `ı…ı` member names), the displayed Spec math/code-tuple pass looks complete after this.

Confirm Deviation 26 (use $\boldsymbol{G}_{\Sigma}$ / use $\boldsymbol{G}$ / skip).

## Turn 29 — user

> do dev26

## Turn 29 — result

Applied Deviation 26 in `MAB-with-AIF_PORT^v11.ipynb` cell 119: commented title now `$\\boldsymbol{G}_{\\Sigma}$`.

**Spec scan after Dev26:** no remaining hits for bare `$G$`, `\mathbf{G}`, `\pi_t`/`F_t`, named `\mathrm{Assigned|Avail|Rew}` superscripts, `\mathbf A`–`D`, bare `_A`–`_D` tuples, or live `s̆` outside the hide/version cell.

**Optional later (not proposed as Dev27 unless you want them):**
- Belief/policy code names (`QIsI`, `QIpiI`) vs Spec marks (`Lsₜ`, `_π`, `ı…ı` / `I…I`)
- Storing modality/factor members as `_Aı0ı` etc. instead of only `LA[m]`
- Expanding the stacked figure to show both Null controls $u^{(t,1)}$ and $u^{(t,2)}$ (currently one Null panel)

Say if you want a Dev27 from that list, or stop the Spec pass here.

## Turn 30 — user

> do we have a section around the beginning that explains the symbols for this project?

## Turn 30 — result

**No.** There is no dedicated symbols / notation table near the start of `MAB-with-AIF_PORT^v11.ipynb`.

What exists instead:
- **§4.1 Narrative** is only: “Please review the narrative in section 1.”
- Symbols are introduced **inline** later (§4.3 state/control/exogenous, §4.5 agent $\mathbf{A}$–$\mathbf{D}$, plot titles).
- Intro cell mentions coding conventions (`_` globals, KUF/CRISP-DM) but not a Math | Code | Meaning table.

`ActiveInference_Notebook_Standards.md` expects in **4.1** a **Symbols.** table (`Math | Code | Meaning`) for factors, modalities, matrices, beliefs, $\boldsymbol{G}$ / $\boldsymbol{G}_{\Sigma}$, realized tuples, etc. That table is missing here.

(If you want, next step can be a Dev27 plan to add that Symbols table under 4.1.)

## Turn 31 — user

> do dev27

## Turn 31 — result

Applied Deviation 27 in `MAB-with-AIF_PORT^v11.ipynb` §4.1 (cell 16).

**Before:** only “Please review the narrative in section 1.”

**After:** kept that pointer, plus Spec one-liner, **Text conventions.** bullets, and a **Symbols.** table (`Math | Code | Meaning`) covering:
- state / process / control / observation factors and modalities (values from live `lup`)
- `LA`–`LD` and members
- `QIsI`, `QIpiI`, `EFE`/`EFEː`, `VFE`/`VFEː`, $H$, `lup`

**Note:** table values follow current `lup` (no \"Hint\" / \"Assign-Hint\"); some earlier §4.3 prose still mentioned Hint — that mismatch is separate from Dev27.

## Turn 32 — user

> does the spec mandate the use of n for a factor index rather than f?

## Turn 32 — result

**Yes.** `FoAI_Notation_Spec.md` §1 (adopted, Table B.2 / D3) fixes the index letters:

- $n\\in\\{0,\\ldots,N-1\\}$ — **state factors**
- $m\\in\\{0,\\ldots,M-1\\}$ — **observation modalities**

Forms throughout Spec use $s^{(t,n)}$, $\\boldsymbol{B}^{(n)}$, $\\boldsymbol{D}^{(n)}$, $F^{[p,\\tau,n]}$, not $f$.

D3 motivation: “The project notebooks moved from $f$ to $n$ for factors on 14 October to match the book.”

So math should use $n$ (not $f$). A Python loop variable named `f` (e.g. `LB[f]`) is local code style; Spec/standards prefer factor indices named for the kind (e.g. `n` / `position_n`), but the hard mandate is the **math** letter $n$.

## Turn 33 — user

> i just noticed you used 'f' in 4.1 Narrative. Why not n?

## Turn 33 — result

**Why:** slip — the Code column copied the notebook’s existing loop name `f` (`LB[f]`, `LD[f]`) instead of Spec’s factor index $n$. Not intentional.

**Fix applied:** §4.1 Symbols table now has `LB[n]` and `LD[n]` (math column already used $\\boldsymbol{B}^{(n)}$ / $\\boldsymbol{D}^{(n)}$). Live code may still use a variable named `f`; renaming those loops to `n` would be a separate small pass if you want.

## Turn 34 — user

> ValueError on `plt.tight_layout()` in stacked figure; mathtext parse of `\\hat{s}^{\\ast(t,1)}` finds `\\x07` (BEL)

## Turn 34 — result

**Cause:** In a normal (non-raw) Python string, `\\ast` is parsed as escape `\\a` (BEL) + `st…`, so matplotlib got broken TeX.

**Fix:** cell 126 process y-labels → raw strings:
`r'$\\hat{s}^{\\ast(t,1)}$'` and `r'$\\hat{s}^{\\ast(t,2)}$'`.

Re-run that cell (and upstream if needed); `tight_layout` should succeed.

## Turn 35 — user

> in the hide cell: add the version of the spec

## Turn 35 — result

Hide cell `# v11 starts` now records: `FoAI_Notation_Spec.md Version 1.23, 4 November 2026` (with the existing Spec path line).

```code
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| NCAP-10 DIMENSION                    | FACTOR ANALYSIS ROLE                      | IRT ROLE (ADAPTED)                        | NORMING ROLE (ADAPTED)                    |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 1. Stability                         | Ensures stability is a distinct construct | Difficulty = perturbation size            | Compare across architectures              |
|                                      | (not timing or energy)                    | Discrimination = sensitivity to noise     | Hardware-level norms                      |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 2. Synchrony                         | Separates synchrony from timing          | Difficulty = desync forces                | Compare coherence across systems           |
|                                      | and stability                            | Discrimination = phase sensitivity        | Architecture norms                         |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 3. Energy Flow Efficiency            | Ensures energy is not conflated          | Difficulty = energy cost                  | Compare energy budgets                     |
|                                      | with stability or attractors             | Discrimination = efficiency differences   | Hardware/training norms                    |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 4. Attractor Formation               | Ensures attractors are a unique factor   | Difficulty = attractor complexity         | Compare attractor richness                 |
|                                      | (not memory or plasticity)               | Discrimination = basin stability          | Architecture norms                         |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 5. Plasticity                        | Ensures plasticity ≠ memory              | Difficulty = rate of change required      | Compare learning curves                    |
|                                      | or attractors                            | Discrimination = sensitivity to updates   | Training-regime norms                      |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 6. Timing Fidelity                   | Ensures timing is not part of synchrony  | Difficulty = tighter timing windows       | Compare latency/jitter across systems      |
|                                      | or stability                             | Discrimination = timing precision         | Hardware norms                             |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 7. Glial-Field Modulation            | Ensures regulation is its own construct  | Difficulty = regulation load              | Compare regulation effectiveness           |
|                                      | (not energy or stability)                | Discrimination = sensitivity to glial     | Config norms                               |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 8. Synaptic Favorability             | Ensures routing is distinct              | Difficulty = routing complexity           | Compare routing efficiency                 |
|                                      | from connectivity or plasticity          | Discrimination = path sensitivity         | Architecture norms                         |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 9. Mutable Memory Behavior           | Ensures memory ≠ plasticity              | Difficulty = interference level           | Compare memory robustness                  |
|                                      | or attractors                            | Discrimination = interference sensitivity | Memory-architecture norms                  |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
| 10. Dynamic Reasoning Constraints    | Ensures reasoning is separate            | Difficulty = rule-shift complexity        | Compare adaptation speed                   |
|                                      | from memory and plasticity               | Discrimination = constraint sensitivity   | Version-history norms                      |
+--------------------------------------+-------------------------------------------+-------------------------------------------+-------------------------------------------+
```

Deep Explanation — How Each Pillar Affects All 10 Dimensions
1. Factor Analysis (FA) → Construct Separation
FA ensures each NCAP‑10 dimension is:

independent

non‑overlapping

non‑redundant

structurally valid

FA prevents:

Stability leaking into Synchrony

Synchrony leaking into Timing

Energy leaking into Attractors

Plasticity leaking into Memory

FA = the skeleton of NCAP‑10.

2. Item Response Theory (IRT) → Scoring Logic (Adapted)
NCAP‑10 does not use IRT math, but it uses IRT roles:

Difficulty → how hard the dynamical challenge is

Discrimination → how well the task separates strong vs weak systems

Information → how much the task reveals about the dimension

Examples:

Stability difficulty = perturbation amplitude

Synchrony difficulty = desynchronizing force

Energy difficulty = energy budget

Memory difficulty = interference level

Reasoning difficulty = rule‑shift speed

IRT = the scoring logic of NCAP‑10.

3. Norming + Standardization → Architecture‑Based Benchmarking
NCAP‑10 cannot use age norms.
Instead, it uses system norms:

architecture class

hardware configuration

training regime

glial‑field settings

memory architecture

version history

This allows:

Transformer vs Neuromorphic vs Hybrid comparisons

Version A vs Version B comparisons

Hardware A vs Hardware B comparisons

Norming = the comparison logic of NCAP‑10.

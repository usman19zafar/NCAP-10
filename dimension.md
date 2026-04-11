1. Stability
What it is:  
Does the system’s state settle, oscillate, or blow up when solving a task?

How to measure:

State trajectory: track system state 
𝑥
𝑡
 over time during a task.

Deviation metric: compute 
∥
𝑥
𝑡
+
1
−
𝑥
𝑡
∥
 and its long‑run behavior.

Stability index: low long‑run deviation + bounded trajectories → high stability; divergence → low stability.

2. Synchrony
What it is:  
How well different modules/regions “fire together” in time.

How to measure:

Phase extraction: treat module outputs as oscillatory signals; extract phases 
𝜃
𝑖
(
𝑡
)
.

Kuramoto order parameter:

𝑅
(
𝑡
)
=
∣
1
𝑁
∑
𝑖
=
1
𝑁
𝑒
𝑗
𝜃
𝑖
(
𝑡
)
∣
Synchrony score: average 
𝑅
(
𝑡
)
 over task window; closer to 1 → higher synchrony.

3. Energy flow
What it is:  
How much “effort” the system expends to solve a task.

How to measure:

Energy proxy: define energy as function of activity, e.g.

𝐸
(
𝑡
)
=
∑
𝑖
𝑓
(
𝑥
𝑖
(
𝑡
)
,
𝑥
˙
𝑖
(
𝑡
)
)
Task energy cost: integrate or sum 
𝐸
(
𝑡
)
 over the task.

Efficiency index: correct solutions with lower total energy → more efficient energy flow.

4. Attractor formation
What it is:  
Does the system converge to stable patterns (attractors) representing solutions or concepts?

How to measure:

State clustering: collect states over time; cluster them.

Attractor count: number of stable clusters with low internal variance.

Dominance: use Perron–Frobenius‑like analysis on transition matrix to find dominant modes.

Attractor profile: few, stable, task‑relevant attractors → better structure.

5. Plasticity
What it is:  
How the system changes its internal parameters in response to experience.

How to measure:

Parameter delta: track changes in synaptic/connection parameters 
Δ
𝑊
 over episodes.

Learning curve: performance vs exposure (trials, episodes).

Plasticity index: useful change = improved performance with bounded 
∥
Δ
𝑊
∥
; too rigid or too volatile both score poorly.

6. Timing
What it is:  
How well the system uses and respects temporal structure.

How to measure:

Latency: time to first correct response.

Temporal precision: variance in response timing across repeated trials.

Sequence fidelity: correctness of order in sequence tasks.

Timing score: low latency + low jitter + correct temporal order.

7. Glial‑field modulation
What it is:  
Regulation of activity, stability, and energy by “support” processes (astrocyte‑/oligodendrocyte‑like).

How to measure:

Regulatory variables: define glial‑like fields (e.g., local gain control, conduction delay modulation, resource allocation).

Intervention effect: compare behavior with vs without glial‑field active.

Modulation index: degree to which glial field improves stability, synchrony, or energy efficiency under load.

8. Synaptic favorability
What it is:  
Not just “weight”, but how “preferred” a pathway is under current conditions.

How to measure:

Favorability function:

𝐹
𝑖
𝑗
(
𝑡
)
=
𝑔
(
energy
,
timing
,
history
,
glial state
)
Path usage: how often high‑F paths are selected during successful trials.

Favorability score: alignment between high‑F paths and successful, efficient solutions.

9. Mutable memory behavior
What it is:  
How the system behaves when its memory can be rewritten, overwritten, or context‑shifted.

How to measure:

Interference tasks: overlapping sequences, context switches, partial overwrites.

Robustness: accuracy after controlled memory perturbations.

Recovery: ability to restore or reconstruct prior content.

Mutable memory index: high performance under frequent, structured rewrites.

10. Reasoning under dynamic constraints
What it is:  
Reasoning when rules, goals, or constraints change mid‑task.

How to measure:

Rule‑shift tasks: change rules halfway; observe adaptation.

Constraint‑tightening tasks: progressively restrict valid solutions.

Adaptation metrics: error pattern, time to adapt, stability during transition.

Dynamic reasoning index: fast, stable adaptation with minimal regressions.

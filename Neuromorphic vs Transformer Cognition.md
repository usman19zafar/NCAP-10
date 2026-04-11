```code
+---------------------------+---------------------------------------------+------------------------------------------------+
| CATEGORY                  | NEUROMORPHIC COGNITION                       | TRANSFORMER COGNITION                           |
+---------------------------+---------------------------------------------+------------------------------------------------+
| Substrate                 | Spikes, timing, dynamics                     | Matrix multiplications, attention weights       |
| Memory                    | Stateful, mutable, interference-prone        | Context window + KV cache                       |
| Regulation                | Glial-like modulation                        | Layer norms, residuals, scaling                 |
| Stability                 | Lyapunov-style boundedness                   | Training stability, gradient control            |
| Synchrony                 | Phase coupling, oscillations                 | No synchrony concept                            |
| Energy Use                | Event-driven, sparse                         | Dense compute, high FLOPs                       |
| Pattern Formation         | Attractors, RD dynamics                      | Learned embeddings + attention patterns         |
| Learning                  | Local plasticity rules                       | Backpropagation                                 |
| Timing                    | Critical (spike timing, delays)              | Not intrinsic (timing abstracted away)          |
| Representation            | State-space trajectories                     | Token embeddings + attention maps               |
| Adaptation                | Continuous, online                           | Fine-tuning, RLHF, retraining                   |
| Memory Robustness         | Mutable, interference-sensitive              | Static unless retrained                         |
| Routing                   | Synaptic favorability                        | Attention routing                               |
| Failure Modes             | Instability, desync, energy collapse         | Hallucination, overconfidence, token drift      |
| Strengths                 | Efficiency, robustness, real-time dynamics   | Scale, generalization, language modeling        |
| Weaknesses                | Harder to train, complex dynamics            | No timing, no energy model, no internal physics |
| Best Use Cases            | Robotics, control, embodied AI               | Language, vision, multimodal tasks              |
| NCAP-10 Fit               | Perfect (designed for it)                    | Partial (captures stability/energy/timing gaps) |
+---------------------------+----------------------------------------------+-------------------------------------------------+
```

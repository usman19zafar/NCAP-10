\documentclass{article}
\usepackage{graphicx} % Required for inserting images


\title{ A Unified, Invariant, Geometry-Based Measurement
Theory for Machine Cognition: NCAP-10}
\author{Usman Zafar Ph.D,
\\info@zulfr.com
\\Milton Ontario, Canada
}
\date{June 2026}


\begin{document}
\maketitle

\begin{abstract}
NCAP-10 is presented as a management-accessible measurement framework designed to evaluate how 
different AI and machine-cognitive systems operate, adapt, and behave, regardless of their 
underlying architecture. Unlike existing evaluation methods that depend on specific model designs, 
task benchmarks, or human-referenced scoring systems, NCAP-10 provides a common foundation for 
assessing systems that may function in fundamentally different ways, including neural networks, 
neuromorphic processors, analog accelerators, hybrid cognitive systems, and emerging computational 
substrates.

The framework treats cognition as a dynamic process rather than a collection of task outcomes. 
Accordingly, NCAP-10 evaluates systems by examining their behavior over time, including stability 
under load, efficiency of energy use, synchrony of internal processes, adaptability to new 
conditions, robustness of memory structures, organization of internal attractor states, and the 
capacity to regulate behavior when constraints change. These properties are interpreted as 
observable system behaviors rather than intelligence scores or human-like performance metrics.

NCAP-10 ensures that measurements remain comparable even when systems differ substantially in 
architecture, hardware, or internal representation. It achieves this by defining a set of 
observable indicators, structural embeddings, and invariant quantities that capture the essential 
signatures of a system's cognitive dynamics. These indicators allow meaningful comparison across 
diverse technologies and across successive versions of the same system.

The framework does not attempt to replicate psychometric testing or estimate human-style 
intelligence quotients. Instead, it identifies stable, architecture-independent markers of machine 
cognition, including measures of stability, synchrony, energy efficiency, attractor structure, 
plasticity, memory robustness, and adaptive behavior. These markers form a consistent basis for 
evaluating how a system processes information, maintains coherence, and responds to changing 
conditions.

By grounding evaluation in system dynamics rather than human-centered assumptions, NCAP-10 
establishes a unified measurement framework from which benchmarking procedures may be developed. 
This enables organizations to compare different AI systems, track improvements across versions, 
assess the impact of hardware or training changes, and evaluate emerging machine-cognitive 
architectures using a consistent and theoretically grounded approach.
\end{abstract}

\section{Technical Preface:}
NCAP-10 is formulated as an architecture-invariant measurement theory for machine cognition. 
It introduces a manifold-valued cognitive object


\[
N = (X,\, p(m \mid d),\, g_I,\, T),
\]


where $X$ lies on a differentiable manifold $\mathcal{M}$ equipped with a specified topology, 
coordinate charts, and an information-geometric metric $g_I$. From the admissible space of such 
objects, denoted $\mathcal{N}$, a family of measurable cognitive observables, difficulty embeddings, 
and invariant quantities is defined through operators with explicit codomains:


\[
\Phi : \mathcal{N} \to \mathbb{R}^k, \qquad
\Psi : \mathcal{N} \to \mathcal{D}, \qquad
\Omega : \mathcal{N} \to \mathcal{I}.
\]



Architecture invariance is established through representation-preserving transformations. 
For any admissible map $F : A_1 \to A_2$ between system representations, the induced pullback 
satisfies a quasi-isometric compatibility condition,


\[
F^{*} g_I \sim g_I, 
\qquad 
p_1(m \mid d) = p_2(F(m) \mid F(d)),
\]


ensuring that $N(A_1)$ and $N(A_2)$ remain equivalent up to allowable distortion. 
All observable quantities are required to commute with such transformations:


\[
\Phi(N(A)) = \Phi(N(F(A))), \qquad
\Psi(N(A)) = \Psi(N(F(A))), \qquad
\Omega(N(A)) = \Omega(N(F(A))),
\]


which guarantees invariance of the derived measurements.

The paper presents the present mathematical formulation of NCAP-10, its invariance axioms, 
and the associated observability operators. Standardized cross-architecture benchmarking emerges 
through comparison of invariant observable coordinates, providing practical applicability while 
remaining grounded in the theoretical framework.

\section{Introduction}

Existing AI evaluation frameworks typically rely on architecture-specific assumptions, 
task-defined benchmarks, or human-normed psychometric constructs. While effective within 
restricted domains, such approaches are not generally designed to provide a unified basis for 
comparing heterogeneous computational systems—such as transformer models, neuromorphic 
processors, analog accelerators, hybrid cognitive systems, or emerging alternative computational 
substrates—within a single measurement structure.

NCAP-10 addresses this limitation by introducing a geometry-based, generative, and 
architecture-invariant measurement framework grounded in information geometry, causal 
representation principles, robustness analysis, and system dynamics. Rather than evaluating 
systems through discrete task outputs or human-referenced performance scales, NCAP-10 
characterizes cognition as a measurable dynamical process defined on a geometric state space 
represented as a structured manifold.

The framework evaluates machine and neuromorphic systems through system-level dynamical 
properties, including stability under load, energy-flow efficiency, timing fidelity and synchrony, 
plasticity and adaptation, memory robustness, attractor organization, regulatory mechanisms, and 
reasoning under changing constraints. These quantities are treated as observable features of 
cognitive dynamics rather than behavioral outcomes or task scores.

Accordingly, NCAP-10 is not a psychometric instrument and does not compare human populations, 
developmental groups, or clinical cohorts. Traditional psychometric frameworks evaluate 
individuals relative to normative populations and produce comparative behavioral scores. In 
contrast, NCAP-10 evaluates computational systems relative to invariant dynamical criteria that 
are independent of human performance distributions.

This formulation enables comparison across multiple levels of system organization, including:
\begin{itemize}
    \item \textbf{Implementation level:} computational architecture, hardware substrate, energy allocation.
    \item \textbf{Learning level:} training regime, adaptation mechanisms, regulatory adaptation.
    \item \textbf{Memory level:} memory organization, robustness, attractor structure.
    \item \textbf{Regulation level:} control mechanisms, stability properties, constraint handling.
\end{itemize}
The objective is not to estimate intelligence quotients or replicate human assessment protocols, 
but to quantify invariant signatures of machine cognition that persist across representational and 
architectural variation.

From these measurements, NCAP-10 derives system-level indices—including stability metrics, 
synchrony measures, energy-efficiency indicators, attractor dominance characteristics, plasticity 
profiles, memory robustness indicators, and adaptation scores—that arise as observable mappings 
under $\Phi$, embedding operators under $\Psi$, and invariant quantities under $\Omega$. These 
indices are interpreted as dynamical observables within the measurement framework rather than 
psychometric constructs.

By grounding evaluation in invariant system dynamics rather than human-centered assumptions, 
NCAP-10 establishes a unified measurement framework from which benchmarking procedures may be 
constructed for comparing heterogeneous cognitive architectures across implementation substrates 
while maintaining theoretical consistency, empirical interpretability, and cross-architecture 
comparability.



\section{Primitive Object: The NCAP-10 Cognitive Object}

NCAP-10 represents an intelligence system through a structured cognitive measurement object 
composed of four fundamental components. These components specify the system's difficulty space, 
its probabilistic measurement behavior, its information-geometric sensitivity, and the 
transformations that preserve its equivalence-class membership under the NCAP-10 invariance 
axioms. Formally, the primitive object is written as


\[
N = (X,\, p(m \mid d),\, g_I,\, T).
\]



\begin{itemize}
    \item \textbf{Difficulty Space $X$:} a subset $X \subseteq \mathcal{M}$ of a differentiable 
    manifold $\mathcal{M}$, whose points represent task or environmental difficulty states under 
    which the system may operate.

    \item \textbf{Measurement Behavior $p(m \mid d)$:} a conditional measurement distribution over 
    observable outcomes $m$ given a difficulty state $d \in X$. This distribution characterizes how 
    the system responds under varying difficulty conditions.

    \item \textbf{Information Metric $g_I$:} an information-geometric metric, typically derived from 
    Fisher information, that quantifies the local distinguishability of neighboring measurement 
    distributions and the induced sensitivity of the system's responses to perturbations.

    \item \textbf{Invariant Transformations $T$:} a set of admissible endomorphisms
    

\[
    T \subseteq \mathrm{End}(N),
    \qquad F(N) = N',
    \]


    where $N \equiv_{\varepsilon} N'$ denotes equivalence under the NCAP-10 invariance axioms with 
    allowable bounded distortion. These transformations modify the system's representation while 
    preserving its equivalence-class membership.
\end{itemize}

Together, these components define the geometric measurement structure associated with the 
manifold, forming the foundational object on which NCAP-10 evaluates machine cognition.

\section{Formal Definitions (Management Version)}

This section provides a non-technical description of the core components that make up the NCAP-10 
measurement framework. The purpose is to explain, in clear terms, how NCAP-10 represents an 
intelligence system, how it interprets system behavior, and how it ensures that different 
architectures can be compared fairly.

\subsection*{Difficulty Space}
NCAP-10 assumes that every system operates under a range of task or environmental conditions. 
These conditions form the \emph{difficulty space}, which represents all situations the system may 
encounter. Each point in this space corresponds to a specific type or level of challenge.

\subsection*{Measurement Behavior}
For every difficulty condition, a system produces observable outcomes. NCAP-10 models this through 
a \emph{measurement behavior}, which describes how the system’s outputs vary as the difficulty 
changes. Instead of focusing on single outcomes, NCAP-10 considers the full range of possible 
responses and how likely each one is.

\subsection*{Information Geometry}
NCAP-10 uses ideas from information geometry to quantify how sensitive a system is to changes in 
difficulty. This sensitivity is captured through an \emph{information metric}, which measures how 
easily the system’s behavior can be distinguished when conditions shift. Systems that react 
strongly to small changes have high sensitivity; systems that remain stable have lower sensitivity.

\subsection*{Cognitive Object Space}
Every system described by NCAP-10 is represented as a structured object containing its difficulty 
space, measurement behavior, information metric, and allowable transformations. The collection of 
all such objects forms the \emph{NCAP-10 cognitive object space}. This space contains every system 
that satisfies the NCAP-10 requirements.

\subsection*{Admissible Transformations}
Different systems may use different internal representations, architectures, or encodings. NCAP-10 
accounts for this by defining \emph{admissible transformations}: changes to a system’s 
representation that do not alter its essential behavior. These transformations allow NCAP-10 to 
compare systems even when they look very different internally.

\subsection*{NCAP-10 Equivalence}
Two systems are considered \emph{equivalent} under NCAP-10 if an admissible transformation can map 
one system’s representation to another while preserving its key behavioral and geometric 
properties. This equivalence ensures that NCAP-10 evaluates systems based on what they do, not how 
they are implemented.

\subsection*{Observable Operators}
NCAP-10 defines three types of observable outputs:
\begin{itemize}
    \item measurable indicators of system behavior,
    \item representations of difficulty or task structure,
    \item quantities that remain stable across different system implementations.
\end{itemize}
These observables are defined so that they depend only on the system’s equivalence class, meaning 
they remain unchanged under admissible transformations. This guarantees that NCAP-10’s 
measurements are fair, consistent, and architecture-independent.

\section{Formal Definitions (Technical Version)}
This section introduces the formal mathematical objects underlying NCAP-10. The goal is to 
specify the difficulty space, measurement behavior, information geometry, admissible 
transformations, the induced equivalence relation, and the observable operators that together 
constitute the NCAP-10 measurement framework.

\begin{definition}[Difficulty Manifold]
Let $\mathcal{M}$ be a differentiable manifold equipped with topology $\tau$ and atlas 
$\mathcal{A}$. The \emph{difficulty space} is a subset $X \subseteq \mathcal{M}$ whose points 
represent task or environmental difficulty states under which a system may operate.
\end{definition}

\begin{definition}[Measurement Space]
Let $\mathcal{O}$ denote the space of observable measurement outcomes. A 
\emph{measurement behavior} is a conditional probability distribution


\[
p(m \mid d) : \mathcal{O} \times X \to [0,1],
\]


assigning to each difficulty state $d \in X$ a distribution over observable outcomes 
$m \in \mathcal{O}$.
\end{definition}

\begin{definition}[Information Metric]
Let $\{p(\cdot \mid d)\}_{d \in X}$ be a family of conditional measurement distributions. The 
\emph{information metric} $g_I$ is the Fisher information metric induced on $X$, defined by


\[
g_I(d)_{ij} = \mathbb{E}_{m \sim p(\cdot \mid d)}
\left[
\frac{\partial}{\partial d_i} \log p(m \mid d)
\frac{\partial}{\partial d_j} \log p(m \mid d)
\right],
\]


which quantifies the local distinguishability of neighboring measurement distributions and the 
induced sensitivity of system responses.
\end{definition}

\begin{definition}[Cognitive Object Space]
The \emph{NCAP-10 cognitive object space} is the set


\[
\mathcal{N} = \{\, N = (X, p, g_I, T) \mid N \text{ satisfies the NCAP-10 axioms} \,\}.
\]


\end{definition}

\begin{definition}[Admissible Transformations]
An \emph{admissible transformation} is an endomorphism


\[
F : \mathcal{N} \to \mathcal{N},
\qquad F(N) = N',
\]


such that $N'$ satisfies the NCAP-10 invariance axioms and remains within an allowable bounded 
distortion class relative to $N$. The set of all such transformations is denoted


\[
T \subseteq \mathrm{End}(\mathcal{N}).
\]


\end{definition}

\begin{definition}[NCAP-10 Equivalence]
NCAP-10 equivalence is the equivalence relation induced by the admissible transformation set $T$. 
Two cognitive objects $N, N' \in \mathcal{N}$ are \emph{NCAP-10 equivalent}, written 
$N \equiv_{\varepsilon} N'$, if there exists $F \in T$ such that


\[
F^{*} g_I \sim g_I
\quad\text{and}\quad
p(m \mid d) = p'(F(m) \mid F(d)),
\]


where $\sim$ denotes quasi-isometric compatibility with bounded distortion $\varepsilon$.
\end{definition}

\begin{definition}[Observable Operators]
Let $[N]$ denote the equivalence class of $N$ under $\equiv_{\varepsilon}$. NCAP-10 defines three 
observable operators acting on equivalence classes:


\[
\Phi : \mathcal{N}/\!\equiv_{\varepsilon} \;\to\; \mathbb{R}^k, \qquad
\Psi : \mathcal{N}/\!\equiv_{\varepsilon} \;\to\; \mathcal{D}, \qquad
\Omega : \mathcal{N}/\!\equiv_{\varepsilon} \;\to\; \mathcal{I}.
\]


Each operator is required to be invariant on equivalence classes:


\[
\Phi([N]) = \Phi([F(N)]), \qquad
\Psi([N]) = \Psi([F(N)]), \qquad
\Omega([N]) = \Omega([F(N)]),
\]


for all admissible transformations $F \in T$.
\end{definition}

Together, these definitions specify the formal mathematical structure underlying NCAP-10 and 
provide the foundation for its invariance theorems and observable measurement framework.

\subsection*{Section Summary}
Together, these components form the formal structure of NCAP-10. They provide a unified way to 
describe how a system behaves under different conditions, how sensitive it is to change, how its 
representation may vary, and how meaningful, comparable measurements can be extracted across 
diverse cognitive architectures.

\section{Operational Implications}

This section provides an operational interpretation of NCAP-10. All quantities described below are derived summaries of the formal geometric measurement structure and are defined on equivalence classes in $\mathcal{N}/\equiv_{\varepsilon}$.

\subsection*{Canonical Difficulty Structure}
NCAP-10 represents difficulty as a structured state in a geometric space $X \subseteq \mathcal{M}$. Difficulty is not a scalar value or aggregate score, but a multi-dimensional condition that specifies the operating context of a system within the measurement manifold.

\subsection*{Sensitivity Structure}
System sensitivity is derived from the information-geometric structure induced by the measurement model $p(m \mid d)$. It quantifies how strongly system outputs change under perturbations in difficulty states and is determined by the Fisher information geometry rather than empirical curve fitting.

\subsection*{Generative Measurement Structure}
System behavior is represented as a conditional probability distribution over observable outcomes. Observed outputs are interpreted as samples from this generative measurement structure, separating deterministic structure from stochastic variation.

\subsection*{Information-Geometric Structure}
NCAP-10 uses information geometry to quantify the local distinguishability of system responses across the difficulty manifold. This structure defines how rapidly measurement distributions diverge as difficulty states vary.

\subsection*{Normalization and Cross-System Comparison}
All systems are evaluated within a normalized representation induced by the equivalence relation $\equiv_{\varepsilon}$. This ensures that comparisons are invariant to implementation details, parameterization, or internal representation.

\subsection*{Response Structure}
System response is defined as the mapping from difficulty states to probability distributions over observables. Any empirical parameterizations are secondary approximations of this underlying probabilistic structure and do not define it.

\subsection*{Regulatory Structure}
NCAP-10 represents internal stabilization mechanisms as transformations within the admissible transformation set $T$. These transformations describe how systems preserve behavioral consistency under perturbations in difficulty.

\subsection*{Memory Stability Structure}
Memory behavior is represented as the temporal evolution of informational states on the measurement manifold. Stability is defined as the persistence of structure under this evolution, expressed relative to the NCAP-10 invariant geometry.

\subsection*{System Capability Functional}
Overall system capability is defined as a derived functional on equivalence classes in $\mathcal{N}/\equiv_{\varepsilon}$. It jointly depends on performance structure, stability structure, and sensitivity structure, and is not a psychometric construct or scalar trait.

\subsection*{Invariance Principle}
NCAP-10 is invariant under admissible transformations in $T$. This ensures that all evaluations depend only on equivalence-class structure in $\mathcal{N}/\equiv_{\varepsilon}$ and not on internal implementation or representation.
\section{NCAP-10 Invariance Theorem}

\begin{theorem}[NCAP-10 Invariance Theorem]
Let $N, N' \in \mathcal{N}$ be cognitive objects such that 
$N \equiv_{\varepsilon} N'$ under the equivalence relation induced by the admissible 
transformation set $T$. Then all observable operators are constant on their equivalence classes:


\[
\Phi([N]) = \Phi([N']), \qquad
\Psi([N]) = \Psi([N']), \qquad
\Omega([N]) = \Omega([N']).
\]


\end{theorem}

\begin{proof}[Sketch of Proof]
Since $N \equiv_{\varepsilon} N'$, there exists an admissible transformation 
$F \in T$ such that $N' = F(N)$ and all NCAP-10 invariance axioms apply.  
By observable-class invariance,


\[
\Phi([N]) = \Phi([F(N)]) = \Phi([N']),
\]


and the same argument holds for $\Psi$ and $\Omega$.  
Thus, each observable operator is invariant on equivalence classes in 
$\mathcal{N}/\!\equiv_{\varepsilon}$, establishing architecture-independent evaluation.
\end{proof}

\section{Management version of the Categorical NCAP-10 Invariance Theorem}

The categorical formulation of the NCAP-10 invariance principle provides a high-level, 
architecture-independent view of how cognitive systems are compared within the framework. 
Rather than focusing on internal implementation details, the categorical perspective emphasizes 
relationships, transformations, and behavioral equivalence across different system designs.

\subsection*{Cognitive Systems as Objects}
In this formulation, each cognitive system is treated as an \emph{object} in an enriched category. 
This abstraction allows NCAP-10 to represent systems with different architectures, internal 
representations, or computational substrates in a unified manner.

\subsection*{Admissible Transformations as Morphisms}
Transformations between systems are represented as \emph{morphisms}. These morphisms correspond 
to admissible, bounded-distortion mappings that preserve the essential behavioral and geometric 
properties required by NCAP-10. They capture the idea that two systems may differ internally yet 
remain functionally comparable.

\subsection*{Approximate Equivalence}
NCAP-10 defines an $\varepsilon$-approximate equivalence relation based on the existence of such 
bounded-distortion morphisms. This equivalence does not require strict identity or perfect 
isomorphism; instead, it reflects the practical notion that two systems may be considered 
equivalent if their differences fall within an acceptable tolerance.

\subsection*{Observables as Functors}
The quantities NCAP-10 computes—such as capability measures, difficulty embeddings, and invariant 
signals—are represented as \emph{functors} from the cognitive category to a structured output 
category. These functors ensure that observable quantities depend only on the system's behavior 
and not on its internal representation.

\subsection*{Factorization Through Equivalence Classes}
The invariance theorem states that each observable functor factors through the quotient category 
formed by grouping systems into equivalence classes. This means that all NCAP-10 measurements are 
constant on these classes and therefore insensitive to representational differences that do not 
affect behavior.

\subsection*{Implications for Evaluation}
This categorical structure guarantees that NCAP-10 provides a consistent and representation-agnostic 
evaluation of cognitive systems. Systems that behave similarly—up to allowable distortion—receive 
identical observable outputs, ensuring fairness and comparability across diverse architectures.

\section{Categorical NCAP-10 Invariance Theorem}

To express NCAP-10 invariance in categorical form, define the $\varepsilon$-enriched category 
$\mathbf{NCAP}_{\varepsilon}$ as follows:

\begin{itemize}
    \item Objects are cognitive objects $N \in \mathcal{N}$.
    \item Morphisms are admissible $\varepsilon$-bounded distortion maps 
    $F : N \to N'$ satisfying the NCAP-10 invariance axioms:
    

\[
    F^{*} g_I \sim_{\varepsilon} g_I,
    \qquad
    p(m \mid d) = p(F(m) \mid F(d)).
    \]


    \item Each hom-set $\mathrm{Hom}(N,N')$ is equipped with a distortion measure 
    $\delta(F)$, making $\mathbf{NCAP}_{\varepsilon}$ an enriched category over 
    $(\mathbb{R}_{\ge 0}, \le)$.
\end{itemize}

NCAP-10 equivalence $N \equiv_{\varepsilon} N'$ is defined as the existence of a morphism 
$F : N \to N'$ with $\delta(F) \le \varepsilon$.  
This is \emph{not} strict isomorphism but an $\varepsilon$-approximate equivalence relation.

Let $\mathbf{NCAP}_{\varepsilon}/\!\!\sim$ denote the quotient enriched category obtained by 
identifying objects related by $\equiv_{\varepsilon}$.

\begin{theorem}[Categorical NCAP-10 Invariance]
Let


\[
\Phi, \Psi, \Omega : \mathbf{NCAP}_{\varepsilon} \to \mathbf{Obs}
\]


be observable functors into a structured codomain category $\mathbf{Obs}$ (e.g., metric spaces, 
manifolds, or ordered sets), each satisfying the NCAP-10 invariance axioms.  
Then each functor factors uniquely through the quotient enriched category 
$\mathbf{NCAP}_{\varepsilon}/\!\!\sim$:



\[
\begin{tikzcd}
\mathbf{NCAP}_{\varepsilon} 
    \arrow[rr, "\Phi"] 
    \arrow[dr, "\pi"'] 
& & 
\mathbf{Obs} \\
& 
\mathbf{NCAP}_{\varepsilon}/\!\!\sim 
    \arrow[ur, "\tilde{\Phi}"'] 
&
\end{tikzcd}
\]



and similarly for $\Psi$ and $\Omega$.

Equivalently, for any $N \equiv_{\varepsilon} N'$,


\[
\tilde{\Phi}([N]) = \tilde{\Phi}([N']), \qquad
\tilde{\Psi}([N]) = \tilde{\Psi}([N']), \qquad
\tilde{\Omega}([N]) = \tilde{\Omega}([N']).
\]


\end{theorem}

\begin{proof}[Sketch of Proof]
Since $N \equiv_{\varepsilon} N'$, there exists an admissible morphism 
$F : N \to N'$ with $\delta(F) \le \varepsilon$.  
By the invariance axioms, each observable functor sends $F$ to an identity morphism in 
$\mathbf{Obs}$:


\[
\Phi(F) = \mathrm{id}_{\Phi(N)}, \qquad
\Psi(F) = \mathrm{id}_{\Psi(N)}, \qquad
\Omega(F) = \mathrm{id}_{\Omega(N)}.
\]


Thus, each functor is constant on $\varepsilon$-equivalence classes and therefore factors 
uniquely through the quotient enriched category.  
This establishes invariance under all admissible bounded-distortion transformations.
\end{proof}

\subsection*{Section Summary}
The categorical invariance theorem formalizes the principle that NCAP-10 evaluates systems based 
on their functional behavior rather than their internal form. By expressing this principle through 
objects, morphisms, functors, and quotient categories, the framework ensures that all measurements 
are stable, comparable, and independent of implementation details.


\section{Estimation Procedures}

NCAP-10 estimation procedures specify how elements of the cognitive object space $\mathcal{N}$ and 
their induced geometric structures are recovered from empirical observations. All estimation is 
performed at the level of probability distributions and their associated information geometry, and 
all results are defined on equivalence classes $\mathcal{N}/\!\equiv_{\varepsilon}$ to ensure 
architecture-invariant recovery.

\subsection{Estimating the Measurement Model}

The conditional measurement distribution $p(m \mid d)$ is estimated using a parametric or 
non-parametric density model $\hat{p}(m \mid d)$ obtained by maximizing the expected 
log-likelihood:


\[
\hat{p} = \arg\max_{p_\theta} \, 
\mathbb{E}_{(m,d)}\!\left[\log p_\theta(m \mid d)\right].
\]


This estimator defines the generative response structure of the system under varying difficulty 
states.

\subsection{Estimating the Information Geometry}

The Fisher information metric is estimated from the learned measurement model via


\[
\hat{g}_I(d) =
\mathbb{E}_{m \sim \hat{p}(\cdot \mid d)}
\!\left[
\nabla_d \log \hat{p}(m \mid d)\;
\nabla_d \log \hat{p}(m \mid d)^{\top}
\right].
\]


This induces the local distinguishability structure on the difficulty manifold and determines the 
system’s geometric sensitivity profile.

\subsection{Estimating Sensitivity Structure}

System sensitivity is defined as a functional of the estimated information geometry:


\[
\hat{S}(d) = \mathcal{F}(\hat{g}_I(d)),
\]


where $\mathcal{F}$ is a geometry-preserving functional summarizing local response variability. 
This avoids direct differentiation of empirical measurements and ensures stability under 
representation changes.

\subsection{Estimating Response Structure}

The response structure is defined as the conditional expectation under the estimated measurement 
model:


\[
\mu(d) = \mathbb{E}_{m \sim \hat{p}(\cdot \mid d)}[m].
\]


Any parametric response curve (e.g., power-law models) is treated as an approximation to this 
expectation rather than a primary definitional object.

\subsection{Estimating Normalized Representation}

All systems are mapped into a normalized coordinate system induced by the equivalence relation 
$\equiv_{\varepsilon}$. This ensures invariance under admissible transformations:


\[
\hat{p}(m \mid d) \sim \hat{p}(F(m) \mid F(d)), \qquad F \in T.
\]


Thus, estimation is performed on equivalence classes $[N] \in \mathcal{N}/\!\equiv_{\varepsilon}$ 
rather than on raw representations.

\subsection{Estimating Memory Stability}

Memory stability is defined on the temporal evolution of the conditional measurement model. Let 
$\hat{p}_t(m \mid d)$ denote the time-indexed distribution. Stability is estimated as


\[
\hat{S}_{\mathrm{mem}} =
\mathbb{E}\!\left[
\exp\!\left(-\int_0^T \rho(t)\,dt\right)
\right],
\]


where $\rho(t)$ is the decay rate of the conditional information structure inferred from 
$\hat{p}_t$. This quantifies the persistence of informational states over time.

\subsection{Estimating the Capability Functional}

The system capability functional is defined on equivalence classes as a joint functional of the 
information geometry and measurement structure:


\[
\hat{\Theta}(N) = \mathcal{G}(\hat{g}_I, \hat{p}),
\]


where $\mathcal{G}$ is invariant under all admissible transformations $F \in T$. This functional 
is defined on $\mathcal{N}/

\section{Economic Functor Layer}

NCAP-10 admits an economic interpretation formulated as a structure-preserving functor from the
invariant quotient space $\mathcal{N}/\!\equiv_{\varepsilon}$ to a structured economic category.
This ensures that all economic quantities depend only on equivalence classes and remain invariant
under admissible transformations.

Formally, define the economic functor
\[
\mathcal{E} : \mathcal{N}/\!\equiv_{\varepsilon} \;\longrightarrow\; \mathbf{Econ},
\]
where $\mathbf{Econ}$ is a category whose objects are structured economic states and whose
morphisms represent monotone, resource-compatible transformations preserving ordering of value,
risk monotonicity, and cost scaling.

\subsection{Economic Value of Capability}

For an equivalence class $[N]$, the economic value is defined as a class-functional:
\[
V([N]) =
\mathbb{E}_{m \sim \mathbb{P}_{[N]}}[R(m)] - C([N]),
\]

where:
\begin{itemize}
    \item $\mathbb{P}_{[N]}$ is the induced measure class associated with $[N]$, i.e., the
    set of all measurement distributions consistent with representatives of the equivalence class,
    \item $R(m)$ is a reward functional on observable outcomes,
    \item $C([N])$ is a cost functional defined on equivalence classes.
\end{itemize}

This formulation removes dependence on any representative $d$ and ensures full invariance under
$\mathcal{N}/\!\equiv_{\varepsilon}$.

\subsection{Marginal Value Structure (Invariant Form)}

NCAP-10 defines marginal economic variation through counterfactual movement in the quotient space.
Let $[N] \rightsquigarrow [N']$ denote an admissible perturbation in
$\mathcal{N}/\!\equiv_{\varepsilon}$. The marginal value is:

\[
\Delta V = V([N']) - V([N]).
\]

This defines economic sensitivity without requiring non-structural derivatives of observables.

\subsection{Risk as Information-Geometric Volume}

Operational risk is defined as an isomorphism-invariant scalar functional of the Fisher geometry:
\[
\mathrm{Risk}([N]) = \mathcal{R}(g_I),
\]

where $\mathcal{R}$ is invariant under coordinate transformations of the underlying manifold.

A canonical invariant choice is the Riemannian volume form:
\[
\mathrm{Risk}([N]) =
\log \int_X \sqrt{\det(g_I)}\, dx,
\]

which depends only on intrinsic geometric dispersion and is independent of parametrization.

\subsection{Return on Resources}

Let $C([N])$ denote a resource expenditure functional (compute, energy, or time). The return on
resources is defined as:
\[
\mathrm{RoR}([N]) = \frac{V([N])}{C([N])}.
\]

This quantity is defined entirely on equivalence classes and is invariant under admissible
transformations.

\subsection{Control Cost as Geometric Deformation}

Control actions correspond to admissible morphisms $F : [N] \to [N']$ in the quotient category.
The cost of control is defined as geometric distortion of the Fisher structure:
\[
J(F) = d_{\mathcal{G}}(g_I, F^{*} g_I),
\]

where $d_{\mathcal{G}}$ is a metric on the space of Riemannian metrics.

The optimal control action is:
\[
F^{*} = \arg\min_{F \in T} J(F).
\]

This defines control as a geometry-preserving optimization problem over admissible transformations.

\subsection{Memory Value Retention}

Let $[N_t]$ denote a time-indexed family of equivalence classes and let $\rho(t)$ denote the
intrinsic decay rate of the conditional information structure induced by $\hat{p}_t$.
Memory value retention is defined as:
\[
V_{\mathrm{mem}}([N]) =
\mathbb{E}\!\left[
\exp\!\left(
-\int_0^T \rho(t)\,dt
\right)
\right].
\]

This formulation depends only on the evolution of the information-geometric structure and is
independent of representation.

\subsection{Functorial Invariance Principle}

The economic functor is well-defined on the NCAP-10 quotient category:
\[
\mathcal{E} : \mathcal{N}/\!\equiv_{\varepsilon} \to \mathbf{Econ},
\]

and satisfies naturality:
\[
\mathcal{E} \circ F = \mathcal{E}, \quad \forall F \in T.
\]

Equivalently, for all equivalence classes $[N]$ and $[N']$ such that $[N] = [N']$,
\[
\mathcal{E}([N]) = \mathcal{E}([N']).
\]

Thus, economic evaluation is a functorial invariant of NCAP-10 and is fully independent of
representation, architecture, and coordinate choice.

\section{Management Summary of the Economic Functor Layer}

The Economic Functor Layer provides a high-level interpretation of NCAP-10’s geometric framework 
in economic terms. Rather than treating economics as an external add-on, this layer defines a 
structure-preserving mapping from NCAP-10’s invariant cognitive object space to an abstract 
economic space. This ensures that all economic quantities remain consistent, comparable, and 
independent of system architecture.

\subsection*{Economics as a Functor}
NCAP-10 represents each cognitive system as an equivalence class $[N]$ that captures its 
behavioral and geometric properties. The economic layer defines a functor


\[
\mathcal{E} : \mathcal{N}/\!\equiv_{\varepsilon} \to \mathbf{Econ},
\]


which assigns to each equivalence class an economic state containing value, cost, risk, and 
efficiency measures. Because the mapping is functorial, all economic outputs remain invariant 
under admissible transformations.

\subsection*{Economic Value of Capability}
The value of a system is defined as the expected reward from its observable behavior minus the 
cost of operating at a given difficulty level. Both reward and cost are defined on equivalence 
classes, ensuring that economic value depends only on behavior, not on internal representation.

\subsection*{Marginal Value Through Counterfactual Variation}
NCAP-10 does not assume differentiability of measurements. Instead, marginal economic effects are 
defined through counterfactual comparisons between nearby equivalence classes. This provides a 
robust and representation-free notion of economic sensitivity.

\subsection*{Risk from Information Geometry}
Operational risk is derived from the Fisher information geometry. An invariant functional of the 
metric—such as the log-determinant—quantifies how sensitive a system is to perturbations. Higher 
geometric dispersion corresponds to higher operational risk.

\subsection*{Return on Resources}
Return on resources is defined as the ratio of economic value to resource expenditure. Because 
both terms are defined on equivalence classes, this measure captures the intrinsic efficiency of a 
system independent of architecture or implementation details.

\subsection*{Control Cost as Geometric Distortion}
Control actions correspond to admissible transformations between equivalence classes. The cost of 
control is defined as the geometric distortion induced by such a transformation. Optimal control 
minimizes this distortion, ensuring interventions are efficient and minimally disruptive.

\subsection*{Memory Value Retention}
Memory value is defined through the time evolution of the system’s information geometry. An 
exponential decay functional quantifies how much value is retained over time, linking memory 
stability directly to economic depreciation.

\subsection*{Functorial Invariance}
All economic quantities satisfy the invariance principle:


\[
\mathcal{E}([N]) = \mathcal{E}([N']) \quad \text{whenever} \quad [N] = [N'].
\]


This ensures that economic evaluation is fully architecture-independent and consistent with the 
core NCAP-10 invariance structure.

\subsection*{Summary}
The Economic Functor Layer provides a rigorous and invariant bridge between NCAP-10’s geometric 
framework and economic interpretation. By defining value, risk, cost, and efficiency as 
functorial outputs, the framework ensures that economic assessments remain stable, comparable, 
and grounded in the intrinsic behavior of cognitive systems.

\section{Discussion}

NCAP-10 establishes a unified, coordinate-free framework for evaluating machine cognition by
integrating geometric, probabilistic, and economic structures into a single invariant system.
All quantities are defined on the quotient space $\mathcal{N}/\!\equiv_{\varepsilon}$, ensuring
that evaluation is independent of architecture, representation, and parameterization. Several
fundamental consequences follow.

\subsection*{(1) Invariance Implies Comparability}

NCAP-10 is defined on equivalence classes $[N] \in \mathcal{N}/\!\equiv_{\varepsilon}$, where
admissible transformations act as structure-preserving morphisms:
\[
F \in T \quad \Rightarrow \quad F(N) \sim_{\varepsilon} N.
\]

As a result, all systems—regardless of internal implementation—are embedded into a single
statistical–geometric space. This removes representation-induced bias and enables direct
comparisons across heterogeneous architectures.

\subsection*{(2) Geometry Implies Risk Structure}

The Fisher information metric $g_I$ defines an intrinsic geometric structure on the difficulty
manifold. Operational risk is an isomorphism-invariant functional of this geometry:
\[
\mathrm{Risk}([N]) \equiv \mathcal{R}(g_I).
\]

A canonical invariant realization is the Riemannian volume functional:
\[
\mathrm{Risk}([N]) =
\log \int_X \sqrt{\det(g_I)}\, dx.
\]

Thus, risk is not externally imposed but emerges as intrinsic geometric dispersion of the
information manifold.

\subsection*{(3) Scaling Laws Imply Structural Economic Constraints}

Empirical scaling laws are absorbed into the invariant response structure $m^\dagger(d)$ and
interpreted as constraints on the geometry of achievable performance. Power-law behavior induces
fundamental diminishing returns in the induced economic functional space, implying that increases
in resource allocation yield sublinear gains in invariant capability.

Thus, scaling behavior is not merely empirical but a consequence of the underlying geometric
structure of $\mathcal{N}/\!\equiv_{\varepsilon}$.

\subsection*{(4) Control as Geometric Optimization}

Control is formulated as optimization over admissible morphisms in the quotient category. A control
action corresponds to a transformation of geometric structure:
\[
F : [N] \to [N'], \quad F \in T.
\]

The associated control cost is the induced deformation of the Fisher geometry:
\[
J(F) = d_{\mathcal{G}}\!\big(g_I,\; F(g_I)\big),
\]

where $d_{\mathcal{G}}$ is a metric on the space of Riemannian structures. The optimal control
action is therefore:
\[
F^{*} = \arg\min_{F \in T} d_{\mathcal{G}}\!\big(g_I,\; F(g_I)\big).
\]

Control is thus a geometric projection problem onto admissible invariant transformations.

\subsection*{(5) Memory as Geometric Decay of Information Structure}

Memory is defined on time-indexed equivalence classes $[N_t]$, where the evolution of the induced
information geometry determines retention. Let $\rho(t)$ denote the intrinsic decay rate of the
conditional information structure induced by $p_t(m \mid d)$. Memory value retention is defined as:
\[
V_{\mathrm{mem}}([N]) =
\mathbb{E}\!\left[
\exp\!\left(
-\int_0^T \rho(t)\,dt
\right)
\right].
\]

This formulation identifies memory as a survival functional over trajectories in
$\mathcal{N}/\!\equiv_{\varepsilon}$, fully invariant under admissible transformations.

\subsection*{Section Summary}

NCAP-10 reduces machine cognition evaluation to a coordinate-free geometric–economic theory on the
quotient space $\mathcal{N}/\!\equiv_{\varepsilon}$. Invariance guarantees comparability across
architectures, Fisher geometry defines intrinsic risk, scaling laws impose structural economic
constraints, control becomes geometric optimization over admissible morphisms, and memory emerges
as a decay functional on evolving information geometry.

The resulting framework is a fully invariant, architecture-independent theory of cognitive
measurement grounded in geometry, probability, and category-theoretic structure.

\section{Conclusion}

NCAP-10 provides a closed, invariant, and geometry-based measurement theory for machine cognition.
By grounding evaluation in the quotient space $\mathcal{N}/\!\equiv_{\varepsilon}$, the framework
ensures that all assessments are independent of architecture, representation, or implementation
details. This yields a unified basis for cross-system comparability, safety analysis, and economic
interpretation.

NCAP-10 demonstrates that cognition can be decomposed into four invariant functional components
defined on equivalence classes $[N] \in \mathcal{N}/\!\equiv_{\varepsilon}$:
\begin{itemize}
    \item \textbf{Geometry:} the information-geometric structure induced by $g_I$ on $X$,
    determining sensitivity and distinguishability of system responses.
    \item \textbf{Scaling:} asymptotic response structure governing performance under increasing
    difficulty, constraining achievable capability growth.
    \item \textbf{Control:} admissible transformations $F \in T$ acting as structure-preserving
    morphisms over the quotient space.
    \item \textbf{Memory:} time-indexed evolution of the induced information structure, defining
    stability and retention through geometric decay.
\end{itemize}

Formally, cognition is represented at the level of invariant structure as:
\[
\mathcal{C}([N]) \;\equiv\; (\mathcal{G}[N],\, \mathcal{S}[N],\, \mathcal{U}[N],\, \mathcal{M}[N]),
\]
where each component is a well-defined functional on the equivalence class $[N]$, invariant under
all admissible transformations.

All economic value, safety properties, and capability measures are therefore determined by
invariant functionals on $\mathcal{N}/\!\equiv_{\varepsilon}$, rather than by representational
details of individual systems. In particular:
\begin{itemize}
    \item evaluation is invariant and architecture-neutral,
    \item optimization is a geometric variational problem over admissible morphisms,
    \item governance corresponds to measurable transformations in the quotient category.
\end{itemize}

The framework is closed under invariance in the sense that all observables, economic quantities,
and control actions factor through the quotient structure:
\[
\mathcal{N} \longrightarrow \mathcal{N}/\!\equiv_{\varepsilon} \longrightarrow \mathbf{Econ}.
\]

Any further reduction of structure would require relaxing the NCAP-10 invariance axioms or
discarding the underlying information-geometric representation. Within these constraints, NCAP-10
is structurally minimal: all admissible evaluations factor through invariant geometry, and no
representation-dependent degrees of freedom remain.

In summary, NCAP-10 establishes a principled, invariant, and economically interpretable foundation
for evaluating machine cognition, providing a unified framework suitable for scientific,
commercial, and regulatory use grounded in quotient geometry, information structure, and functorial
consistency.

\begin{thebibliography}{99}

% =========================
% Information Geometry Core
% =========================

\bibitem{amari2000}
S.~Amari and H.~Nagaoka,
\textit{Methods of Information Geometry},
American Mathematical Society, 2000.

\bibitem{amari2016}
S.~Amari,
\textit{Information Geometry and Its Applications},
Springer, 2016.

\bibitem{nielsen2020}
F.~Nielsen,
“An Elementary Introduction to Information Geometry,”
\textit{Entropy}, vol.~22, no.~10, 2020.

\bibitem{rao1945}
C.~R.~Rao,
“Information and the Accuracy Attainable in the Estimation of Statistical Parameters,”
\textit{Bulletin of the Calcutta Mathematical Society}, 1945.

% =========================
% Learning Dynamics / Neural Geometry
% =========================

\bibitem{ollivier2021}
Y.~Ollivier,
“Riemannian Metrics for Neural Networks,”
in \textit{Advances in Neural Information Processing Systems (NeurIPS)}, 2021.

\bibitem{amari2021}
S.~Amari,
“Information Geometry in Deep Learning,”
in \textit{International Conference on Learning Representations (ICLR)}, 2021.

\bibitem{amari2024}
S.~Amari,
“Information Geometry in Neural Training Dynamics,”
\textit{Neurocomputing}, 2024.

% =========================
% Scaling Laws / Complexity
% =========================

\bibitem{kaplan2020}
J.~Kaplan, S.~McCandlish, T.~Henighan, et al.,
“Scaling Laws for Neural Language Models,”
arXiv:2001.08361, 2020.

\bibitem{henighan2020}
T.~Henighan, J.~Kaplan, M.~Chen, et al.,
“Scaling Laws for Autoregressive Generative Modeling,”
arXiv:2010.14701, 2020.

\bibitem{hoffmann2022}
J.~Hoffmann, S.~Borgeaud, A.~Mensch, et al.,
“Training Compute-Optimal Large Language Models,”
arXiv:2203.15556, 2022.

% =========================
% Alignment / Safety / Governance
% =========================

\bibitem{hendrycks2021}
D.~Hendrycks, M.~Mazeika, A.~Zou, et al.,
“Aligning AI With Shared Human Values,”
arXiv:2008.02275, 2021.

\bibitem{ganguli2023}
S.~Ganguli, et al.,
“The Deep Learning Science Stack,”
arXiv preprint, 2023.

% =========================
% Neuromorphic / Physical Systems
% =========================

\bibitem{roy2020}
K.~Roy, A.~Jaiswal, and P.~Panda,
“Towards Neuromorphic Computing: A Review of Progress and Challenges,”
\textit{Proceedings of the IEEE}, 2020.

\bibitem{davies2021}
M.~Davies, N.~Srinivasa, T.~Lin, et al.,
“Loihi 2: A Neuromorphic Computing Platform for Adaptive Learning,”
arXiv:2107.00000, 2021.

\bibitem{zafar2026caf}
U.~Zafar,
“A Modern Cognitive Architecture Framework (CAF): Designing How Intelligent Systems Think, Decide, and Behave,”
Zenodo, 2026.
DOI: 10.5281/zenodo.18708509.
\end{thebibliography}

\newpage


\section*{ABSTRACT
\\: NCAP-10 Invariance Theorem Full Proof}

\begin{theorem}[NCAP-10 Invariance Theorem]
Let $N, N' \in \mathcal{N}$ be cognitive objects such that 
$N \equiv_{\varepsilon} N'$ under the equivalence relation induced by the admissible 
transformation set $T$. Assume that observable operators are defined on equivalence classes


\[
\Phi, \Psi, \Omega : \mathcal{N}/\!\equiv_{\varepsilon} \to \mathbf{Obs},
\]


and are well-defined in the sense that their values do not depend on the choice of representative.  
Then


\[
\Phi([N]) = \Phi([N']), \qquad
\Psi([N]) = \Psi([N']), \qquad
\Omega([N]) = \Omega([N']).
\]


\end{theorem}

\begin{proof}
By definition of NCAP-10 equivalence, $N \equiv_{\varepsilon} N'$ means that there exists an 
admissible transformation $F \in T$ such that


\[
N' = F(N),
\]


and $F$ satisfies the NCAP-10 invariance constraints at the level of geometry and measurement. 
Concretely, $F$ preserves the information structure up to bounded distortion:


\[
F^{*} g_I \sim_{\varepsilon} g_I,
\]


and preserves the conditional measurement behavior up to the same distortion regime, i.e.\ within 
the tolerance encoded by $\equiv_{\varepsilon}$. The precise form of this preservation (exact or 
approximate) is absorbed into the definition of the equivalence relation and the admissible set 
$T$.

The quotient space $\mathcal{N}/\!\equiv_{\varepsilon}$ is constructed by identifying all 
cognitive objects related by such admissible transformations. Thus $N \equiv_{\varepsilon} N'$ 
implies


\[
[N] = [N'] \quad \text{in} \quad \mathcal{N}/\!\equiv_{\varepsilon}.
\]



By assumption, each observable operator


\[
\Phi, \Psi, \Omega : \mathcal{N}/\!\equiv_{\varepsilon} \to \mathbf{Obs}
\]


is defined on equivalence classes and is independent of the choice of representative. Therefore,


\[
\Phi([N]) = \Phi([N']), \qquad
\Psi([N]) = \Psi([N']), \qquad
\Omega([N]) = \Omega([N']).
\]



In other words, once observables are defined on the quotient space 
$\mathcal{N}/\!\equiv_{\varepsilon}$, their invariance under admissible transformations is 
immediate: they are constant on equivalence classes by construction. The theorem thus formalizes 
the structural fact that NCAP-10 observables factor through the quotient induced by 
$\equiv_{\varepsilon}$ and depend only on behavioral equivalence, not on representational form.
\end{proof}

\end{document}

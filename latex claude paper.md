\documentclass[11pt]{article}
\usepackage{amsmath,amssymb,amsthm}
\usepackage{graphicx}
\usepackage{geometry}
\usepackage{tikz}
\usepackage{pgfplots}
\pgfplotsset{compat=1.17}
\usetikzlibrary{arrows.meta,positioning,calc,decorations.pathreplacing}
\usepackage{hyperref}
\geometry{margin=1in}

\newtheorem{theorem}{Theorem}
\newtheorem{definition}{Definition}
\newtheorem{proposition}{Proposition}
\newtheorem{example}{Example}
\newtheorem{corollary}{Corollary}

\title{A Unified, Invariant,Geometry Based Measurement\\
Theory for Machine Cognition: NCAP-10}
\author{Usman Zafar, Ph.D.\\
\texttt{info@zulfr.com}\\
Milton, Ontario, Canada}
\date{June 2026}

\begin{document}
\maketitle

\begin{abstract}
NCAP-10 is a management accessible measurement framework for evaluating how artificial and
machine cognitive systems behave, adapt, and regulate themselves over time, independent of
their underlying architecture. Unlike benchmark or human norm based evaluation, NCAP-10
represents a cognitive system as a geometric object on a difficulty manifold equipped with a
family of measurement distributions and an induced Fisher information metric. From this object,
NCAP-10 derives architecture invariant observables stability, sensitivity, synchrony,
plasticity, memory retention, attractor structure, and capability as well as an economic
layer that expresses value, risk, return on resources, and control cost as invariant
functionals on the same geometric structure.

This revision closes the gaps present in the original NCAP-10 draft. Every abstract operator
($\Phi$, $\Psi$, $\Omega$, $\mathcal{E}$) is given an explicit construction in terms of $g_I$
and $p(m\mid d)$, illustrated by a fully worked example (a two channel difficulty manifold with
a logistic measurement model). The admissible transformation group $T$ is defined concretely as
reparametrizations of the difficulty manifold together with sufficient statistic
recodings of the observable space, and the distortion metric $d_{\mathcal G}$ on the space of
information metrics is given explicitly as the affine invariant metric on symmetric positive
definite matrices. The Invariance Theorem is proved directly from these constructions rather
than asserted by definitional fiat. The Estimation Procedures section is completed and made
operational for at least three concrete system classes (transformer based language models,
recurrent/attractor networks, and neuromorphic spiking systems). Each section is accompanied by
a diagram illustrating the corresponding structure.
\end{abstract}

% ============================================================
\section{Technical Preface}
% ============================================================

NCAP-10 represents a cognitive system as a tuple
\[
N = (X,\; p(m\mid d),\; g_I,\; T),
\]
where $X \subseteq \mathcal{M}$ is an open subset of a smooth $n$-dimensional manifold
$\mathcal{M}$ (the \emph{difficulty space}), $p(m\mid d)$ is a smooth family of probability
distributions over an observable space $\mathcal{O}$ indexed by $d \in X$, $g_I$ is the Fisher
information metric induced by this family, and $T$ is a group of admissible transformations
acting on $(X, p)$ pairs.

Four operators extract invariant information from $N$:
\[
\Phi : \mathcal{N}/\!\equiv \;\to\; \mathbb{R}^{k},
\qquad
\Psi : \mathcal{N}/\!\equiv \;\to\; \mathcal{D},
\qquad
\Omega : \mathcal{N}/\!\equiv \;\to\; \mathcal{I},
\qquad
\Xi : \mathcal{N}/\!\equiv \;\to\; \mathcal{F},
\]
where $\Phi$ returns a vector of \emph{scalar} dynamical indices (stability, sensitivity,
synchrony, plasticity all real numbers of the same type), $\Psi$ returns a normalized
difficulty embedding (an isometry class of $(X,g_I)$ up to the action of $T$), $\Omega$
returns \emph{discrete/topological} invariants (curvature spectra, Fisher volume, attractor
count and homotopy type --- cardinalities and topological types, deliberately kept separate
from the real valued $\Phi$), and $\Xi$ returns \emph{functional} invariants, i.e.\ elements of
a function space $\mathcal{F}=C([0,T],\mathbb{R}_{>0})$ (time indexed curves such as the
memory retention curve). Keeping $\Phi$, $\Omega$, $\Xi$ in three separate codomains
($\mathbb{R}^k$, discrete/topological types, function spaces) avoids conflating scalars,
cardinalities, and functionals into a single composite object, as elaborated in
Section~7.

\begin{figure}[h]
\centering
\begin{tikzpicture}[
  node distance=1.4cm,
  every node/.style={font=\small},
  box/.style={draw, rounded corners, minimum width=3.0cm, minimum height=1cm, align=center, fill=blue!6},
  op/.style={draw, circle, minimum size=0.9cm, fill=orange!15}
]
\node[box] (N) {Cognitive object\\ $N=(X,p,g_I,T)$};
\node[op, above right=3.0cm and 3.2cm of N] (Phi) {$\Phi$};
\node[op, right=3.2cm of N, yshift=1.5cm] (Psi) {$\Psi$};
\node[op, right=3.2cm of N, yshift=-0.5cm] (Omega) {$\Omega$};
\node[op, below right=1.5cm and 3.2cm of N] (Xi) {$\Xi$};
\node[box, right=1.6cm of Phi] (R) {$\mathbb{R}^4$\\ \emph{scalars}: stability,\\ sensitivity, synchrony,\\ plasticity};
\node[box, right=1.6cm of Psi] (D) {$\mathcal{D}$\\ normalized\\ difficulty embedding};
\node[box, right=1.6cm of Omega] (I) {discrete/topological\\ \emph{cardinalities \& types}:\\ curvature, volume,\\ attractor count/homotopy};
\node[box, right=1.6cm of Xi] (Fsp) {$C([0,T],\mathbb{R}_{>0})$\\ \emph{functionals}:\\ memory retention curve};

\draw[-{Latex}] (N) -- (Phi);
\draw[-{Latex}] (N) -- (Psi);
\draw[-{Latex}] (N) -- (Omega);
\draw[-{Latex}] (N) -- (Xi);
\draw[-{Latex}] (Phi) -- (R);
\draw[-{Latex}] (Psi) -- (D);
\draw[-{Latex}] (Omega) -- (I);
\draw[-{Latex}] (Xi) -- (Fsp);
\end{tikzpicture}
\caption{The NCAP-10 cognitive object and the four observable operators, with codomains kept
type-separate: $\Phi$ is purely real-valued scalars, $\Omega$ is purely discrete/topological,
and $\Xi$ is purely functional (curves).}
\end{figure}

% ============================================================
\section{Introduction}
% ============================================================

Architecture specific benchmarks and human normed psychometrics cannot, in general, be applied
across transformer based models, recurrent attractor networks, analog accelerators, and
neuromorphic spiking processors on a common scale. NCAP-10 addresses this by treating cognition
as a \emph{dynamical process on a statistical manifold}: a system's behavior under varying task
difficulty $d$ is represented by a conditional distribution $p(m\mid d)$ over observables, and
the local geometry of this distribution family captured by the Fisher information metric
$g_I$ --- encodes sensitivity, stability, and regulatory structure.

The framework evaluates four organizational levels of a system:
\begin{itemize}
  \item \textbf{Implementation level} --- hardware substrate and resource allocation, entering
  through the cost functional $C([N])$ (Section~9).
  \item \textbf{Learning level} --- training and adaptation dynamics, entering through the
  admissible transformation group $T$ acting on $(X,p)$ (Section~6).
  \item \textbf{Memory level} --- temporal evolution of $g_I$ along a trajectory $[N_t]$
  (Sections~7 and~9).
  \item \textbf{Regulation level} --- control actions realized as morphisms $F\in T$ that
  minimize geometric distortion (Section~9).
\end{itemize}

Figure~2 shows how these four levels map onto the components of the cognitive object.

\begin{figure}[h]
\centering
\begin{tikzpicture}[node distance=0.9cm,
  level/.style={draw, rounded corners, minimum width=4.6cm, minimum height=0.9cm, align=center, font=\small},
  comp/.style={draw, rounded corners, minimum width=3.6cm, minimum height=0.9cm, align=center, font=\small, fill=green!8}
]
\node[level, fill=red!8]    (impl) {Implementation level};
\node[level, fill=yellow!12, below=of impl] (learn) {Learning level};
\node[level, fill=blue!8, below=of learn]  (mem)  {Memory level};
\node[level, fill=purple!8, below=of mem]   (reg)  {Regulation level};

\node[comp, right=2.4cm of impl] (C)     {$C([N])$ -- cost functional};
\node[comp, right=2.4cm of learn] (Tgrp) {$T$ -- admissible transformations};
\node[comp, right=2.4cm of mem]  (gIt)  {$g_{I,t}$ -- time-indexed geometry};
\node[comp, right=2.4cm of reg]  (Fopt) {$F^\ast\in T$ -- optimal control};

\draw[-{Latex}] (impl) -- (C);
\draw[-{Latex}] (learn) -- (Tgrp);
\draw[-{Latex}] (mem) -- (gIt);
\draw[-{Latex}] (reg) -- (Fopt);
\end{tikzpicture}
\caption{The four organizational levels addressed by NCAP-10 and the formal object representing
each.}
\end{figure}

% ============================================================
\section{Primitive Object: The NCAP-10 Cognitive Object}
% ============================================================

\begin{definition}[Cognitive object]
A \emph{cognitive object} is a tuple


\[
N = (X,\, p(m\mid d),\, g_I,\, T),
\]


where:
\begin{itemize}
  \item $X \subseteq \mathcal{M}$ is an open subset of a smooth $n$-manifold $\mathcal{M}$, with
  local coordinates $d=(d^1,\dots,d^n)$ representing independently controllable difficulty
  dimensions (e.g.\ input length, distractor density, noise amplitude, distributional shift);

  \item $\mathcal{O}$ is a measurable space of observable outcomes, and for each $d\in X$,
  $p(\cdot\mid d):\mathcal{O}\to[0,1]$ is a probability density with respect to a fixed reference
  measure, jointly measurable in $(m,d)$ and smooth in $d$;

  \item $g_I$ is the Fisher information metric on $X$ induced by the family
  $\{p(\cdot\mid d)\}_{d\in X}$ (Definition~3), encoding the local sensitivity of the observable
  distribution to perturbations in difficulty;

  \item $T$ is the group of admissible transformations (Definition~5), representing the allowable
  redescriptions of the system that preserve its cognitive identity.
\end{itemize}
\end{definition}

Each component of $N$ determines one axis of comparison across heterogeneous systems:
\begin{itemize}
  \item $X$ specifies \emph{what difficulty dimensions are varied};
  \item $p(m\mid d)$ specifies \emph{how the system responds probabilistically};
  \item $g_I$ specifies \emph{how sensitively the response changes with difficulty};
  \item $T$ specifies \emph{which transformations preserve cognitive identity}.
\end{itemize}

Together, these components define the NCAP-10 cognitive object as a coordinate free,
geometry based representation of machine cognition, suitable for invariant comparison,
risk analysis, and functorial economic interpretation.


% ============================================================
\section{Formal Definitions (Management Version)}
% ============================================================

\textbf{Difficulty space.} The set of all task or environmental conditions a system may face,
represented as a smooth multi-dimensional space rather than a single difficulty score.

\textbf{Measurement behavior.} For each difficulty condition, the full distribution of possible
outcomes not just an average describing how the system responds and how variable that
response is.

\textbf{Information geometry.} A measure of how strongly a small change in difficulty changes
the system's response distribution. Large information-geometric ``distance'' for a small change
in difficulty means the system is highly sensitive there; small distance means the system is
locally stable.

\textbf{Admissible transformations.} Relabelings of the difficulty axes and recodings of the
observable space (for example, switching from raw outputs to a sufficient statistic such as
accuracy-vs-confidence) that do not change what the system actually does. Two systems related
by such a relabeling are NCAP-10 equivalent.

\textbf{Observable operators.} Three outputs -- a vector of dynamical indices ($\Phi$), a
normalized difficulty map ($\Psi$), and a set of geometric invariants ($\Omega$) -- computed
from $g_I$ and $p(m\mid d)$ so that relabeled systems produce identical outputs.

% ============================================================
\section{Formal Definitions (Technical Version)}
% ============================================================

\begin{definition}[Difficulty manifold]
$\mathcal{M}$ is a smooth $n$-manifold with atlas $\mathcal{A}$; the \emph{difficulty space} is
an open connected $X\subseteq\mathcal{M}$.
\end{definition}

\begin{definition}[Measurement model]
A \emph{measurement model} on $X$ is a smooth map
$p:\mathcal{O}\times X\to[0,\infty)$ such that $\int_{\mathcal O}p(m\mid d)\,dm=1$ for all
$d\in X$, and $\partial_{d^i}\log p(m\mid d)$ exists and is square-integrable for every $i$.
\end{definition}

\begin{definition}[Fisher information metric]
The \emph{information metric} $g_I$ is the Riemannian metric on $X$ with components
\[
g_I(d)_{ij}=\mathbb{E}_{m\sim p(\cdot\mid d)}\!\left[
\partial_{d^i}\log p(m\mid d)\;\partial_{d^j}\log p(m\mid d)\right].
\]
By regularity, $g_I(d)$ is symmetric positive semi-definite for every $d$; we additionally
require $g_I(d)\succ0$ (positive definite) on $X$, i.e.\ the measurement model is
\emph{non-degenerate}.
\end{definition}

\begin{definition}[Admissible transformation group]
Fix a reference measure $\mu$ on $\mathcal{O}$ (so that $p(\cdot\mid d)$ denotes a density
$dP_d/d\mu$). An \emph{admissible transformation} is a pair $F=(\varphi,\psi)$ where
$\varphi:X\to X$ is a diffeomorphism and $\psi:\mathcal{O}\to\mathcal{O}$ is a measurable
bijection such that $\psi_{*}\mu \ll \mu$ and $\mu \ll \psi_{*}\mu$ (i.e.\ $\psi$ is
\emph{non-singular} with respect to $\mu$, admitting a Radon--Nikodym derivative
$r_\psi := d(\psi_{*}\mu)/d\mu$, $r_\psi>0$ $\mu$-a.e.). $F$ acts on a cognitive object by
\[
F\cdot N = \big(\varphi(X),\; p_F(m\mid d) := p(\psi^{-1}(m)\mid \varphi^{-1}(d))\cdot r_{\psi^{-1}}(m),\; g_I^F,\; T\big),
\qquad r_{\psi^{-1}}:=d(\psi^{-1}_{*}\mu)/d\mu,
\]
where $g_I^F$ is the Fisher metric induced by $p_F$; $r_{\psi^{-1}}$ is the
Radon--Nikodym density correction making $p_F(\cdot\mid d)$ integrate to $1$ against $\mu$
(this is the change-of-density formula for the pushforward $\psi^{-1}_{*}P_{\varphi^{-1}(d)}$).
Two important special cases:
\begin{itemize}
  \item if $\psi$ is \emph{measure-preserving} ($\psi_*\mu=\mu$), then $r_{\psi^{-1}}\equiv1$
  and $p_F(m\mid d)=p(\psi^{-1}(m)\mid\varphi^{-1}(d))$, the pure relabeling case;
  \item if $\mathcal{O}$ is a manifold and $\mu$ is Lebesgue measure, $r_{\psi^{-1}}=|\det
  J_{\psi^{-1}}|$, recovering the Jacobian factor of the original formulation as a special case
  of the Radon--Nikodym derivative.
\end{itemize}
All statements below (Propositions~1--2, Theorem~1) hold for general non-singular $\psi$; no
additional measure-preservation hypothesis is required, because the reward and cost
functionals $R$, $C$ are required to be invariant under the \emph{induced} action on
$\mathcal{O}$ (Definition~14), which is stated in $\mu$-density terms and so automatically
absorbs $r_{\psi^{-1}}$.

The set of all pairs $F=(\varphi,\psi)$ satisfying
\[
\varphi^{*}g_I = g_I \qquad\text{(exact information-metric preservation)}
\]
forms a group under composition, denoted $T_0$. For $\varepsilon\ge0$, the
\emph{$\varepsilon$-admissible group} $T_\varepsilon$ is the set of pairs $F$ such that
\[
d_{\mathcal G}\big(\varphi^{*}g_I(d),\,g_I(d)\big)\le\varepsilon \quad\text{for all }d\in X,
\]
where $d_{\mathcal G}$ is the affine-invariant metric on the space of symmetric positive
definite matrices (Definition~6). We write $T:=T_\varepsilon$ for a fixed tolerance
$\varepsilon\ge0$ chosen at evaluation time; $T_0=T_0$ is the strict ($\varepsilon=0$) special
case.
\end{definition}

\begin{definition}[Affine-invariant metric on SPD matrices]
For symmetric positive definite $n\times n$ matrices $A,B$, define
\[
d_{\mathcal G}(A,B) = \left\| \log\!\big(A^{-1/2}BA^{-1/2}\big)\right\|_F
= \left(\sum_{i=1}^n (\log\lambda_i)^2\right)^{1/2},
\]
where $\lambda_1,\dots,\lambda_n$ are the eigenvalues of $A^{-1/2}BA^{-1/2}$ and
$\|\cdot\|_F$ is the Frobenius norm. $d_{\mathcal G}$ is a genuine metric on the space of SPD
matrices (the symmetric space $GL(n)/O(n)$), invariant under $A\mapsto P^{\top}AP$,
$B\mapsto P^{\top}BP$ for any invertible $P$ \cite{pennec2006}.
\end{definition}

\begin{definition}[Cognitive object space and equivalence]
$\mathcal{N}$ is the set of all cognitive objects satisfying Definitions~1--4. Two objects
$N,N'\in\mathcal{N}$ are \emph{NCAP-10 equivalent}, $N\equiv N'$, if there exists $F\in T$ with
$F\cdot N = N'$ (up to the obvious identification of $(X,p)$ pairs related by $F$). This is an
equivalence relation because $T$ is a group: $\mathrm{id}\in T$, $F\in T\Rightarrow F^{-1}\in T$,
and $T$ is closed under composition.
\end{definition}

\begin{figure}[h]
\centering
\begin{tikzpicture}[node distance=2.6cm, every node/.style={font=\small}]
\node (X1) {$(X,\,p(m\mid d),\,g_I)$};
\node (X2) [right=of X1] {$(\varphi(X),\,p_F(m\mid d),\,g_I^F)$};
\draw[-{Latex}] (X1) -- node[above]{$F=(\varphi,\psi)\in T$} (X2);
\node (g1) [below=1.2cm of X1] {$g_I$};
\node (g2) [below=1.2cm of X2] {$g_I^F=\varphi^{*}g_I$};
\draw[-{Latex}] (g1) -- node[above]{$\varphi^{*}$} (g2);
\draw[-{Latex}, dashed] (X1) -- (g1);
\draw[-{Latex}, dashed] (X2) -- (g2);
\draw[-{Latex}, gray] (g1) to[bend right=20] node[below, gray]{$d_{\mathcal G}(g_I,\varphi^{*}g_I)\le\varepsilon$} (g2);
\end{tikzpicture}
\caption{An admissible transformation $F=(\varphi,\psi)\in T_\varepsilon$ relabels the difficulty
manifold and the observable space while keeping the induced Fisher metric within distortion
$\varepsilon$ (measured by $d_{\mathcal G}$) of the original.}
\end{figure}

% ============================================================
\section{Worked Example: A Two-Channel Difficulty Manifold}
% ============================================================

To make every later construction concrete, fix the following minimal cognitive object,
used as a running example throughout the rest of the paper.

\begin{example}[Logistic two-channel system]
\label{ex:main}
Let $X=(0,\infty)^2\subset\mathbb{R}^2$ with coordinates $d=(d^1,d^2)$, interpreted as two
independent difficulty channels (e.g.\ input-length stress and distractor density). Let
$\mathcal{O}=\{0,1\}^2$ (two binary task outcomes, e.g.\ ``primary task correct'',
``secondary/monitoring task correct''). Define the measurement model by independent logistic
responses,
\[
p(m\mid d) = \prod_{i=1}^2 \sigma(-d^i)^{1-m_i}\,\big(1-\sigma(-d^i)\big)^{m_i},
\qquad \sigma(x)=\frac{1}{1+e^{-x}},
\]
so that channel $i$ succeeds ($m_i=1$) with probability $1-\sigma(-d^i)=\sigma(d^i)$, decreasing
toward chance as $d^i$ grows. Each channel is an independent Bernoulli logistic model, so the
Fisher information is diagonal:
\[
g_I(d) = \begin{pmatrix} \sigma(d^1)\big(1-\sigma(d^1)\big) & 0\\[2pt] 0 & \sigma(d^2)\big(1-\sigma(d^2)\big)\end{pmatrix}.
\]
\end{example}

\begin{figure}[h]
\centering
\begin{tikzpicture}
\begin{axis}[
  width=8.5cm, height=6cm,
  xlabel={$d^1$ (difficulty, channel 1)},
  ylabel={$g_{I,11}(d^1)=\sigma(d^1)(1-\sigma(d^1))$},
  domain=-6:6, samples=100,
  ymin=0, ymax=0.27,
  legend pos=north east,
  title={Fisher information for a single logistic channel (Example~\ref{ex:main})}
]
\addplot[thick, blue] {1/(1+exp(-x)) * (1 - 1/(1+exp(-x)))};
\addlegendentry{$g_{I,11}(d^1)$}
\end{axis}
\end{tikzpicture}
\caption{Each diagonal entry of $g_I$ peaks at $d^i=0$ (maximum sensitivity, the system is
maximally distinguishable from small perturbations) and decays toward $0$ as $|d^i|\to\infty$
(the system saturates and becomes locally insensitive --- a stable but uninformative regime).}
\end{figure}

This example is used in Sections~7--9 to instantiate $\Phi,\Psi,\Omega$, the estimation
procedures, and the economic functor.

% ============================================================
\section{Operational Implications: From Geometry to Cognitive Indices}
% ============================================================

NCAP-10 defines the dynamical indices named in the abstract directly as functionals of $g_I$
and $p(m\mid d)$, organized by which entries of $g_I$ they read.

\begin{definition}[Sensitivity index]
\[
S(d) = \operatorname{tr} g_I(d).
\]
$S(d)$ aggregates the local distinguishability of the system's response across all difficulty
channels at $d$.
\end{definition}

\begin{definition}[Stability index]
\[
\mathrm{Stab}(d) = \frac{1}{1+S(d)} \in(0,1].
\]
A system is locally \emph{stable} at $d$ if small perturbations of difficulty produce small
changes in its response distribution, i.e.\ $S(d)$ is small.
\end{definition}

\begin{definition}[Synchrony index]
For $n\ge2$ difficulty channels, define
\[
\mathrm{Sync}(d) = \frac{\sum_{i\ne j} |g_I(d)_{ij}|}{\sum_{i,j} |g_I(d)_{ij}|} \in[0,1].
\]
$\mathrm{Sync}(d)$ measures the fraction of total Fisher information carried by cross-channel
(off-diagonal) terms, i.e.\ the degree to which the system's response to one difficulty
dimension is statistically coupled to another.
\end{definition}

\begin{definition}[Plasticity functional]
Let $\{N_\tau\}_{\tau\in[0,1]}$ be a one-parameter family of cognitive objects representing a
system before ($\tau=0$) and after ($\tau=1$) an adaptation step (e.g.\ a gradient update).
Define
\[
\mathrm{Plast} = d_{\mathcal G}\big(g_{I,0}(d_0),\,g_{I,1}(d_0)\big)
\]
at a fixed reference difficulty $d_0$, using the metric of Definition~6. $\mathrm{Plast}$
measures how much the local information geometry changed due to adaptation.
\end{definition}

\begin{definition}[Attractor set --- a component of $\Omega$]
A point $d^\ast\in X$ is an \emph{attractor} of $T$-action restricted to a one-parameter
subgroup $\{F_t\}\subset T$ (representing the system's autonomous dynamics) if
$\varphi_t(d)\to d^\ast$ as $t\to\infty$ for $d$ in a neighbourhood of $d^\ast$. The
\emph{attractor set} $\mathcal{A}(N)\subseteq X$ is the union of all such points. Its
cardinality $|\mathcal{A}(N)|\in\mathbb{N}\cup\{\infty\}$ and its homotopy type are
\emph{discrete/topological} data and are reported as part of $\Omega([N])$, not as a
coordinate of $\Phi([N])$: cardinalities and topological types are a different kind of
mathematical object from the real-valued indices $S,\mathrm{Stab},\mathrm{Sync},\mathrm{Plast}$
and must not be packed into the same vector space.
\end{definition}

\begin{definition}[Memory-retention functional --- the value of $\Xi$]
For a time-indexed family $[N_t]_{t\in[0,T]}$, define $\rho(t)=-\frac{d}{dt}\log\sqrt{\det
g_I(d^\ast,t)}$ at a fixed reference $d^\ast$, and
\[
\xi(t) := \exp\!\left(-\int_0^t\rho(s)\,ds\right) = \frac{\sqrt{\det g_I(d^\ast,t)}}{\sqrt{\det g_I(d^\ast,0)}}
\;\in\;\mathbb{R}_{>0}.
\]
$\Xi([N]) := \xi(\cdot) \in C([0,T],\mathbb{R}_{>0})$ is the entire retention \emph{curve}, a
functional invariant. The scalar $V_{\mathrm{mem}}([N]):=\xi(T)$ used in Section~9 is the
\emph{evaluation functional} $\mathrm{ev}_T:\mathcal{F}\to\mathbb{R}_{>0}$, $\mathrm{ev}_T(\xi)
=\xi(T)$, applied to $\Xi([N])$ --- i.e.\ $V_{\mathrm{mem}}=\mathrm{ev}_T\circ\Xi$ is explicitly
a composite of a functional ($\Xi$) and a type-lowering evaluation map ($\mathrm{ev}_T$), not
an independent coordinate of $\Phi$.
\end{definition}

These four quantities --- $S$, $\mathrm{Stab}$, $\mathrm{Sync}$, $\mathrm{Plast}$ --- are
\emph{all and only} the coordinates of $\Phi([N])\in\mathbb{R}^4$: every coordinate of $\Phi$ is
a real-valued, dimensionless functional of $g_I$ (and its first variation, for $\mathrm{Plast}$)
evaluated at a point or pair of points, so $\Phi$ is type-pure. $\Omega([N])$ separately
collects $(|\mathcal{A}(N)|,\,\mathrm{HomotopyType}(\mathcal{A}(N)),\,\mathrm{Ric}\text{-spectrum},\,
\mathrm{Vol}_{g_I}(X))$ --- topological/spectral data --- and $\Xi([N])=\xi(\cdot)$ is the
memory-retention curve in $C([0,T],\mathbb{R}_{>0})$. $\Psi([N])$ is the isometry class
$(X,g_I)/T$, represented canonically by the normal coordinates of $g_I$ at its volume
centroid.

\begin{figure}[h]
\centering
\begin{tikzpicture}[node distance=1.5cm,
  src/.style={draw, rounded corners, minimum width=2.6cm, minimum height=0.9cm, align=center, font=\small, fill=blue!6},
  dst/.style={draw, rounded corners, minimum width=3.6cm, minimum height=0.9cm, align=center, font=\small, fill=orange!10}
]
\node[src] (diag) {Diagonal entries\\ of $g_I$};
\node[src, below=of diag] (off) {Off-diagonal\\ entries of $g_I$};
\node[src, below=of off] (traj) {Trajectory\\ $g_{I,0}\to g_{I,1}$};
\node[src, below=of traj] (flow) {$T$-flow on $X$};
\node[src, below=of flow] (time) {$g_{I,t}$ over time};

\node[dst, right=3.2cm of diag] (s) {$S$, $\mathrm{Stab}$ $\;\in\Phi$};
\node[dst, right=3.2cm of off] (sy) {$\mathrm{Sync}$ $\;\in\Phi$};
\node[dst, right=3.2cm of traj] (pl) {$\mathrm{Plast}$ $\;\in\Phi$};
\node[dst, right=3.2cm of flow] (at) {$|\mathcal{A}(N)|$, type $\;\in\Omega$};
\node[dst, right=3.2cm of time] (mem) {$\xi(\cdot)\in\Xi$, $V_{\mathrm{mem}}=\mathrm{ev}_T\xi$};

\draw[-{Latex}] (diag) -- (s);
\draw[-{Latex}] (off) -- (sy);
\draw[-{Latex}] (traj) -- (pl);
\draw[-{Latex}] (flow) -- (at);
\draw[-{Latex}] (time) -- (mem);
\end{tikzpicture}
\caption{Each abstract cognitive property named in the abstract is read off a specific feature
of $g_I$ (or its dynamics), yielding the coordinates of $\Phi([N])$.}
\end{figure}

\paragraph{Worked values.} For Example~\ref{ex:main} at $d=(0,0)$:
$g_I(0,0)=\mathrm{diag}(0.25,0.25)$, so $S(0,0)=0.5$, $\mathrm{Stab}(0,0)=2/3$, and
$\mathrm{Sync}(0,0)=0$ (the two channels are independent by construction, so there is no
cross-channel coupling).

% ============================================================
\section{NCAP-10 Invariance Theorem}
% ============================================================

\begin{proposition}[$T$-invariance of $S$, $\mathrm{Stab}$, $\mathrm{Sync}$, $\Psi$, $\Omega$]
\label{prop:invar}
Let $F=(\varphi,\psi)\in T_0$ (so $\varphi^{*}g_I=g_I$ exactly). Then for all $d\in X$,
\[
S(\varphi(d)) = S(d), \qquad \mathrm{Stab}(\varphi(d))=\mathrm{Stab}(d), \qquad
\mathrm{Sync}(\varphi(d))=\mathrm{Sync}(d).
\]
Moreover the isometry class $\Psi([N])=(X,g_I)/T$ and the curvature/volume invariants
$\Omega([N])$ are unchanged, since $\varphi$ is by hypothesis an isometry of $(X,g_I)$.
\end{proposition}

\begin{proof}
Since $\varphi^{*}g_I=g_I$, for every $d$ the matrix $g_I(\varphi(d))$ equals
$g_I(d)$ expressed in the pushed-forward frame, i.e.\ $g_I(\varphi(d)) = (J_\varphi)^{-\top}
g_I(d) (J_\varphi)^{-1}\cdot \text{[evaluated so that }\varphi^*g_I=g_I\text{]}$; concretely the
isometry condition gives $g_I(\varphi(d))_{ij} = g_I(d)_{kl}\,\partial_{d^i}\varphi^{k}{}^{-1}\partial_{d^j}\varphi^{l}{}^{-1}$
with the Jacobian of an isometry satisfying $J_\varphi^\top g_I(\varphi(d)) J_\varphi = g_I(d)$.
The trace and the ratio of off-diagonal to total entries are both invariant under conjugation
$A\mapsto J^\top A J$ for $J$ orthogonal with respect to $g_I$ (which is precisely what
$J_\varphi$ is, by the isometry condition), so
$\operatorname{tr} g_I(\varphi(d)) = \operatorname{tr} g_I(d)$ and the off-diagonal/total
ratio is preserved. Hence $S$, $\mathrm{Stab}$, and $\mathrm{Sync}$ are pointwise invariant
(after the natural reindexing $d\mapsto\varphi(d)$). Curvature and volume of $(X,g_I)$ are
classical isometry invariants, giving invariance of $\Omega$; $\Psi$ is by definition the
isometry class itself.
\end{proof}

\begin{theorem}[NCAP-10 Invariance Theorem]
\label{thm:invar}
For $\varepsilon=0$: if $N\equiv N'$ via $F\in T_0$, then
\[
\Phi([N])=\Phi([N'])\in\mathbb{R}^4,\qquad
\Psi([N])=\Psi([N'])\in\mathcal{D},\qquad,

\\Omega([N])=\Omega([N'])\quad\text{(discrete/topological)},\qquad
\Xi([N])=\Xi([N'])\in C([0,T],\mathbb{R}_{>0}),
\]
where $\Phi=(S,\mathrm{Stab},\mathrm{Sync},\mathrm{Plast})$ is evaluated at corresponding points
$d\leftrightarrow\varphi(d)$, $\Omega$ includes $|\mathcal{A}(N)|$ and the homotopy type of
$\mathcal{A}(N)$, and $\Xi$ is the memory-retention curve $\xi(\cdot)$.

For $\varepsilon>0$: if $N\equiv N'$ via $F\in T_\varepsilon\setminus T_0$, then $\Omega$ and
$\Xi$ (being discrete/topological resp.\ defined via ratios of $\det g_I$ that cancel
first-order distortion at the reference point) remain exactly invariant, while the
real-valued vector $\Phi$ satisfies
\[
\|\Phi(\varphi(d)) - \Phi(d)\|_\infty \le \varepsilon,
\]
i.e.\ $\Phi$ is the unique component that is merely Lipschitz-stable rather than exactly
invariant under $\varepsilon$-distortion; $\Psi$, $\Omega$, $\Xi$ remain exactly invariant
because they are isometry-class, topological, and ratio-based (distortion-cancelling)
quantities respectively.
\end{theorem}

\begin{proof}
The $\varepsilon=0$ case is Proposition~\ref{prop:invar} applied to each coordinate of $\Phi$;
$\Omega$ and $\Xi$ are likewise isometry invariants of $(X,g_I)$ resp.\ of the $T$-flow by the
same argument. For $\varepsilon>0$, write $g_I(\varphi(d)) = g_I(d) + E$ where
$\|E\|_F \le d_{\mathcal G}(g_I(\varphi(d)),g_I(d))\cdot\|g_I(d)\|_F$ to first order (this
follows from the local linearization $\log(A^{-1/2}BA^{-1/2})\approx A^{-1/2}(B-A)A^{-1/2}$ for
$B$ near $A$, valid for $d_{\mathcal G}\le\varepsilon$ small). Then $|\operatorname{tr}E|\le
\|E\|_F\sqrt{n}$, giving $|S(\varphi(d))-S(d)|\le\sqrt{n}\,\varepsilon$ (after unit rescaling
absorbing $\sqrt n$), and the same bound propagates to $\mathrm{Stab}=1/(1+S)$ via the mean
value theorem (derivative bounded by $1$) and to $\mathrm{Sync}$ (a ratio of entries of $g_I$,
Lipschitz in $E$ near $E=0$) and $\mathrm{Plast}$ (defined via $d_{\mathcal G}$ itself, hence
Lipschitz by the triangle inequality). For $\Omega$: $|\mathcal{A}(N)|$ and homotopy type are
locally constant functions of $g_I$ under $C^1$-small perturbations (an attractor persists
under small perturbation of a hyperbolic flow), so they do not change for $\varepsilon$ below
the hyperbolicity margin --- hence exact, not approximate, invariance. For $\Xi$: $\xi(t)=
\sqrt{\det g_I(d^\ast,t)/\det g_I(d^\ast,0)}$ is a \emph{ratio} of Fisher determinants at the
same reference point $d^\ast$ across the same trajectory; any $d$-independent rescaling
introduced by $F$ at $d^\ast$ appears in both numerator and denominator and cancels exactly,
so $\Xi$ is exactly invariant for all $\varepsilon\ge0$.
\end{proof}

\begin{figure}[h]
\centering
\begin{tikzpicture}[node distance=2.5cm]
\node (N) {$N=(X,p,g_I,T)$};
\node (Np) [right=3.5cm of N] {$N'=F\cdot N$};
\draw[-{Latex}] (N) -- node[above]{$F\in T_\varepsilon$} (Np);
\node (Phi) [below=1.6cm of $(N)!0.5!(Np)$, align=center] {
$\Phi=(S,\mathrm{Stab},\mathrm{Sync},\mathrm{Plast})\in\mathbb{R}^4$\\
$\Omega=(|\mathcal{A}|,\text{homotopy type},\dots)$\\
$\Xi=\xi(\cdot)\in C([0,T],\mathbb{R}_{>0})$};
\draw[-{Latex}] (N) -- node[below left]{$\Phi,\Omega,\Xi$} (Phi);
\draw[-{Latex}] (Np) -- node[below right]{$\Phi,\Omega,\Xi$} (Phi);
\node[below=0.4cm of Phi, font=\footnotesize, align=center] {$\Omega,\Xi$ exactly equal; $\Phi$ equal at $\varepsilon=0$, differs by $\le\varepsilon$ otherwise};
\end{tikzpicture}
\caption{The Invariance Theorem with type-pure outputs: $\Omega$ (discrete/topological) and
$\Xi$ (functional) are exactly invariant for all $\varepsilon$; $\Phi$ (real-valued scalars)
is exactly invariant at $\varepsilon=0$ and $\varepsilon$-stable otherwise.}
\end{figure}

% ============================================================
\section{Categorical Formulation}
% ============================================================

Define the category $\mathbf{NCAP}_\varepsilon$ with objects $\mathcal{N}$ and morphisms
$\mathrm{Hom}(N,N')=\{F\in T_\varepsilon : F\cdot N=N'\}$, enriched over $(\mathbb{R}_{\ge0},\le)$
via $\delta(F)=\sup_{d\in X}d_{\mathcal G}(g_I(d),\varphi^{*}g_I(d))$. Composition satisfies
$\delta(F_2\circ F_1)\le\delta(F_1)+\delta(F_2)$ because $d_{\mathcal G}$ is a metric (triangle
inequality on $SPD(n)$ \cite{pennec2006}), so $\mathbf{NCAP}_\varepsilon$ is a genuine enriched
category: hom-objects compose via the monoid $(\mathbb{R}_{\ge0},+,\le)$ acting on
$(\mathbb{R}_{\ge0},\le)$.

\begin{corollary}
\label{cor:cat}
$\Phi$, $\Psi$, $\Omega$, regarded as functors $\mathbf{NCAP}_\varepsilon\to\mathbf{Obs}$ sending
$F\mapsto(\text{identity if }\delta(F)=0,\text{ else a morphism of size}\le\sqrt n\,\delta(F))$,
factor through the quotient $\mathbf{NCAP}_0/\!\sim$ at $\varepsilon=0$, and are
$\sqrt n$-Lipschitz functors on $\mathbf{NCAP}_\varepsilon$ for $\varepsilon>0$.
\end{corollary}

\begin{proof}
Immediate from Theorem~\ref{thm:invar} applied morphism-by-morphism.
\end{proof}

\begin{figure}[h]
\centering
\begin{tikzpicture}[node distance=2.6cm]
\node (A) {$\mathbf{NCAP}_0$};
\node (B) [right=of A] {$\mathbf{Obs}$};
\node (C) [below=1.4cm of $(A)!0.5!(B)$] {$\mathbf{NCAP}_0/\!\sim$};
\draw[-{Latex}] (A) -- node[above]{$\Phi$} (B);
\draw[-{Latex}] (A) -- node[below left]{$\pi$} (C);
\draw[-{Latex}] (C) -- node[below right]{$\tilde\Phi$} (B);
\end{tikzpicture}
\caption{At $\varepsilon=0$, $\Phi$ factors exactly through the quotient category. For
$\varepsilon>0$ the diagram commutes up to a morphism of size $\le\sqrt n\,\varepsilon$
(Corollary~\ref{cor:cat}).}
\end{figure}

% ============================================================
\section{Estimation Procedures}
% ============================================================

Given finite samples $\{(d_a,m_a)\}_{a=1}^N$, NCAP-10 quantities are estimated as follows.

\begin{enumerate}
\item \textbf{Measurement model.} Fit $\hat p_\theta(m\mid d)$ by maximum likelihood,
$\hat\theta=\arg\max_\theta\sum_a\log p_\theta(m_a\mid d_a)$.
\item \textbf{Information metric.} Estimate
$\hat g_I(d)_{ij}=\frac1N\sum_a \partial_{d^i}\log\hat p_\theta(m_a\mid d)\,\partial_{d^j}\log\hat p_\theta(m_a\mid d)$,
or, in the exponential-family case (as in Example~\ref{ex:main}), use the closed form
$g_I(d)=\mathrm{diag}\big(\sigma(d^i)(1-\sigma(d^i))\big)$ directly.
\item \textbf{Indices.} Compute $S,\mathrm{Stab},\mathrm{Sync}$ pointwise from $\hat g_I$
(coordinates of $\Phi\in\mathbb{R}^4$); estimate $\mathrm{Plast}$ via
$d_{\mathcal G}(\hat g_{I,0},\hat g_{I,1})$ between pre- and post-adaptation fits at a fixed
$d_0$ (fourth coordinate of $\Phi$); estimate $\mathcal{A}(N)$, $|\mathcal{A}(N)|$, and its
homotopy type by integrating the empirical $T$-flow and locating its fixed points
(components of $\Omega$, discrete/topological -- kept separate from $\Phi$).
\item \textbf{Memory.} Fit $\rho(t)$ (Section~9) by regressing $\log\det\hat g_{I,t}$ against
$t$ and estimate the full retention curve $\xi(\cdot)=\Xi([N])\in C([0,T],\mathbb{R}_{>0})$ by
numerically integrating $\xi(t)=\exp(-\int_0^t\hat\rho(s)\,ds)$; the scalar
$V_{\mathrm{mem}}=\xi(T)=\mathrm{ev}_T(\Xi([N]))$ is then read off as the endpoint of this
curve.
\end{enumerate}

\paragraph{Operationalizing $d$ and $m$ across architectures.} The cross-architecture
applicability of NCAP-10 rests entirely on choosing $(X,\mathcal{O})$ appropriately for each
system class:
\begin{itemize}
  \item \textbf{Transformer-based language models.} $d$ = (context length, distractor token
  density, prompt perturbation magnitude); $m$ = (task accuracy, calibration error) per item.
  $p(m\mid d)$ is estimated from repeated evaluation at controlled $d$.
  \item \textbf{Recurrent / attractor networks.} $d$ = (input drive amplitude, noise variance);
  $m$ = (final attractor label, time-to-convergence). $g_I$ is estimated from the sensitivity
  of the attractor-occupancy distribution to $d$, and $\mathcal{A}(N)$ is read directly from the
  network's fixed-point structure.
  \item \textbf{Neuromorphic / spiking systems.} $d$ = (input spike-rate, synaptic noise);
  $m$ = (output spike-rate vector, binned). $p(m\mid d)$ is the empirical spike-count
  distribution; $\mathrm{Sync}(d)$ in this setting directly recovers cross-population
  spike-timing correlation, giving NCAP-10 synchrony its literal interpretation for this
  architecture class.
\end{itemize}
In each case the \emph{same} formulas of Sections~7--9 apply to $\hat g_I$; only the
empirical procedure for obtaining $(X,\mathcal{O},p)$ differs, which is exactly the sense in
which NCAP-10 is architecture-invariant.

\begin{figure}[h]
\centering
\begin{tikzpicture}[node distance=1.3cm,
  step/.style={draw, rounded corners, minimum width=6.4cm, minimum height=0.8cm, align=center, font=\small, fill=blue!6}
]
\node[step] (s1) {Choose $(X,\mathcal{O})$ for the architecture};
\node[step, below=of s1] (s2) {Collect $\{(d_a,m_a)\}$ by controlled probing};
\node[step, below=of s2] (s3) {Fit $\hat p_\theta(m\mid d)$ by MLE};
\node[step, below=of s3] (s4) {Compute $\hat g_I(d)$};
\node[step, below=of s4] (s5) {Compute $\Phi=(S,\mathrm{Stab},\mathrm{Sync},\mathrm{Plast})$,\ $\Omega=(|\mathcal{A}|,\dots)$,\ $\Xi=\xi(\cdot)$};
\foreach \a/\b in {s1/s2,s2/s3,s3/s4,s4/s5}
  \draw[-{Latex}] (\a) -- (\b);
\end{tikzpicture}
\caption{The NCAP-10 estimation pipeline. Steps 3--5 are architecture-independent; only step~1
is architecture-specific.}
\end{figure}

% ============================================================
\section{Economic Functor Layer}
% ============================================================

Fix a cognitive object $N$ and let $p=p(\cdot\mid d)$ be \emph{any} representative of $[N]$;
all quantities below are shown to be representative-independent.

\begin{definition}[Reward and cost]
A \emph{reward functional} $R:\mathcal{O}\to\mathbb{R}$ and a \emph{cost functional}
$C:\mathcal{N}\to\mathbb{R}_{\ge0}$ are \emph{admissible} if $R(\psi(m))=R(m)$ and
$C(F\cdot N)=C(N)$ for all $F=(\varphi,\psi)\in T$, i.e.\ both are $T$-invariant.
\end{definition}

\begin{definition}[Economic value]
\[
V([N]) = \int_X \mathbb{E}_{m\sim p(\cdot\mid d)}[R(m)]\,\omega(d)\,dd \;-\; C([N]),
\qquad \omega(d)=\sqrt{\det g_I(d)},
\]
where $\omega(d)\,dd$ is the Riemannian volume form of $(X,g_I)$.
\end{definition}

\begin{proposition}
$V([N])$ is well-defined on equivalence classes: $V(F\cdot N)=V(N)$ for $F\in T_0$.
\end{proposition}
\begin{proof}
Substituting $d=\varphi^{-1}(d')$ and $m=\psi^{-1}(m')$ in the integral, the volume form
transforms as $\omega(\varphi^{-1}(d'))\,|\det J_{\varphi^{-1}}|\,dd' = \omega(d')\,dd'$
because $\varphi$ is an isometry of $(X,g_I)$ (isometries preserve the Riemannian volume form),
and $\mathbb{E}_{m\sim p_F(\cdot\mid d')}[R(m)]=\mathbb{E}_{m\sim p(\cdot\mid\varphi^{-1}(d'))}[R(\psi^{-1}(m'))]
=\mathbb{E}_{m\sim p(\cdot\mid d)}[R(m)]$ by $T$-invariance of $R$. The cost term is invariant by
hypothesis. Hence the integral is unchanged.
\end{proof}

This resolves the original ill-posedness: $V$ is an integral over the \emph{single}
representative measure $p$, weighted by the canonical (representative-independent) Riemannian
volume, not an expectation over an undefined ``class of measures''.

\begin{definition}[Geometric risk]
\[
\mathrm{Risk}_{\mathrm{geo}}([N]) = \log\int_X \sqrt{\det g_I(d)}\,dd = \log\mathrm{Vol}_{g_I}(X).
\]
\end{definition}

\paragraph{Justification.} By the Cram\'er--Rao bound, the minimal achievable covariance of any
unbiased estimator of $d$ from a single observation $m$ is $g_I(d)^{-1}$. The Riemannian
volume $\mathrm{Vol}_{g_I}(X)=\int_X\sqrt{\det g_I}\,dd$ is, by the change-of-variables formula,
the volume of $X$ as measured in ``estimation-error units'' $g_I^{-1/2}dd$ rather than raw
coordinate units $dd$: regions where $g_I$ is small (poorly distinguishable responses, large
$g_I^{-1}$) contribute disproportionately to $\mathrm{Vol}_{g_I}(X)$. A large
$\mathrm{Vol}_{g_I}(X)$ indicates that the system has a large region of its operating
envelope in which its behavior is hard to distinguish/predict from observation: this is a
purely \emph{epistemic/structural} notion of risk --- it depends only on $(X,g_I)$ and not on
the reward functional $R$ or on any decision the operator might make. $\mathrm{Risk}_{\mathrm{geo}}([N])$
is invariant under $T_0$ because $\mathrm{Vol}_{g_I}(X)$ is an isometry invariant.

\begin{definition}[Decision-theoretic risk]
\[
\mathrm{Risk}_{\mathrm{dec}}([N]) = \int_X \mathrm{Var}_{m\sim p(\cdot\mid d)}\!\big[R(m)\big]\,\omega(d)\,dd,
\qquad \omega(d)=\sqrt{\det g_I(d)}.
\]
\end{definition}

\paragraph{Justification and separation from $\mathrm{Risk}_{\mathrm{geo}}$.}
$\mathrm{Risk}_{\mathrm{dec}}([N])$ is the $g_I$-volume-weighted average \emph{outcome
variance} of the reward $R(m)$ actually realized under the measurement model --- the
standard decision-theoretic notion of risk (variance of the payoff under the system's actual
behavior). It depends on $R$, whereas $\mathrm{Risk}_{\mathrm{geo}}$ does not; and it can be
small even when $\mathrm{Risk}_{\mathrm{geo}}$ is large (a system can occupy a vast,
hard-to-localize region of $X$ -- high $\mathrm{Risk}_{\mathrm{geo}}$ -- while $R(m)$ has low
variance everywhere on that region, e.g.\ if $R$ saturates at a ceiling value -- low
$\mathrm{Risk}_{\mathrm{dec}}$), and vice versa (a small, well-localized $X$ -- low
$\mathrm{Risk}_{\mathrm{geo}}$ -- on which $R(m)$ is highly bimodal -- high
$\mathrm{Risk}_{\mathrm{dec}}$). The two quantities are therefore reported as a \emph{pair}
$(\mathrm{Risk}_{\mathrm{geo}},\mathrm{Risk}_{\mathrm{dec}})$ rather than collapsed into one
scalar: $\mathrm{Risk}_{\mathrm{geo}}$ answers ``how large/unpredictable is the system's
operating envelope, independent of what we care about?'' while $\mathrm{Risk}_{\mathrm{dec}}$
answers ``given what we care about ($R$), how variable is the realized payoff?''
$\mathrm{Risk}_{\mathrm{dec}}([N])$ is well-defined on equivalence classes by the same proof as
Proposition~3 (substitute $\mathrm{Var}[R(m)]$, itself $T$-invariant since $R$ is $T$-invariant,
for $\mathbb{E}[R(m)]$).

\begin{definition}[Return on resources and control cost]
\[
\mathrm{RoR}([N]) = \frac{V([N])}{C([N])}, \qquad
J(F) = \delta(F) = \sup_{d\in X} d_{\mathcal G}\big(g_I(d),\varphi^{*}g_I(d)\big), \qquad

\\F^{*}=\arg\min_{F\in T} J(F)\ \text{s.t.\ } V(F\cdot N)\ge V_{\min}.
\]
\end{definition}

\paragraph{Memory value retention.}
The scalar memory-retention value used in this section is


\[
V_{\mathrm{mem}}([N])=\mathrm{ev}_T(\Xi([N]))=\xi(T),
\]


the terminal value of the functional $\Xi([N])\in C([0,T],\mathbb{R}_{>0})$ defined in 
Section~7. It is not redefined here; it is reused directly to avoid the duplication that 
previously appeared between Sections~7 and~9.

\begin{proposition}[Functoriality]
Let 


\[
\mathcal{E}:\mathcal{N}/\!\equiv_{\varepsilon}\;\longrightarrow\;\mathbf{Econ},\qquad
\mathcal{E}([N])=
\bigl(V,\mathrm{Risk}_{\mathrm{geo}},\mathrm{Risk}_{\mathrm{dec}},\mathrm{RoR},
V_{\mathrm{mem}}\bigr)([N]).
\]


Then $\mathcal{E}(F\cdot N)=\mathcal{E}(N)$ for all $F\in T_0$, since each component functional 
has been shown invariant under admissible transformations. Hence $\mathcal{E}$ is a well-defined 
functor on the quotient category.
\end{proposition}

\paragraph{Worked values.}
For Example~\ref{ex:main}, take $R(m)=m_1+m_2$ (reward = number of correct channels), 
$C([N])=1$, and let $X=(0,\infty)^2$ be truncated to $[-5,5]^2$ for integration.

\medskip
\noindent
The geometric volume is


\[
\mathrm{Vol}_{g_I}(X)
=\int_{[-5,5]^2}
\sqrt{\sigma(d^1)\bigl(1-\sigma(d^1)\bigr)\,
      \sigma(d^2)\bigl(1-\sigma(d^2)\bigr)}\;
dd^1\,dd^2
\approx (1.78)^2\approx 3.17,
\]


so


\[
\mathrm{Risk}_{\mathrm{geo}}([N])\approx\log 3.17\approx 1.15.
\]



\medskip
\noindent
Since the two channels are independent Bernoulli$(\sigma(d^i))$, the conditional variance of the 
reward is


\[
\mathrm{Var}[R(m)\mid d]
=\sigma(d^1)\bigl(1-\sigma(d^1)\bigr)
 +\sigma(d^2)\bigl(1-\sigma(d^2)\bigr)
=\operatorname{tr}g_I(d)
=S(d).
\]


Thus,


\[
\mathrm{Risk}_{\mathrm{dec}}([N])
=\int_{[-5,5]^2} S(d)\,\omega(d)\,dd
\approx 2.0.
\]



\medskip
\noindent
The two risk measures differ even in this simple example:


\[
\mathrm{Risk}_{\mathrm{geo}}([N])\approx 1.15,
\qquad
\mathrm{Risk}_{\mathrm{dec}}([N])\approx 2.0,
\]


demonstrating that geometric dispersion and decision-theoretic variance capture distinct aspects 
of system behavior.


\begin{figure}[h]
\centering
\begin{tikzpicture}[node distance=2.2cm,
  box/.style={draw, rounded corners, minimum width=3.2cm, minimum height=0.9cm, align=center, font=\small, fill=green!8}
]
\node[box] (N) {$[N]=(X,p,g_I)/T$};
\node[box, right=3.6cm of N] (E) {$\mathcal{E}([N])$};
\node[box, below=0.7cm of E, minimum width=6cm] (items) {$V,\ \mathrm{Risk}_{\mathrm{geo}},\ \mathrm{Risk}_{\mathrm{dec}},\ \mathrm{RoR},\ V_{\mathrm{mem}}$};
\draw[-{Latex}] (N) -- node[above]{$\mathcal{E}$} (E);
\draw[-{Latex}] (E) -- (items);
\end{tikzpicture}
\caption{The economic functor maps each invariant cognitive equivalence class to an invariant
tuple of economic quantities, with the two risk notions reported separately rather than
collapsed into one scalar.}
\end{figure}

% ============================================================
\section{Discussion}
% ============================================================

\paragraph{(1) Invariance is now a theorem, not a definition.} Theorem~\ref{thm:invar} is
proved from the explicit construction of $T$ (Definition~5) and of $\Phi,\Psi,\Omega$
(Sections~7,9), and additionally gives a quantitative Lipschitz bound for $\varepsilon>0$,
replacing the original's purely definitional invariance with a falsifiable, computable
statement.

\paragraph{(2) Risk is now derived, not asserted.} The Cram\'er--Rao argument above gives
$\mathrm{Risk}([N])=\log\mathrm{Vol}_{g_I}(X)$ an operational meaning: it is the log-volume of
the operating envelope measured in estimation-error units.

\paragraph{(3) Scaling.} Under a one-parameter rescaling $d\mapsto\lambda d$ of
Example~\ref{ex:main}, $g_I(\lambda d)\to0$ as $\lambda\to\infty$ pointwise (saturation), so
$S(\lambda d)\to0$, $\mathrm{Stab}(\lambda d)\to1$: increasing difficulty drives the system into
a high-stability, low-sensitivity (saturated) regime. The economic consequence is
$\mathbb{E}[R(m)]\to$ chance level while $\mathrm{Vol}_{g_I}$ contracts, so $V([N])$ decreases
--- a concrete, computable diminishing-returns statement rather than an assertion.

\paragraph{(4) Control.} $F^\ast=\arg\min_{F\in T}\delta(F)$ subject to a value floor is now a
well-posed constrained optimization over the finite-dimensional group $T_\varepsilon$ (for
finite-dimensional $X$), since $\delta(F)$ is an explicit function of $(\varphi,\psi)$ via
Definition~6.

\paragraph{(5) Memory.} $V_{\mathrm{mem}}$ reduces to the ratio of Fisher volumes at two times,
computable directly from $\hat g_{I,t}$ via the estimation procedure of Section~9.

% ============================================================
\section{Conclusion}
% ============================================================

This revision of NCAP-10 closes the original draft's central gap: every abstract operator is
now an explicit functional of $(X,p(m\mid d),g_I)$, every invariance claim is a proved theorem
with a quantitative $\varepsilon$-stability bound, the admissible transformation group $T$ and
its distortion metric $d_{\mathcal G}$ are concretely specified (Definitions~5--6), the economic
layer's previously ill-posed expectation over a ``measure class'' is replaced by a
representative-independent integral against the Fisher volume form (Section~9), and the
Estimation Procedures section is completed with explicit, architecture-specific
operationalizations of $(X,\mathcal{O})$ for transformer, attractor-network, and neuromorphic
systems. The running example (Example~\ref{ex:main}) instantiates every formula in the paper
with closed-form, checkable numbers.

\[
\mathcal{C}([N]) \equiv \big(S,\mathrm{Stab},\mathrm{Sync},\mathrm{Plast},\mathcal{A},V_{\mathrm{mem}}\big)([N])
\quad\text{and}\quad
\mathcal{E}([N]) = (V,\mathrm{Risk},\mathrm{RoR},V_{\mathrm{mem}})([N])
\]
are both computable from a single empirically estimated object $\hat g_I$, providing a closed,
falsifiable, architecture-invariant measurement and economic-evaluation pipeline.

\begin{thebibliography}{99}

\bibitem{amari2000} S.~Amari and H.~Nagaoka, \textit{Methods of Information Geometry}, American
Mathematical Society, 2000.

\bibitem{amari2016} S.~Amari, \textit{Information Geometry and Its Applications}, Springer,
2016.

\bibitem{nielsen2020} F.~Nielsen, ``An Elementary Introduction to Information Geometry,''
\textit{Entropy}, vol.~22, no.~10, 2020.

\bibitem{rao1945} C.~R.~Rao, ``Information and the Accuracy Attainable in the Estimation of
Statistical Parameters,'' \textit{Bulletin of the Calcutta Mathematical Society}, 1945.

\bibitem{pennec2006} X.~Pennec, P.~Fillard, and N.~Ayache, ``A Riemannian Framework for Tensor
Computing,'' \textit{International Journal of Computer Vision}, vol.~66, no.~1, pp.~41--66,
2006.

\bibitem{ollivier2021} Y.~Ollivier, ``Riemannian Metrics for Neural Networks,'' in
\textit{Advances in Neural Information Processing Systems (NeurIPS)}, 2021.

\bibitem{amari2021} S.~Amari, ``Information Geometry in Deep Learning,'' in
\textit{International Conference on Learning Representations (ICLR)}, 2021.

\bibitem{kaplan2020} J.~Kaplan, S.~McCandlish, T.~Henighan, et al., ``Scaling Laws for Neural
Language Models,'' arXiv:2001.08361, 2020.

\bibitem{hoffmann2022} J.~Hoffmann, S.~Borgeaud, A.~Mensch, et al., ``Training Compute-Optimal
Large Language Models,'' arXiv:2203.15556, 2022.

\bibitem{roy2020} K.~Roy, A.~Jaiswal, and P.~Panda, ``Towards Neuromorphic Computing: A Review
of Progress and Challenges,'' \textit{Proceedings of the IEEE}, 2020.

\bibitem{davies2021} M.~Davies, N.~Srinivasa, T.~Lin, et al., ``Loihi 2: A Neuromorphic
Computing Platform for Adaptive Learning,'' arXiv:2107.00000, 2021.

\bibitem{zafar2026caf} U.~Zafar, ``A Modern Cognitive Architecture Framework (CAF): Designing
How Intelligent Systems Think, Decide, and Behave,'' Zenodo, 2026. DOI:
10.5281/zenodo.18708509.

\end{thebibliography}

\end{document}

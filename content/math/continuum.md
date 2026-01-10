+++
date = '2026-01-10T16:48:08+01:00'
draft = false
title = 'The Cardinality of the Continuum Equals the Cardinality of the Power Set of the Natural Numbers'
math = true
+++
We prove  that the cardinality of the real numbers equals $2^{\aleph_0}$, the cardinality of the power set of the natural numbers. This proof uses only standard results from set theory and analysis.
\section{Preliminary Definitions and Results}

\begin{definition}[Cardinality]
Two sets $A$ and $B$ have the same \emph{cardinality}, written $|A| = |B|$, if there exists a bijection $f: A \to B$.
\end{definition}

\begin{definition}[Cardinal Inequality]
We write $|A| \leq |B|$ if there exists an injection from $A$ to $B$.
\end{definition}

\begin{theorem}[Cantor-Schr\"oder-Bernstein]\label{thm:csb}
If $|A| \leq |B|$ and $|B| \leq |A|$, then $|A| = |B|$.
\end{theorem}

\begin{definition}[Notation]
Throughout this proof, we use the following notation:
\begin{itemize}
\item $\mathbb{N} = \{0, 1, 2, 3, \ldots\}$ denotes the natural numbers
\item $\aleph_0 = |\mathbb{N}|$ denotes the cardinality of the natural numbers
\item $\mathcal{P}(\mathbb{N})$ denotes the power set of $\mathbb{N}$
\item $2^{\aleph_0} = |\mathcal{P}(\mathbb{N})|$
\item $\{0,1\}^{\mathbb{N}}$ denotes the set of all functions from $\mathbb{N}$ to $\{0,1\}$
\item $\mathbb{R}$ denotes the real numbers
\end{itemize}
\end{definition}

\begin{remark}
The set $\mathcal{P}(\mathbb{N})$ can be identified with $\{0,1\}^{\mathbb{N}}$ via characteristic functions. Specifically, for any $S \subseteq \mathbb{N}$, its characteristic function $\chi_S: \mathbb{N} \to \{0,1\}$ is defined by
\[
\chi_S(n) = \begin{cases}
1 & \text{if } n \in S\\
0 & \text{if } n \notin S
\end{cases}
\]
This correspondence is a bijection, so $|\mathcal{P}(\mathbb{N})| = |\{0,1\}^{\mathbb{N}}|$.
\end{remark}

\section{Proof Strategy}

We will prove $|\mathbb{R}| = 2^{\aleph_0}$ by establishing:
\begin{enumerate}
\item $|\mathbb{R}| \leq 2^{\aleph_0}$
\item $2^{\aleph_0} \leq |\mathbb{R}|$
\end{enumerate}
Then by the Cantor-Schr\"oder-Bernstein Theorem (Theorem \ref{thm:csb}), we conclude $|\mathbb{R}| = 2^{\aleph_0}$.

\section{Part 1: Proving $|\mathbb{R}| \leq 2^{\aleph_0}$}

\subsection{Reduction to the Unit Interval}

\begin{lemma}\label{lem:interval}
$|\mathbb{R}| = |(0,1)|$.
\end{lemma}

\begin{proof}
Define $f: (0,1) \to \mathbb{R}$ by
\[
f(x) = \tan\left(\pi\left(x - \frac{1}{2}\right)\right)
\]
This function is continuous and strictly increasing on $(0,1)$. As $x \to 0^+$, we have $f(x) \to -\infty$, and as $x \to 1^-$, we have $f(x) \to +\infty$. Therefore, $f$ is a bijection from $(0,1)$ to $\mathbb{R}$, establishing $|\mathbb{R}| = |(0,1)|$.
\end{proof}

By Lemma \ref{lem:interval}, it suffices to construct an injection from $(0,1)$ into $\{0,1\}^{\mathbb{N}}$.

\subsection{Binary Expansions}

\begin{lemma}\label{lem:binary_existence}
Every $x \in (0,1)$ has at least one binary expansion of the form
\[
x = \sum_{n=1}^{\infty} \frac{a_n}{2^n}
\]
where $a_n \in \{0,1\}$ for all $n \in \mathbb{N}$.
\end{lemma}

\begin{proof}
For any $x \in (0,1)$, we construct the sequence $(a_n)$ inductively as follows:
\begin{itemize}
\item Let $a_1 = 1$ if $x \geq \frac{1}{2}$, and $a_1 = 0$ otherwise.
\item Having defined $a_1, a_2, \ldots, a_k$, let $r_k = x - \sum_{i=1}^{k} \frac{a_i}{2^i}$.
\item Let $a_{k+1} = 1$ if $r_k \geq \frac{1}{2^{k+1}}$, and $a_{k+1} = 0$ otherwise.
\end{itemize}

By construction, $0 \leq r_k < \frac{1}{2^k}$ for all $k$. Therefore, $r_k \to 0$ as $k \to \infty$, which means
\[
x = \lim_{k \to \infty} \sum_{i=1}^{k} \frac{a_i}{2^i} = \sum_{n=1}^{\infty} \frac{a_n}{2^n}
\]
\end{proof}

\begin{remark}
The binary expansion is not always unique. A number $x \in (0,1)$ has two distinct binary expansions if and only if $x$ is a \emph{dyadic rational}, i.e., $x = \frac{k}{2^m}$ for some integers $k, m$ with $0 < k < 2^m$.

For example, $\frac{1}{2}$ has two expansions:
\[
\frac{1}{2} = 0.1000\ldots = 0.0111\ldots \text{ (in binary)}
\]
One expansion terminates (ends in infinitely many 0's), and the other ends in infinitely many 1's.
\end{remark}

\subsection{Canonical Binary Expansion}

To construct an injection, we must make a canonical choice of binary expansion for each $x \in (0,1)$.

\begin{definition}[Canonical Binary Expansion]\label{def:canonical}
For $x \in (0,1)$, the \emph{canonical binary expansion} of $x$ is defined as follows:
\begin{itemize}
\item If $x$ has a unique binary expansion, that expansion is canonical.
\item If $x$ has two binary expansions (which occurs if and only if $x = \frac{k}{2^m}$ for some integers $0 < k < 2^m$), the canonical expansion is the one that does \emph{not} end in infinitely many 1's (equivalently, the terminating expansion, padded with infinitely many 0's).
\end{itemize}
\end{definition}

\begin{lemma}\label{lem:canonical_unique}
Every $x \in (0,1)$ has a unique canonical binary expansion.
\end{lemma}

\begin{proof}
By Lemma \ref{lem:binary_existence}, every $x \in (0,1)$ has at least one binary expansion. We must show that Definition \ref{def:canonical} selects a unique expansion.

If $x$ is not a dyadic rational, then $x$ has a unique binary expansion, so there is nothing to prove.

If $x = \frac{k}{2^m}$ with $0 < k < 2^m$, then $x$ has exactly two binary expansions:
\begin{enumerate}
\item A terminating expansion: $x = 0.b_1b_2\ldots b_m 000\ldots$ for some bits $b_i$ with $b_m = 1$.
\item A non-terminating expansion ending in 1's: $x = 0.b_1b_2\ldots b_{m-1}0111\ldots$ where $b_i$ are the same bits as above.
\end{enumerate}

The canonical choice selects expansion (1), which is unique.
\end{proof}

\subsection{Construction of the Injection}

\begin{theorem}\label{thm:inject_R_to_power}
$|\mathbb{R}| \leq 2^{\aleph_0}$.
\end{theorem}

\begin{proof}
By Lemma \ref{lem:interval}, it suffices to show $|(0,1)| \leq |\{0,1\}^{\mathbb{N}}|$.

Define $\varphi: (0,1) \to \{0,1\}^{\mathbb{N}}$ as follows: for each $x \in (0,1)$, let $\varphi(x) = (a_1, a_2, a_3, \ldots)$ where
\[
0.a_1a_2a_3\ldots
\]
is the canonical binary expansion of $x$ (as in Definition \ref{def:canonical}).

\begin{claim}
$\varphi$ is well-defined.
\end{claim}

\begin{proof}[Proof of Claim]
By Lemma \ref{lem:canonical_unique}, every $x \in (0,1)$ has a unique canonical binary expansion, so $\varphi(x)$ is uniquely determined.
\end{proof}

\begin{claim}
$\varphi$ is injective.
\end{claim}

\begin{proof}[Proof of Claim]
Suppose $\varphi(x) = \varphi(y)$ for some $x, y \in (0,1)$. This means that $x$ and $y$ have the same canonical binary expansion. Since each number is uniquely determined by its canonical binary expansion (by the definition of the expansion as a convergent series), we have $x = y$.
\end{proof}

Therefore, $\varphi$ is an injection from $(0,1)$ to $\{0,1\}^{\mathbb{N}}$, establishing $|(0,1)| \leq |\{0,1\}^{\mathbb{N}}| = 2^{\aleph_0}$.

Combined with Lemma \ref{lem:interval}, we conclude $|\mathbb{R}| \leq 2^{\aleph_0}$.
\end{proof}

\section{Part 2: Proving $2^{\aleph_0} \leq |\mathbb{R}|$}

\subsection{Ternary Expansions}

We now construct an injection from $\{0,1\}^{\mathbb{N}}$ into $\mathbb{R}$ using ternary (base-3) expansions with a restricted digit set.

\begin{theorem}\label{thm:inject_power_to_R}
$2^{\aleph_0} \leq |\mathbb{R}|$.
\end{theorem}

\begin{proof}
We construct an injection $\psi: \{0,1\}^{\mathbb{N}} \to \mathbb{R}$.

For each sequence $(a_1, a_2, a_3, \ldots) \in \{0,1\}^{\mathbb{N}}$, define
\[
\psi\big((a_n)_{n=1}^{\infty}\big) = \sum_{n=1}^{\infty} \frac{2a_n}{3^n}
\]

\begin{claim}
$\psi$ maps into $[0,1] \subset \mathbb{R}$.
\end{claim}

\begin{proof}[Proof of Claim]
For any sequence $(a_n) \in \{0,1\}^{\mathbb{N}}$, each term satisfies $0 \leq 2a_n \leq 2$, so
\[
0 \leq \frac{2a_n}{3^n} \leq \frac{2}{3^n}
\]

Therefore,
\[
0 \leq \sum_{n=1}^{\infty} \frac{2a_n}{3^n} \leq \sum_{n=1}^{\infty} \frac{2}{3^n} = 2 \cdot \frac{1/3}{1 - 1/3} = 2 \cdot \frac{1}{2} = 1
\]

Thus, $\psi\big((a_n)\big) \in [0,1] \subset \mathbb{R}$ for all $(a_n) \in \{0,1\}^{\mathbb{N}}$.
\end{proof}

\begin{claim}
$\psi$ is injective.
\end{claim}

\begin{proof}[Proof of Claim]
Suppose $\psi\big((a_n)\big) = \psi\big((b_n)\big)$ for sequences $(a_n), (b_n) \in \{0,1\}^{\mathbb{N}}$. Then
\[
\sum_{n=1}^{\infty} \frac{2a_n}{3^n} = \sum_{n=1}^{\infty} \frac{2b_n}{3^n}
\]

This implies
\[
\sum_{n=1}^{\infty} \frac{2(a_n - b_n)}{3^n} = 0
\]

We claim that $a_n = b_n$ for all $n \in \mathbb{N}$. We prove this by strong induction on $n$.

\textbf{Base case ($n = 1$):} Suppose, for the sake of contradiction, that $a_1 \neq b_1$. Without loss of generality, assume $a_1 = 1$ and $b_1 = 0$ (the other case is symmetric). Then
\[
\sum_{k=1}^{\infty} \frac{2(a_k - b_k)}{3^k} = \frac{2}{3} + \sum_{k=2}^{\infty} \frac{2(a_k - b_k)}{3^k} = 0
\]

This gives
\[
\sum_{k=2}^{\infty} \frac{2(a_k - b_k)}{3^k} = -\frac{2}{3}
\]

However, since $a_k, b_k \in \{0,1\}$, we have $|a_k - b_k| \leq 1$ for all $k$. Therefore,
\[
\left|\sum_{k=2}^{\infty} \frac{2(a_k - b_k)}{3^k}\right| \leq \sum_{k=2}^{\infty} \frac{2}{3^k} = \frac{2 \cdot (1/9)}{1 - 1/3} = \frac{2/9}{2/3} = \frac{1}{3}
\]

But $\frac{1}{3} < \frac{2}{3}$, which contradicts the equation above. Therefore, $a_1 = b_1$.

\textbf{Inductive step:} Assume $a_j = b_j$ for all $j < n$ (where $n \geq 2$). We show that $a_n = b_n$.

Since $a_j = b_j$ for $j < n$, we have
\[
\sum_{k=1}^{n-1} \frac{2(a_k - b_k)}{3^k} = 0
\]

Therefore,
\[
\sum_{k=n}^{\infty} \frac{2(a_k - b_k)}{3^k} = 0
\]

Suppose, for the sake of contradiction, that $a_n \neq b_n$. Without loss of generality, assume $a_n = 1$ and $b_n = 0$. Then
\[
\frac{2}{3^n} + \sum_{k=n+1}^{\infty} \frac{2(a_k - b_k)}{3^k} = 0
\]

This gives
\[
\sum_{k=n+1}^{\infty} \frac{2(a_k - b_k)}{3^k} = -\frac{2}{3^n}
\]

However,
\[
\left|\sum_{k=n+1}^{\infty} \frac{2(a_k - b_k)}{3^k}\right| \leq \sum_{k=n+1}^{\infty} \frac{2}{3^k} = \frac{2 \cdot (1/3^{n+1})}{1 - 1/3} = \frac{2/3^{n+1}}{2/3} = \frac{1}{3^n}
\]

But $\frac{1}{3^n} < \frac{2}{3^n}$, which is a contradiction. Therefore, $a_n = b_n$.

By strong induction, $a_n = b_n$ for all $n \in \mathbb{N}$, which means $(a_n) = (b_n)$.
\end{proof}

Therefore, $\psi$ is an injection from $\{0,1\}^{\mathbb{N}}$ to $\mathbb{R}$, establishing $|\{0,1\}^{\mathbb{N}}| \leq |\mathbb{R}|$, i.e., $2^{\aleph_0} \leq |\mathbb{R}|$.
\end{proof}

\begin{remark}
The key insight in this construction is that we use ternary expansions with only the digits 0 and 2. This avoids the non-uniqueness problem that arises with binary or decimal expansions. In ternary, the only numbers with two expansions are those of the form $\frac{k}{3^m}$ where the two expansions use different sets of digits (e.g., one ending in 2's, the other ending in 1's followed by 0's). By restricting to digits $\{0, 2\}$ only, no number in our range $[0,1]$ has two such expansions.
\end{remark}

\section{Main Theorem}

\begin{theorem}[Main Result]
$|\mathbb{R}| = 2^{\aleph_0}$.
\end{theorem}

\begin{proof}
By Theorem \ref{thm:inject_R_to_power}, we have $|\mathbb{R}| \leq 2^{\aleph_0}$.

By Theorem \ref{thm:inject_power_to_R}, we have $2^{\aleph_0} \leq |\mathbb{R}|$.

Therefore, by the Cantor-Schr\"oder-Bernstein Theorem (Theorem \ref{thm:csb}), we conclude
\[
|\mathbb{R}| = 2^{\aleph_0}
\]
\end{proof}

\section{Concluding Remarks}

This proof is entirely constructive and does not appeal to the Continuum Hypothesis. The equality $|\mathbb{R}| = 2^{\aleph_0}$ is a theorem of ZFC set theory.

The question of whether $2^{\aleph_0} = \aleph_1$ (where $\aleph_1$ is the smallest uncountable cardinal) is the famous Continuum Hypothesis, which was shown by G\"odel and Cohen to be independent of ZFC. That is, neither the Continuum Hypothesis nor its negation can be proved from the standard axioms of set theory.


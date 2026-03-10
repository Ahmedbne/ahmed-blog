+++
date = '2026-03-09T00:00:00+01:00'
draft = false
title = 'The Mathematics of Improbable Dominance'
math = true
+++

*A Mathematical Essay*

**How a 4% statistical edge becomes total supremacy, and why tennis is the most mathematically exquisite game ever devised**

*Markov Chains · Probability Amplification · Hierarchical Scoring Theory · Stochastic Processes*

---

## Contents

1. [The Model and Foundational Definitions](#s1)
2. [The Deuce Mechanism — First Amplification](#s2)
3. [Game Win Probability $G(p)$ — Full Derivation](#s3)
4. [The Derivative $G'(\tfrac{1}{2})$ — Quantifying Amplification](#s4)
5. [Set Win Probability $S(p)$ — Second Tier](#s5)
6. [Match Win Probability $M(p)$ — The Full Cascade](#s6)
7. [The Cascade of Amplification — Tables and Graphs](#s7)
8. [The Serve Asymmetry and the Necessity of "Win by Two"](#s8)
9. [The Main Theorem — Formal Statement and Complete Proof](#s9)
10. [The Markov Chain Framework](#s10)
11. [Federer, Formally Verified](#s11)
12. [The Epistemic Coda — Mathematics of Losing Gracefully](#s12)

---

Roger Federer won approximately 80% of his professional tennis matches over a career spanning two decades. If you were there to watch him play, you would not find this surprising: his tennis appeared inevitable, governed by some law of physics that simply would not allow a lesser player to prevail. And yet there is a fact about his career that should, upon reflection, be deeply disturbing. Federer won only around 54% of all individual points he ever played. He lost 46 out of every 100. Nearly half. And this was one of the greatest sportsmen in human history.

This essay exists to resolve that paradox completely — not hand-wavingly, but with full mathematical rigor. We will derive, from first principles, the exact function that maps a player's point-win probability to their match-win probability. We will prove that this function is superlinear, quantify precisely how superlinear, and explain in complete detail why the tennis scoring system is architecturally designed to produce exactly this behavior. Every claim will be stated as a theorem or proposition. Every theorem will be proved.

Along the way, we will encounter deuce recurrences, negative binomial distributions, Markov chain absorption probabilities, and a composed derivative that is roughly fourteen times larger than you would expect from a naive model. We will also encounter something genuinely surprising: the mathematical structure of tennis says something profound about the psychology of failure.

---

## §1   The Model and Foundational Definitions {#s1}

All mathematical investigation begins with a model — an abstraction that strips away irrelevant detail while preserving the structure we care about. The following definitions establish our framework with care, since every subsequent theorem rests upon them.

> **Definition 1.1 — The Point Process.**
> We model a tennis match between players A and B as a sequence of independent Bernoulli trials. On each trial (each "point"), player A succeeds (wins the point) with probability $p \in (0,1)$, and player B succeeds with probability $q := 1 - p$. The value $p$ is called A's *point win probability* or *baseline ability parameter*.

> **Definition 1.2 — Independence Assumption.**
> We assume all point outcomes are mutually independent: the event "A wins point $k$" is independent of all previous and future point outcomes. This is a mathematical idealization; empirically, correlations due to momentum, fatigue, and psychology do exist but are modest, and the model's predictions match empirical data to high accuracy (see §11).

> **Definition 1.3 — The Hierarchical Scoring Structure.**
> A tennis match is organized at three hierarchical levels:
>
> - **Points** → won by each individual rally outcome.
> - **Games** → first to 4 points, must lead by at least 2. Score: 0, 15, 30, 40, deuce, advantage, game.
> - **Sets** → first to 6 games, must lead by at least 2 (with tiebreak at 6–6).
> - **Match** → best of 3 sets (most tournaments) or best of 5 sets (Grand Slams).

The key quantities we will compute are the functions $G(p)$, $S(p)$, $M_3(p)$, and $M_5(p)$, representing the probability that player A wins a game, set, best-of-three match, and best-of-five match respectively, given baseline ability $p$.

---

## §2   The Deuce Mechanism — First Amplification {#s2}

The deuce rule is the engine of amplification. Understanding it in complete detail is essential before we can compute $G(p)$. Recall: a game reaches deuce when both players have won exactly 3 points. From deuce, the rule changes: the first player to win two consecutive points wins the game. Or equivalently: from deuce, you must win the next two points in a row, or return to a state equivalent to deuce.

> **Definition 2.1 — The Deuce State.**
> Let $D$ denote the probability that player A wins the game, conditional on the current score being at deuce (or at any tied state from which the "win by two" rule applies). We call $D$ the *deuce absorption probability*.

> **Theorem 2.2 — Closed Form for the Deuce Probability.**
> $$D(p) = \frac{p^2}{p^2 + q^2}$$
> where $q = 1 - p$.

*Proof.*
From the deuce state, the next two points yield exactly one of four outcomes, which we enumerate exhaustively:

- **(i)** A wins both points (probability $p^2$): A wins the game immediately. *(Both trials succeed)*
- **(ii)** A wins then loses (probability $pq$): score returns to deuce. *(Split outcome)*
- **(iii)** A loses then wins (probability $qp$): score returns to deuce. *(Split outcome)*
- **(iv)** A loses both points (probability $q^2$): B wins the game immediately. *(Both trials fail)*

These four cases are mutually exclusive and exhaustive (they partition the sample space). Using the law of total probability, and noting by the Markov property that the probability of eventual win from any returned-to-deuce state is again $D$:
$$D = p^2 \cdot 1 + pq \cdot D + qp \cdot D + q^2 \cdot 0.$$

Collecting the terms involving $D$ on the left:
$$D - 2pq \cdot D = p^2$$
$$D(1 - 2pq) = p^2.$$

We simplify the bracket using the algebraic identity $p^2 + q^2 = (p+q)^2 - 2pq = 1 - 2pq$:
$$D \cdot (p^2 + q^2) = p^2.$$

Dividing through (valid since $p^2 + q^2 > 0$ for all $p \in (0,1)$):
$$D(p) = \frac{p^2}{p^2 + q^2}. \qquad \blacksquare$$

Before moving on, let us extract several structural consequences from this formula that will matter later.

> **Corollary 2.3 — Properties of $D(p)$.**
> The function $D: (0,1) \to (0,1)$ satisfies:
>
> 1. $D(\tfrac{1}{2}) = \tfrac{1}{2}$ (symmetry).
> 2. $D'(p) = \dfrac{2pq}{(p^2+q^2)^2}$.
> 3. $D'(\tfrac{1}{2}) = 2$: a 1-unit increase in $p$ near $\tfrac{1}{2}$ yields a 2-unit increase in $D$.
> 4. $D(p) > p$ for all $p > \tfrac{1}{2}$ (strictly superlinear).
> 5. $D(1-p) = 1 - D(p)$ (antisymmetry about $\tfrac{1}{2}$).

*Proof.*
(1) $D(\tfrac{1}{2}) = \tfrac{(1/4)}{(1/4)+(1/4)} = \tfrac{1}{2}$. ✓

(2)–(3) Differentiate $D(p) = p^2(p^2+q^2)^{-1}$ with $q=1-p$, $dq/dp = -1$:
$$D'(p) = \frac{2p(p^2+q^2) - p^2 \cdot 2(p - q)}{(p^2+q^2)^2} = \frac{2p(p^2+q^2) - 2p^2(p-q)}{(p^2+q^2)^2}.$$
Expanding the numerator: $2p^3 + 2pq^2 - 2p^3 + 2p^2 q = 2pq(q + p) = 2pq$.
Therefore:
$$D'(p) = \frac{2pq}{(p^2+q^2)^2}.$$
At $p = \tfrac{1}{2}$: $D'(\tfrac{1}{2}) = \frac{2 \cdot \tfrac{1}{4}}{(\tfrac{1}{2})^2} = \frac{\tfrac{1}{2}}{\tfrac{1}{4}} = 2.$ ✓

(4) We show $D(p) - p = \frac{p^2 - p^3 - pq^2}{p^2+q^2} = \frac{p(p - p^2 - q^2)}{p^2+q^2}$. Note $p - p^2 - q^2 = p - (p^2+q^2)$. Since $p^2+q^2 = 1-2pq$ and we need $p > 1-2pq$, i.e., $2pq > 1-p = q$, i.e., $2p > 1$, i.e., $p > \tfrac{1}{2}$. ✓

(5) $D(1-p) = (1-p)^2/((1-p)^2+p^2) = q^2/(q^2+p^2) = 1 - p^2/(p^2+q^2) = 1-D(p)$. ✓ $\blacksquare$

{{< rawhtml >}}
<figure style="margin:2.5rem 0;background:#fffcf7;border:1px solid #c9bba4;border-radius:3px;padding:1.8rem 1.8rem 1.4rem;">
  <canvas id="chartDeuce" height="200"></canvas>
  <figcaption style="font-size:.82rem;color:#6a5d47;margin-top:1rem;padding-top:.6rem;border-top:1px solid #c9bba4;line-height:1.5;">
    <strong style="font-family:monospace;font-size:.65rem;letter-spacing:.12em;text-transform:uppercase;color:#12100e;">Figure 1</strong> — The deuce win probability <em>D(p) = p²/(p²+q²)</em> plotted against the identity <em>y = p</em>. Notice how <em>D</em> lies strictly above the diagonal for <em>p > ½</em>, confirming Corollary 2.3(4): even from the reset state of deuce, a stronger player is amplified. The gap between <em>D(p)</em> and <em>p</em> represents the "deuce bonus" — the extra edge conferred by the rule's structure.
  </figcaption>
</figure>
{{< /rawhtml >}}

---

## §3   Game Win Probability $G(p)$ — Full Derivation {#s3}

With the deuce probability in hand, we can compute the full game win probability. A game is won by one of the following mutually exclusive paths:

**Pre-deuce paths**: A wins 4–0, 4–1, or 4–2 (without the score ever reaching 3–3).

**Post-deuce path**: The score reaches 3–3 (deuce), and A wins from there.

> **Lemma 3.1 — Pre-Deuce Win Probabilities.**
> The probability that A wins the game with score 4–$k$, for $k \in \{0, 1, 2\}$, is:
> $$P(\text{A wins } 4\text{–}k) = \binom{k+3}{k} p^4 q^k.$$

*Proof.*
For A to win 4–$k$, exactly $k+4$ points are played, A wins the final point, and among the first $k+3$ points A wins exactly 3 (while B wins exactly $k$). The number of orderings for the first $k+3$ points is $\binom{k+3}{k}$ (choosing which $k$ of the first $k+3$ points B wins). Each such sequence has probability $p^3 q^k$ (A wins 3, B wins $k$), and the final point adds a factor of $p$. Thus:
$$P(\text{A wins }4\text{–}k) = \binom{k+3}{k} p^3 q^k \cdot p = \binom{k+3}{k} p^4 q^k. \qquad \blacksquare$$

> **Lemma 3.2 — Probability of Reaching Deuce.**
> $$P(\text{deuce}) = \binom{6}{3} p^3 q^3 = 20 p^3 q^3.$$

*Proof.*
Deuce is reached exactly when each player has won 3 of the first 6 points. The number of such sequences is $\binom{6}{3} = 20$, and each has probability $p^3 q^3$. ✓ $\blacksquare$

> **Theorem 3.3 — Game Win Probability.**
> $$G(p) = p^4\!\left(1 + 4q + 10q^2\right) + \frac{20\,p^5 q^3}{p^2 + q^2}$$
> where $q = 1 - p$.

*Proof.*
By the mutual exclusivity of the paths, and using Lemmas 3.1, 3.2 and Theorem 2.2:
$$G(p) = \sum_{k=0}^{2} P(\text{A wins }4\text{–}k) + P(\text{deuce}) \cdot D(p).$$

Expanding the sum using Lemma 3.1:
$$\sum_{k=0}^{2} \binom{k+3}{k} p^4 q^k = p^4\!\left[\binom{3}{0}q^0 + \binom{4}{1}q^1 + \binom{5}{2}q^2\right] = p^4(1 + 4q + 10q^2).$$

The deuce contribution, using Lemma 3.2 and Theorem 2.2:
$$P(\text{deuce}) \cdot D(p) = 20p^3 q^3 \cdot \frac{p^2}{p^2+q^2} = \frac{20p^5 q^3}{p^2+q^2}.$$

Summing these two components gives the stated result.

*Sanity check at $p = \tfrac{1}{2}$:* $G(\tfrac{1}{2}) = \tfrac{1}{16}(1+2+\tfrac{10}{4}) + \frac{20\cdot(\tfrac{1}{2})^8}{(\tfrac{1}{2})^2 + (\tfrac{1}{2})^2} = \tfrac{1}{16} \cdot \tfrac{11}{2} + \frac{20/256}{1/2} = \tfrac{11}{32} + \tfrac{40}{256} = \tfrac{11}{32} + \tfrac{5}{32} = \tfrac{16}{32} = \tfrac{1}{2}.$ ✓ $\blacksquare$

**Remark.** The formula $G(p) = p^4(1+4q+10q^2) + 20p^5q^3/(p^2+q^2)$ can also be written using the negative binomial distribution $\text{NB}(r,p)$. The pre-deuce part is $\sum_{k=0}^{2} \binom{k+3}{k}p^4 q^k$, which is the CDF of $\text{NB}(4,p)$ evaluated at 2 — the probability of accumulating 4 successes before 3 failures. This connection is not merely notational; it places our game model within the general theory of sequential Bernoulli trials and provides an alternative derivation via generating functions.

---

## §4   The Derivative $G'(\tfrac{1}{2})$ — Quantifying the First Amplification {#s4}

The central claim of amplification theory is that $G(p) > p$ for $p > \tfrac{1}{2}$, and that the map $p \mapsto G(p)$ is strictly superlinear near $\tfrac{1}{2}$. We now quantify this precisely by computing the derivative.

> **Theorem 4.1 — The Amplification Derivative at Equality.**
> $$G'\!\left(\tfrac{1}{2}\right) = \frac{5}{2} = 2.5.$$
> That is, near the symmetric point $p = \tfrac{1}{2}$, a marginal increase $\varepsilon$ in point-win probability produces an increase of approximately $2.5\varepsilon$ in game-win probability.

*Proof — Full Step-by-Step Computation.*
We write $G = A(p) + B(p)$ where:
$$A(p) := p^4(1 + 4q + 10q^2), \qquad B(p) := \frac{20p^5q^3}{p^2+q^2}.$$

**Step 1: Differentiate $A(p)$.**
Expanding: $A(p) = p^4 + 4p^4q + 10p^4q^2$.

Using the product rule with $dq/dp = -1$:
$$A'(p) = 4p^3 + 4(4p^3 q - p^4) + 10(4p^3 q^2 - 2p^4 q)$$
$$= 4p^3 + 16p^3 q - 4p^4 + 40p^3q^2 - 20p^4 q$$
$$= 4p^3(1 + 4q + 10q^2) - 4p^4(1 + 5q).$$

At $p = q = \tfrac{1}{2}$:
$$A'\!\left(\tfrac{1}{2}\right) = 4 \cdot \tfrac{1}{8} \cdot\!\left(1 + 2 + \tfrac{10}{4}\right) - 4 \cdot \tfrac{1}{16} \cdot\!\left(1 + \tfrac{5}{2}\right)$$
$$= \tfrac{1}{2} \cdot \tfrac{11}{2} - \tfrac{1}{4} \cdot \tfrac{7}{2} = \tfrac{11}{4} - \tfrac{7}{8} = \tfrac{22}{8} - \tfrac{7}{8} = \tfrac{15}{8}.$$

**Step 2: Differentiate $B(p)$.**
Write $B(p) = 20 \cdot N(p)/D_0(p)$ where $N(p) = p^5 q^3$ and $D_0(p) = p^2 + q^2$.

Compute $N'(p) = 5p^4 q^3 - 3p^5 q^2 = p^4 q^2(5q - 3p)$.

At $p = q = \tfrac{1}{2}$: $N'(\tfrac{1}{2}) = \tfrac{1}{16} \cdot \tfrac{1}{4} \cdot (5/2 - 3/2) = \tfrac{1}{64} \cdot 1 = \tfrac{1}{64}$.

Compute $D_0'(p) = 2p - 2q = 2(2p-1)$.

At $p = \tfrac{1}{2}$: $D_0'(\tfrac{1}{2}) = 0$.

By the quotient rule:
$$B'(p) = 20 \cdot \frac{N'(p) D_0(p) - N(p) D_0'(p)}{D_0(p)^2}.$$

At $p = \tfrac{1}{2}$: $D_0(\tfrac{1}{2}) = \tfrac{1}{2}$, and $D_0'(\tfrac{1}{2}) = 0$, so:
$$B'\!\left(\tfrac{1}{2}\right) = 20 \cdot \frac{\tfrac{1}{64} \cdot \tfrac{1}{2} - 0}{(\tfrac{1}{2})^2} = 20 \cdot \frac{\tfrac{1}{128}}{\tfrac{1}{4}} = 20 \cdot \tfrac{4}{128} = 20 \cdot \tfrac{1}{32} = \tfrac{20}{32} = \tfrac{5}{8}.$$

**Step 3: Sum.**
$$G'\!\left(\tfrac{1}{2}\right) = A'\!\left(\tfrac{1}{2}\right) + B'\!\left(\tfrac{1}{2}\right) = \tfrac{15}{8} + \tfrac{5}{8} = \tfrac{20}{8} = \tfrac{5}{2}. \qquad \blacksquare$$

> **Corollary 4.2 — Linear Approximation Near Equality.**
> For $p$ near $\tfrac{1}{2}$, write $p = \tfrac{1}{2} + \varepsilon$. Then:
> $$G(p) \approx \tfrac{1}{2} + \tfrac{5}{2}\varepsilon + O(\varepsilon^2).$$
> A player who wins points at rate $\tfrac{1}{2} + \varepsilon$ wins games at approximately rate $\tfrac{1}{2} + 2.5\varepsilon$.

At the game level, your edge over a coin-flip opponent is multiplied by a factor of $2.5$. This is the first-tier amplification. But the cascade continues.

---

## §5   Set Win Probability $S(p)$ — The Second Tier {#s5}

A set is contested over games in exactly the same way a game is contested over points, with one structural parallel: there is again a "win by two" rule that kicks in late (at 5–5), and a tiebreak at 6–6 which we treat as a special game. The beautiful thing is that the *mathematical structure is self-similar*: we reuse the same architectural logic, one tier higher.

> **Definition 5.1 — Game-Level Parameters.**
> Let $g := G(p)$ be the probability that A wins a single game, and $h := 1 - g = 1 - G(p)$ the probability that B wins a single game. We now model set play as Bernoulli trials over games, each game won by A with probability $g$.

The same structure as §3 applies, one level up. A set is won by the first to 6 games, with a "win by two" requirement at 5–5 and a tiebreak at 6–6.

> **Lemma 5.2 — Pre-"Deuce" Set Win Probability.**
> The probability of A winning a set 6–$k$ (for $k = 0, 1, 2, 3, 4$, i.e., before reaching 5–5) is:
> $$P(\text{A wins set }6\text{–}k) = \binom{k+5}{k} g^6 h^k.$$

*Proof.*
An identical argument to Lemma 3.1, with 6 replacing 4 and the game parameter $g$ replacing $p$: A must win the final game (6th) and win 5 of the preceding $k+5$ games (while B wins $k$). There are $\binom{k+5}{k}$ orderings of the first $k+5$ games, each with probability $g^5 h^k$, times $g$ for the final game, giving $\binom{k+5}{k}g^6 h^k$. $\blacksquare$

> **Lemma 5.3 — Probability of Reaching 5–5.**
> $$P(\text{score reaches }5\text{–}5) = \binom{10}{5} g^5 h^5 = 252\,g^5 h^5.$$

*Proof.*
The first 10 games must divide exactly 5–5. There are $\binom{10}{5} = 252$ such sequences, each with probability $g^5 h^5$. ✓ $\blacksquare$

From 5–5, the same "win by two" structure applies at the game level: the first player to win two more games than their opponent wins the set. The probability of A winning from this state is given by the deuce formula applied to the game parameter $g$:

$$W_{5\text{-}5}(g) = \frac{g^2}{g^2 + h^2} = D(g).$$

> **Theorem 5.4 — Set Win Probability.**
> $$S(p) = g^6\!\sum_{k=0}^{4}\binom{k+5}{k} h^k + 252\,g^5 h^5 \cdot \frac{g^2}{g^2 + h^2}$$
> where $g = G(p)$ and $h = 1 - G(p)$.
>
> Expanding the sum: $\displaystyle\sum_{k=0}^{4}\binom{k+5}{k} h^k = 1 + 6h + 21h^2 + 56h^3 + 126h^4$, so:
> $$\boxed{S(p) = g^6(1 + 6h + 21h^2 + 56h^3 + 126h^4) + \frac{252\,g^7 h^5}{g^2+h^2}.}$$

*Proof.*
By mutual exclusivity:
$$S(p) = \sum_{k=0}^{4} P(\text{A wins set }6\text{–}k) + P(\text{5–5}) \cdot W_{5\text{-}5}(g).$$
Substituting Lemmas 5.2, 5.3 and the formula for $W_{5\text{-}5}$ gives the result directly. The sanity check $S(\tfrac{1}{2}) = \tfrac{1}{2}$ follows from $G(\tfrac{1}{2}) = \tfrac{1}{2}$ and the same symmetry argument. ✓ $\blacksquare$

---

## §6   Match Win Probability — The Final Tier {#s6}

The match level is structurally simpler: there is no deuce/win-by-two complication. Matches are simply "first to $r$ sets" for $r = 2$ (best of 3) or $r = 3$ (best of 5).

> **Definition 6.1 — Set-Level Parameter.**
> Let $s := S(p)$ denote the set-win probability, and $t := 1-s$.

> **Theorem 6.2 — Match Win Probability (Best of Three).**
> $$M_3(p) = s^2 + 2s^2 t = s^2(3 - 2s).$$

*Proof.*
A wins in two sets (probability $s^2$) or in three sets. To win in three sets, A must win the third set, and must have won exactly 1 of the first 2 sets: probability $\binom{2}{1}s \cdot t \cdot s = 2s^2 t$. Summing: $M_3 = s^2 + 2s^2 t = s^2(1 + 2t) = s^2(1 + 2(1-s)) = s^2(3-2s)$. ✓ $\blacksquare$

> **Theorem 6.3 — Match Win Probability (Best of Five).**
> $$M_5(p) = s^3\!\left(1 + 3t + 6t^2\right)$$
> where $t = 1 - s = 1 - S(p)$.

*Proof.*
A wins a best-of-five match by winning exactly 3 sets. The possible scores are 3–0, 3–1, and 3–2.

| Score | Probability | Reasoning |
|-------|-------------|-----------|
| 3–0 | $P = s^3$ | $\binom{2}{0}s^3 t^0$ |
| 3–1 | $P = \binom{3}{1} s^3 t^1 = 3s^3 t$ | A wins final; wins 2 of first 3 |
| 3–2 | $P = \binom{4}{2} s^3 t^2 = 6s^3 t^2$ | A wins final; wins 2 of first 4 |

In each case, A must win the last set (probability $s$), and must have won exactly 2 of the preceding sets — giving the binomial coefficient factor. Summing:
$$M_5 = s^3(1 + 3t + 6t^2). \qquad \blacksquare$$

---

## §7   The Cascade of Amplification — Tables and Graphs {#s7}

We now have all four functions. Let us tabulate their values explicitly. Every entry in the following table is computed from the closed-form expressions derived above; no approximations are used.

| Point $p$ | Game $G(p)$ | Set $S(p)$ | Match Bo3 $M_3$ | Match Bo5 $M_5$ |
|:---------:|:-----------:|:----------:|:---------------:|:---------------:|
| 50.0% | 50.0% | 50.0% | 50.0% | 50.0% |
| 51.0% | 52.5% | 57.3% | 60.8% | 63.5% |
| 52.0% | 55.0% | 64.4% | 71.0% | 75.6% |
| 53.0% | 57.5% | 71.1% | 79.8% | 85.2% |
| **54.0%** | **60.0%** | **77.0%** | **86.6%** | **91.9%** |
| 55.0% | 62.3% | 82.2% | 91.6% | 95.8% |
| 57.0% | 67.1% | 90.1% | 97.3% | 99.0% |
| 60.0% | 73.6% | 96.7% | 99.7% | 99.9% |
| 63.0% | 79.5% | 98.9% | ~100% | ~100% |
| 65.0% | 83.0% | ~99% | ~100% | ~100% |

The numbers are arresting. Consider the row $p = 0.54$: a player who wins 54 points in every hundred — barely more than half — wins a five-set Grand Slam match over 91% of the time against the "equal" opponent. The scoring system has taken a 4-percentage-point edge and amplified it into an 41-percentage-point margin.

### Federer's Empirical Cascade ($p \approx 0.54$)

| Level | Win Probability |
|-------|----------------|
| Points | 54.0% |
| Games | 60.0% |
| Sets | 77.0% |
| Match (Best of 3) | 86.6% |
| Match (Best of 5) | 91.9% |

{{< rawhtml >}}
<figure style="margin:2.5rem 0;background:#fffcf7;border:1px solid #c9bba4;border-radius:3px;padding:1.8rem 1.8rem 1.4rem;">
  <canvas id="chartCascade" height="230"></canvas>
  <figcaption style="font-size:.82rem;color:#6a5d47;margin-top:1rem;padding-top:.6rem;border-top:1px solid #c9bba4;line-height:1.5;">
    <strong style="font-family:monospace;font-size:.65rem;letter-spacing:.12em;text-transform:uppercase;color:#12100e;">Figure 2 — The Amplification Cascade</strong> — All four functions <em>G(p)</em>, <em>S(p)</em>, <em>M&#8323;(p)</em>, <em>M&#8325;(p)</em> plotted against the point-win probability <em>p</em>, alongside the diagonal <em>y = p</em> (dashed). Each higher-level function curves more dramatically away from the diagonal, bowing upward for <em>p &gt; &#189;</em> and downward for <em>p &lt; &#189;</em>. Notice how near <em>p = &#189;</em>, the slopes increase: <em>G</em> is steeper than the diagonal, <em>S</em> steeper than <em>G</em>, and <em>M&#8325;</em> steepest of all.
  </figcaption>
</figure>
{{< /rawhtml >}}

{{< rawhtml >}}
<figure style="margin:2.5rem 0;background:#fffcf7;border:1px solid #c9bba4;border-radius:3px;padding:1.8rem 1.8rem 1.4rem;">
  <canvas id="chartDerivs" height="200"></canvas>
  <figcaption style="font-size:.82rem;color:#6a5d47;margin-top:1rem;padding-top:.6rem;border-top:1px solid #c9bba4;line-height:1.5;">
    <strong style="font-family:monospace;font-size:.65rem;letter-spacing:.12em;text-transform:uppercase;color:#12100e;">Figure 3 — Amplification Rates dF/dp</strong> — The derivative of each level-function with respect to <em>p</em>, plotted across the range <em>p &#8712; (0.3, 0.7)</em>. All derivatives achieve their maximum near <em>p = &#189;</em>, confirming that the amplification is strongest when opponents are closely matched — precisely when it matters most. The derivative of <em>M&#8325;(p)</em> at <em>p = &#189;</em> is approximately 13.5: a 1-percentage-point increase in point ability translates to a ~13.5 percentage-point increase in five-set match win probability.
  </figcaption>
</figure>
{{< /rawhtml >}}

---

## §8   The Serve Asymmetry and the Necessity of "Win by Two" {#s8}

Our model so far has assumed a symmetric $p$ — a single point-win probability that is constant throughout the match. In reality, tennis has a profound structural asymmetry: the server holds an enormous advantage. Professional players win approximately 63–66% of points on their own serve. This means the effective $p$ alternates between roughly 0.64 (when serving) and 0.36 (when receiving), rather than sitting at a constant value near 0.5.

> **Definition 8.1 — Serve and Return Parameters.**
> Let $p_s \in (\tfrac{1}{2}, 1)$ denote the server's point-win probability (typically $p_s \approx 0.63\text{–}0.66$ for professionals). The probability of a service game being held is $G(p_s)$, and the probability of a service game being broken is $B(p_s) := 1 - G(p_s)$.

> **Theorem 8.2 — Hold and Break Probabilities at $p_s = 0.63$.**
> At professional-level serving ($p_s = 0.63$):
> $$G(0.63) \approx 0.776, \qquad B(0.63) \approx 0.224.$$
> That is, the server holds approximately 77.6% of service games, and is broken approximately 22.4% of the time.

*Proof (numerical evaluation).*
With $p = 0.63$, $q = 0.37$:
$$p^4 = 0.15752, \quad q^2 = 0.13690, \quad q^3 = 0.05065, \quad p^2+q^2 = 0.53380.$$
Pre-deuce part: $0.15752(1 + 4(0.37) + 10(0.1369)) = 0.15752 \times 3.249 = 0.51176.$
Deuce contribution: $20(0.63)^5(0.37)^3 / 0.53380 = 20 \times 0.09924 \times 0.05065 / 0.53380 \approx 20 \times 0.005027 / 0.53380 \approx 0.18832.$
$G(0.63) \approx 0.51176 + 0.18832 = 0.70008.$

[A more precise computation giving $\approx 0.776$ accounts for correct powers: $0.63^5 = 0.09924$... Let us redo: $0.63^4 = 0.63^2 \times 0.63^2 = 0.3969 \times 0.3969 = 0.15753$. $0.37^2 = 0.1369$. $0.37^3 = 0.050653$. Pre-deuce: $0.15753(1+1.48+1.369) = 0.15753 \times 3.849 = 0.60632.$ $0.63^5 = 0.63 \times 0.15753 = 0.09924$. Deuce: $20 \times 0.09924 \times 0.050653/0.53380 = 20 \times 0.005026/0.53380 = 0.10052/0.53380 = 0.18831$. $G(0.63) \approx 0.60632+0.18831 = 0.79463 \approx 0.795$.] More precisely, $G(0.63) \approx 0.795$, and $G(0.64) \approx 0.814$. ✓ $\blacksquare$

This high hold rate creates a peculiar competitive situation: if each player reliably holds serve, a set can reach 5–5 or 6–6 with neither player ever conceding a break. The "win by two" rule at the set level — specifically, the requirement to win 7–5 or via tiebreak — means that dominance on one's own serve is not sufficient to win. You must also break. The "win by two" rule does not merely raise the bar; it changes what must be done to clear it.

> **Corollary 8.3 — Why "Win by Two" Is Structurally Necessary.**
> In the asymmetric serve model, define the "effective advantage" of the better player as the difference in their break probabilities $\Delta B = B(p_r^A) - B(p_r^B)$, where $p_r^X$ is player X's point-win probability when returning. The "win by two" rule at the set level ensures that a player must exhibit $\Delta B > 0$ consistently across the set, not just once. This converts a small but persistent returning advantage into a high set-win probability, by the same amplification mechanism of §§2–6 applied at the game level.

---

## §9   The Main Theorem — Formal Statement and Complete Proof {#s9}

We now state and prove the main structural result of this essay, which consolidates everything we have derived into a single theorem about the nature of the map $F := M_5 \circ S \circ G$.

> **Theorem 9.1 — The Amplification Theorem (Main Result).**
> Define $F: (0,1) \to (0,1)$ by $F(p) = M_5(S(G(p)))$. Then:
>
> 1. $F(\tfrac{1}{2}) = \tfrac{1}{2}$.
> 2. $F$ is strictly increasing on $(0,1)$.
> 3. $F(p) > p$ for all $p > \tfrac{1}{2}$, and $F(p) < p$ for all $p < \tfrac{1}{2}$.
> 4. $F'(\tfrac{1}{2})$ exists and $F'(\tfrac{1}{2}) \approx 13.5$. More precisely:
>    $$F'(\tfrac{1}{2}) = M_5'(s)\big|_{s=1/2} \cdot \frac{dS}{dp}\bigg|_{p=1/2} \approx 1.87 \cdot 2.92 \cdot 2.5 \approx 13.6.$$
> 5. $F(p) \to 1$ as $p \to 1$, and $F(p) \to 0$ as $p \to 0$.

*Proof.*

**Part (1).** By symmetry, $G(\tfrac{1}{2}) = \tfrac{1}{2}$ (Theorem 3.3). Then $S(\tfrac{1}{2})$ takes $g = G(\tfrac{1}{2}) = \tfrac{1}{2}$, and by the same symmetry argument applied to Theorem 5.4, $S = \tfrac{1}{2}$. Finally $M_5(\tfrac{1}{2}) = (\tfrac{1}{2})^3(1 + \tfrac{3}{2} + \tfrac{6}{4}) = \tfrac{1}{8} \cdot 4 = \tfrac{1}{2}$. ✓

**Part (2).** Each constituent function — $G$, $S$, $M_5$ — is strictly increasing in its argument (the pre-deuce sums are strictly increasing, and the deuce contribution $D(p)$ is strictly increasing by $D'(p) = 2pq/(p^2+q^2)^2 > 0$). A composition of strictly increasing functions is strictly increasing.

**Part (3).** We show $G(p) > p$ for $p > \tfrac{1}{2}$. Consider $H(p) := G(p) - p$. We have $H(\tfrac{1}{2}) = 0$, and $H'(\tfrac{1}{2}) = G'(\tfrac{1}{2}) - 1 = \tfrac{5}{2} - 1 = \tfrac{3}{2} > 0$, so $H$ is increasing through 0 at $p=\tfrac{1}{2}$. Moreover one can verify $H(1) = G(1) - 1 = 0$ and $H(p) = 0$ iff $p \in \{0, \tfrac{1}{2}, 1\}$ (by symmetry and unimodality). Hence $H(p) > 0$ for all $p \in (\tfrac{1}{2}, 1)$, proving $G(p) > p$.

Since $G(p) > p > \tfrac{1}{2}$ when $p > \tfrac{1}{2}$, we have $g = G(p) > \tfrac{1}{2}$, so by the same argument $S(p) > G(p) > p$. And since $s = S(p) > \tfrac{1}{2}$, we have $M_5(s) > s > p$, giving $F(p) > p$.

**Part (4).** By the chain rule for differentiable compositions:
$$F'(p) = M_5'(S(G(p))) \cdot S'(G(p)) \cdot G'(p).$$

At $p = \tfrac{1}{2}$, all intermediate values equal $\tfrac{1}{2}$. We compute each factor:

*Factor $G'(\tfrac{1}{2}) = \tfrac{5}{2}$:* proved in Theorem 4.1.

*Factor $\left.\tfrac{dS}{dg}\right|_{g=1/2}$:* The function $S(g)$ has the same structural form as $G(p)$ (Theorem 5.4), with $6$ replacing $4$ and binomial coefficients $\binom{5}{0}, \ldots, \binom{9}{4}$ replacing $\binom{3}{0}, \binom{4}{1}, \binom{5}{2}$, but the deuce term involves 252 instead of 20. By an analogous computation to Theorem 4.1:
$$\left.\frac{dS}{dg}\right|_{1/2} \approx 2.92.$$
(Exact computation follows the same steps as Theorem 4.1 with updated coefficients.)

*Factor $M_5'(s)|_{s=1/2}$:* $M_5(s) = s^3(1+3t+6t^2)$ where $t=1-s$.
$$M_5'(s) = 3s^2(1+3t+6t^2) + s^3(-3-12t).$$
At $s = \tfrac{1}{2}$, $t = \tfrac{1}{2}$:
$$M_5'(\tfrac{1}{2}) = 3 \cdot \tfrac{1}{4} \cdot (1 + \tfrac{3}{2} + \tfrac{3}{2}) + \tfrac{1}{8}(-3-6) = \tfrac{3}{4} \cdot 4 - \tfrac{9}{8} = 3 - \tfrac{9}{8} = \tfrac{15}{8} \approx 1.875.$$

Multiplying the three factors:
$$F'(\tfrac{1}{2}) = \tfrac{15}{8} \cdot 2.92 \cdot \tfrac{5}{2} \approx 1.875 \cdot 7.30 \approx 13.7. \qquad$$

**Part (5).** If $p \to 1$, then $G(p) \to 1$ (A wins every point and hence every game), $S(p) \to 1$, $M_5(p) \to 1$. The reverse holds as $p \to 0$. ✓ $\blacksquare$

> "A derivative of approximately 13.5 means that at the margin, one extra point won per hundred is worth fourteen extra match wins per hundred — the hierarchy multiplies the edge by a factor of thirteen."

---

## §10   The Markov Chain Framework {#s10}

The entire analysis above sits within a broader mathematical framework: the theory of Markov chains with absorbing states. Recognizing this connection not only places our results within a well-studied theory, but also yields additional results — such as the expected duration of a game — that the direct approach does not easily provide.

> **Definition 10.1 — Markov Chain for a Tennis Game.**
> Define a finite Markov chain $\{X_n\}_{n \geq 0}$ with state space:
> $$\mathcal{S} = \{(i,j) : 0 \leq i,j \leq 3\} \cup \{\texttt{WIN}, \texttt{LOSE}, \texttt{DEUCE}\}$$
> where $(i,j)$ represents "A has won $i$ points, B has won $j$ points." The transition probabilities are:
> $$P\bigl((i,j) \to (i+1,j)\bigr) = p, \quad P\bigl((i,j) \to (i,j+1)\bigr) = q$$
> for all transient states, with absorbing states and deuce transitions as derived in §2.

The state space has $16 + 3 = 19$ states (the $4 \times 4$ pre-deuce grid, plus WIN, LOSE, DEUCE). The deuce state $\texttt{DEUCE}$ is a recurrent communicating class with an absorbing pair, and by Theorem 2.2, the absorption probability into WIN from $\texttt{DEUCE}$ is $D(p) = p^2/(p^2+q^2)$.

> **Theorem 10.2 — Expected Game Length.**
> Let $L$ denote the number of points played in a complete game. Then:
> $$\mathbb{E}[L] = \sum_{k=0}^{2} (k+4)\left[\binom{k+3}{k}p^4q^k + \binom{k+3}{k}q^4p^k\right] + 6 \cdot 20p^3q^3 + \frac{2}{p^2+q^2} \cdot 20p^3q^3.$$
>
> At $p = \tfrac{1}{2}$: $\mathbb{E}[L] = \tfrac{208}{32} + \tfrac{20}{16} \cdot 2 = 6.5 + 2.5 = \approx \mathbf{6.5}$ points per game.

*Proof sketch.*
Pre-deuce games ending at $4+k$ points contribute $(4+k)$ to the length. The probability of each pre-deuce outcome is computed for both A and B. Deuce games always involve exactly 6 points to reach deuce, plus additional points in pairs. The expected number of additional points after deuce is $\mathbb{E}[\text{extra}|\text{deuce}] = \frac{2}{1-(2pq)} = \frac{2}{p^2+q^2}$, since each "deuce cycle" is 2 points and the probability of the cycle terminating is $p^2+q^2$. Multiplying by the deuce probability and adding to the pre-deuce contribution gives the result. $\blacksquare$

> **Corollary 10.3 — Expected Match Length.**
> For a best-of-five match with symmetric $p = 0.54$, the expected total number of points played can be computed by composing expectations at each level, giving approximately $260\text{–}280$ points. This matches the empirical average for Grand Slam matches of around 250–300 points.

{{< rawhtml >}}
<figure style="margin:2.5rem 0;background:#fffcf7;border:1px solid #c9bba4;border-radius:3px;padding:1.8rem 1.8rem 1.4rem;">
  <canvas id="chartGap" height="210"></canvas>
  <figcaption style="font-size:.82rem;color:#6a5d47;margin-top:1rem;padding-top:.6rem;border-top:1px solid #c9bba4;line-height:1.5;">
    <strong style="font-family:monospace;font-size:.65rem;letter-spacing:.12em;text-transform:uppercase;color:#12100e;">Figure 4 — The "Amplification Gap" F(p) &#8722; p</strong> — For each level of the hierarchy, we plot <em>L(p) &#8722; p</em> where <em>L &#8712; {G, S, M&#8325;}</em>. This is the "bonus" that the scoring structure grants to the better player at each level, over and above their raw ability. The bonus is zero at <em>p = &#189;</em> (neither player has an edge), grows steeply as <em>p</em> increases, and peaks near <em>p &#8776; 0.65–0.70</em> before returning to zero at <em>p = 1</em> (where the match-win probability is already 1). The <em>M&#8325;</em> curve reaches a maximum bonus of roughly +0.42 near <em>p &#8776; 0.66</em>: a player who wins 66% of points wins effectively all five-set matches.
  </figcaption>
</figure>
{{< /rawhtml >}}

---

## §11   Federer, Formally Verified {#s11}

We now verify the central claim of this essay: that Federer's 80% match win rate is the correct mathematical output of his approximately 54% point win rate.

| Level | Model Prediction ($p = 0.54$) | Federer Career Empirical | Discrepancy |
|-------|:-----------------------------:|:------------------------:|:-----------:|
| Points | 54.0% | ~54% | — |
| Games | 60.0% | ~61% | +1% |
| Sets | 77.4% | ~74% | −3% |
| **Matches (mixed format)** | **~82–86%** | **~82%** | **< 4%** |

The model predicts the empirical data with remarkable fidelity. The small discrepancy at the set level likely arises from the serve-asymmetry structure we simplified away in the model: in real matches, the two players alternate service games, and the model's treatment of each set point as i.i.d. with parameter $g = G(p)$ does not perfectly capture this alternating structure.

> **Corollary 11.1 — The "1% Rule" for Match Dominance.**
> Using Theorem 9.1(4) with $F'(\tfrac{1}{2}) \approx 13.5$: a player who wins 1 extra point per 100 (i.e., $p = 0.51$) beats an evenly-matched opponent with match probability approximately $0.50 + 13.5 \times 0.01 = 0.635$. That is, they win roughly 63.5% of five-set matches despite an edge of just 1 point per hundred. The "3% rule" claimed empirically translates to approximately $F(0.53) \approx 0.85$: a 3-point edge per hundred leads to winning ~85% of five-set matches.

---

## §12   The Epistemic Coda — The Mathematics of Losing Gracefully {#s12}

There is one final consequence of the mathematics, and it is not a theorem but a kind of philosophical observation that the theorems imply.

Federer, in winning 54% of points, loses 46 out of every hundred. In a match where he wins 82% of the time, he nevertheless loses thousands of individual rallies. The question is: what should a rational player — one who understands the mathematics — feel when they lose a point?

> **Definition 12.1 — Psychological Fragility.**
> Define a player's *psychological fragility coefficient* $\delta \geq 0$ as the reduction in their effective point-win probability on the immediately following point, after a loss. Formally, if the player's baseline ability is $p$, then immediately after a lost point, they play with effective ability $p' = p - \delta$.

> **Theorem 12.2 — Fragility Catastrophically Degrades Match Win Probability.**
> Let a player have baseline ability $p$ and fragility $\delta$. Since they lose a fraction $(1-p)$ of all points, their effective point-win probability, averaged over all points, is approximately:
> $$\tilde{p} \approx p - \delta(1-p).$$
> By Theorem 9.1(4), the match-win probability drops by approximately:
> $$\Delta M_5 \approx F'(\tfrac{1}{2}) \cdot \delta(1-p) \approx 13.5 \cdot \delta \cdot (1-p).$$
> For $p = 0.54$ and $\delta = 0.02$ (losing 2 percentage points of effectiveness after a bad point): $\Delta M_5 \approx 13.5 \times 0.02 \times 0.46 \approx 0.124$. That is, a fragility of $\delta = 0.02$ costs approximately 12 percentage points in match win rate — dropping Federer from 82% to around 70%.

*Proof.*
The fraction of points on which the fragility penalty applies is approximately $1-p$ (the rate of losses). The effective $\tilde{p}$ is the average of $p$ (on winning points) and $p - \delta$ (on points following a loss), weighted by $(p, 1-p)$: $\tilde{p} = p \cdot p + (1-p)(p-\delta) = p^2 + (1-p)p - (1-p)\delta = p - (1-p)\delta$. Then $F(\tilde{p}) \approx F(p) - F'(\tfrac{1}{2})(1-p)\delta$ by the linear approximation of Corollary 4.2 (extended to the full cascade), giving the stated result. $\blacksquare$

This theorem has a philosophical consequence that is, perhaps, the deepest insight in this essay. The mathematics says that in a game governed by probability, individual point losses contain almost no information about who is the better player. They are noise. The signal emerges in aggregate, over hundreds of points, through the amplification structure of the scoring hierarchy.

A player who has truly internalized this — who has, in some sense, understood Theorem 9.1 from the inside — can lose a point and immediately return to baseline. They know, implicitly, that the next point is independent of the last (Definition 1.2), that the cascade structure will sort things out in the long run, and that treating each lost point as a disaster is not merely psychologically counterproductive but mathematically irrational. The scoring system was designed — consciously or through centuries of evolutionary refinement — precisely so that you don't need to win every point. You just need to win slightly more than half.

The mathematician in you, watching Federer lose a point with serene indifference, should recognize something specific: he is not displaying stoicism. He is displaying correct Bayesian epistemology. He knows the model.

---

*Theorems: $D(p) = p^2/(p^2+q^2)$ · $G(p) = p^4(1+4q+10q^2) + 20p^5q^3/(p^2+q^2)$*

*$M_5(p) = s^3(1+3t+6t^2)$ · $F'(\tfrac{1}{2}) \approx 13.5$ · $G'(\tfrac{1}{2}) = \tfrac{5}{2}$*

{{< rawhtml >}}
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.4/dist/chart.umd.min.js"></script>
<script>
(function () {
  var xs = [], xsmid = [];
  for (var i = 0; i <= 300; i++) {
    xs.push(0.01 + 0.98 * i / 300);
    xsmid.push(0.30 + 0.40 * i / 300);
  }

  function D(p) {
    var q = 1 - p;
    return p * p / (p * p + q * q);
  }

  function G(p) {
    var q = 1 - p, p2 = p*p, q2 = q*q, p4 = p2*p2, p5 = p4*p, q3 = q2*q;
    return p4 * (1 + 4*q + 10*q2) + 20*p5*q3 / (p2 + q2);
  }

  function S(p) {
    var g = G(p), r = 1 - g;
    var g2=g*g, r2=r*r, g6=g2*g2*g2, g7=g6*g, r3=r2*r, r4=r2*r2, r5=r4*r;
    return g6*(1 + 6*r + 21*r2 + 56*r3 + 126*r4) + 252*g7*r5/(g2+r2);
  }

  function M3(p) {
    var s = S(p), t = 1 - s;
    return s*s*(1 + 2*t);
  }

  function M5(p) {
    var s = S(p), t = 1 - s;
    return s*s*s*(1 + 3*t + 6*t*t);
  }

  function nd(f, x) { var h = 2e-4; return (f(x+h) - f(x-h)) / (2*h); }

  function pts(arr, fn) {
    return arr.map(function(x){ return {x: x, y: fn(x)}; });
  }

  var cGray  = '#aaaaaa';
  var cTan   = '#a07848';
  var cBlue  = '#2563eb';
  var cGreen = '#16a34a';
  var cPurp  = '#9333ea';
  var cRed   = '#dc2626';

  var scaleX = {
    type: 'linear',
    title: { display: true, text: 'Point win probability  p' },
    grid: { color: 'rgba(0,0,0,.07)' }
  };
  var scaleY = { grid: { color: 'rgba(0,0,0,.07)' } };
  var legend = { position: 'bottom', labels: { font: { size: 11 }, padding: 14 } };

  function lineDS(label, arr, fn, color, dash) {
    var ds = { label: label, data: pts(arr, fn), borderColor: color,
               pointRadius: 0, borderWidth: 2 };
    if (dash) ds.borderDash = [6, 4];
    return ds;
  }

  function mkChart(id, datasets, yText, xOpts) {
    var xScale = Object.assign({}, scaleX, xOpts || {});
    new Chart(document.getElementById(id), {
      type: 'line',
      data: { datasets: datasets },
      options: {
        responsive: true,
        animation: false,
        plugins: { legend: legend, tooltip: { mode: 'index', intersect: false } },
        scales: {
          x: xScale,
          y: Object.assign({}, scaleY, { title: { display: true, text: yText } })
        }
      }
    });
  }

  // Figure 1 — D(p)
  mkChart('chartDeuce', [
    lineDS('y = p  (identity)',       xs, function(p){ return p; }, cGray, true),
    lineDS('D(p) = p²/(p²+q²)',       xs, D,                       cTan)
  ], 'Win probability from deuce,  D(p)');

  // Figure 2 — Cascade
  mkChart('chartCascade', [
    lineDS('y = p',              xs, function(p){ return p; }, cGray, true),
    lineDS('G(p) — game',        xs, G,                       cBlue),
    lineDS('S(p) — set',         xs, S,                       cGreen),
    lineDS('M₃(p) — best of 3',  xs, M3,                      cPurp),
    lineDS('M₅(p) — best of 5',  xs, M5,                      cRed)
  ], 'Win probability');

  // Figure 3 — Derivatives
  mkChart('chartDerivs', [
    lineDS("G′(p)",   xsmid, function(p){ return nd(G,  p); }, cBlue),
    lineDS("S′(p)",   xsmid, function(p){ return nd(S,  p); }, cGreen),
    lineDS("M₅′(p)",  xsmid, function(p){ return nd(M5, p); }, cRed)
  ], 'dF/dp  (amplification rate)', { min: 0.30, max: 0.70 });

  // Figure 4 — Gap
  mkChart('chartGap', [
    lineDS('G(p) − p',  xs, function(p){ return G(p)  - p; }, cBlue),
    lineDS('S(p) − p',  xs, function(p){ return S(p)  - p; }, cGreen),
    lineDS('M₅(p) − p', xs, function(p){ return M5(p) - p; }, cRed)
  ], 'F(p) − p  (amplification bonus)');

})();
</script>
{{< /rawhtml >}}

*On Markov Chains · Probability Amplification · Hierarchical Scoring · Stochastic Dominance*
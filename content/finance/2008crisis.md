+++
date = '2026-01-17T16:48:08+01:00'
draft = false
title = '2008: When The World Discovered Gravity Again'
math = true
+++

The 2008 global financial crisis was not “just” a housing bust, nor merely a story of greedy bankers or inattentive regulators. It was a systems failure, a modern credit machine built to look safe in good weather, then revealed to be structurally fragile the moment the climate changed. A long housing boom supplied the fuel; a sprawling securitization pipeline turned local mortgages into global “safe assets”; leverage and short-term funding provided the acceleration; and a set of widely used risk models, especially those underestimating correlated defaults and liquidity risk, helped financial institutions convince themselves that speed was stability. When U.S. house prices stopped rising and mortgage defaults climbed, losses appeared first in the riskiest corners of structured finance, then migrated, through balance sheets, collateral calls, funding markets, and panic, into the core of the global banking system. The result was a sudden stop in credit, a collapse in trade, deep recessions, and a decade-long afterlife of political and institutional change.

### Keywords

Housing bubble; subprime; securitization; MBS; CDO; CDS; leverage; repo; shadow banking; VaR; correlation; contagion; liquidity freeze; Great Recession.

### 1- Why 2008 matters

A healthy financial system does two essential things: **moves savings to productive investment**, and **redistributes risk** from those who can’t bear it to those who can. The trouble is that the same engineering that makes finance efficient also makes it opaque. By the early 2000s, the system had become exceptionally good at slicing, repackaging, and exporting risk, often so effectively that nobody could easily say where the risk finally lived.
For roughly two decades before 2008, many advanced economies experienced relatively stable inflation and fewer severe recessions. This stability encouraged the belief that macroeconomic shocks were tamer and that modern policy tools (especially central banking) could contain crises. In finance, stability has a paradoxical side-effect: it **encourages leverage** because past calm is mistaken for future safety.
Traditional banking is simple to describe: take deposits, make loans, hold capital and liquidity buffers, and accept tight regulation. By 2008, a large share of credit creation had migrated into a parallel universe often called **shadow banking**: broker-dealers, structured investment vehicles (SIVs), money market funds, and securitization conduits that performed bank-like maturity transformation (borrowing short, lending long) without traditional bank safeguards. When confidence is high, shadow banking feels like a miracle of efficiency. When confidence breaks, it can run like a bank, only faster.

### 2- Root causes: the ingredients that made the crisis possible

The crisis begins with a mundane asset: the single-family home. U.S. home prices rose strongly in the early-to-mid 2000s, supported by low interest rates, plentiful credit, and the widespread expectation that house prices “basically always go up.” You don’t need to assume mass delusion to get a bubble, just a feedback loop: 
- Rising prices make lenders feel safer (collateral seems abundant).
- Easier credit increases demand.
- Higher demand pushes prices up again.
Once this loop is socially accepted, underwriting standards tend to loosen because recent performance looks like proof of structural safety.

Now, let's talk about **Subprime Mortgages**.
A subprime mortgage is a loan to a borrower with weaker credit characteristics (lower credit scores, patchier income history, higher existing debt). Subprime lending isn’t inherently evil. The problem in the 2000s was the combination of:
- Aggressive product design (teaser rates, adjustable-rate mortgages that reset upward),
- Weak verification (“low-doc” or “no-doc” loans),
- High loan-to-value ratios (thin borrower equity), and
- A business model that rewarded loan volume more than loan quality.
Think of it like a restaurant that gets paid for serving plates, not for whether customers get food poisoning next week.
Next, here it comes the idea of **Securitization**, turning mortgages into “safe” global assets.
Securitization is the process of pooling loans and selling claims on the pool’s cash flows. The simplest form is a mortgage-backed security (MBS). A more complex layer is a collateralized debt obligation (CDO), often built from slices of many MBS deals.
The crucial innovation was **tranching**, splitting a pool’s cash flows into layers with different priorities. The top layer (senior tranche) gets paid first and is designed to be very safe; the bottom layer (equity tranche) absorbs losses first and is risky.
The narrative pitch was elegant: “If we pool thousands of mortgages across the country, diversify idiosyncratic risk, and structure payments carefully, we can manufacture lots of highly rated bonds.” The Financial Crisis Inquiry Commission (FCIC) later emphasized how these products, combined with failures in governance and oversight, amplified vulnerability.

BUT, when everyone is rational locally and disastrous globally.
A recurring pattern in crises is agency problems: the person making the decision doesn’t bear the full consequence. Mortgage brokers earned fees for origination, not long-term repayment. Then, banks earned fees for packaging and selling securities. Then, rating agencies were paid by issuers whose deals they rated. And last but not least, traders and executives were rewarded for short-run return on equity, which rises mechanically with leverage (until it doesn’t).
Nobody needed to wake up and choose chaos. It was enough that the system paid generously for producing assets that looked safe.

We finally reached the **Leverage** idea, the multiplier that turns a loss into a catastrophe.
Leverage is borrowing to amplify returns. It’s also borrowing to amplify fragility. We’ll formalize this in the next section, but the intuition is immediate:
- A homeowner with a small down payment is leveraged.
- A bank funding long-term assets with short-term borrowing is leveraged.
- A dealer holding securities financed in overnight repo is leveraged and liquidity-sensitive.

There is another crucial point that I want to highlight, **Regulation**. Safe on paper, fragile in practice. It did not keep pace with the evolving system. Banks optimized for regulatory capital rules; activities migrated into less-regulated corners; and models used for risk and capital often assumed liquidity and correlations would remain benign. Basel market-risk frameworks institutionalized Value at Risk (VaR) and backtesting as core tools for market risk capital in large banks, which mattered because model-driven capital can become procyclical, easiest in booms, tightest in stress.

### 3- The mechanics: how the system actually broke

We are now looking inside the bank’s financial body to see the hidden fragility that normal market appearances were masking. Leverage and why small price moves can wipe out equity.

Consider a simplified bank balance sheet:

$$
\text{Assets } (A) = \text{Loans} + \text{Securities} \\
\text{Liabilities } (D) = \text{Short-term funding} + \text{Long-term debt} \\
\text{Equity } (E) = A - D
$$

Define the leverage ratio: $ L = frac{A}{E} $ 

Leverage $L$ tells you how many dollars of assets the bank holds per dollar of equity. If $L=25$, the bank has $25 of assets for every $1 of equity.
Now look at what happens when asset values change. Since $E=A-D$, and debt $D$ is often sticky in the short run, a small drop in $A$ can be a huge percentage drop in $E$:

$$\frac{\Delta E}{E} \approx L \cdot \frac{\Delta A}{A}$$

The percentage hit to equity is roughly leverage times the percentage hit to assets. With $L=25$, a 4% decline in asset value can translate into about a 100% decline in equity. That's insolvency from what looked like "a small market move."

This is the first key mechanism of 2008: **asset risk became solvency risk because leverage was high.**

Now, let's look into the mortgage credit losses, the simplest risk math that everyone quietly tried to ignore.
For any credit exposure, a standard decomposition is:

$$\text{Expected Loss} = PD \times LGD \times EAD$$

* $PD$ = probability of default,
* $LGD$ = loss given default (how much you lose if default happens),
* $EAD$ = exposure at default (how big the loan is when it goes bad).

If underwriting weakens, $PD$ rises. If house prices fall, recoveries fall and $LGD$ rises. In 2008, both moved in the wrong direction at the same time.

How an MBS "waterfall" works: why senior tranches looked safe, until they weren't
Imagine a pool of $N$ mortgages. Let total cash flow from borrowers at time $t$ be:

$$C_t = \sum_{i=1}^{N} \big(\text{interest}_{i,t} + \text{principal}_{i,t}\big) - \text{losses}_t$$

The pool receives interest and principal payments from homeowners; defaults reduce what arrives.

Now split the security into tranches: Senior (S), Mezzanine (M), Equity (E). Losses hit equity first, then mezzanine, then senior.

A stylized loss allocation at time $t$ might look like:

$$\text{Loss}_E(t) = \min(\text{Loss}(t),\,K_E)$$

$$\text{Loss}_M(t) = \min\big(\max(\text{Loss}(t)-K_E,\,0),\,K_M\big)$$

$$\text{Loss}_S(t) = \max(\text{Loss}(t)-K_E-K_M,\,0)$$

Equity absorbs losses up to its thickness $K_E$. If losses exceed that, mezzanine absorbs the next layer $K_M$. Only when losses pierce both cushions does the senior tranche take losses.

So why did seniors get such high ratings? Because if defaults are mostly independent and mild, it's genuinely hard for losses to reach the top. The trap is that defaults are **not** independent in a housing bust—they become correlated through the common factor of falling house prices and tightening refinancing conditions.

A common way to model correlated defaults is a one-factor model:

$$Y_i = \sqrt{\rho}\,Z + \sqrt{1-\rho}\,\varepsilon_i$$

Default occurs if: $Y_i < \Phi^{-1}(p)$
Each borrower's "health" $Y_i$ depends partly on a shared economic factor $Z$ (think: housing market + jobs + credit conditions) and partly on idiosyncratic noise $\varepsilon_i$. The parameter $\rho$ measures how strongly everyone is tied to the same macro factor. If the common factor turns bad, many borrowers weaken together. $\Phi^{-1}(p)$ is just the threshold corresponding to default probability $p$ in a standard normal model.
Here's the uncomfortable fact: **senior tranches are extremely sensitive to tail correlation**. Small underestimates of $\rho$ can turn "almost impossible" senior losses into "suddenly plausible" senior losses. Structured finance wasn't primarily wrong because math exists; it was wrong because the wrong math (and the wrong calibration regime) was treated as certainty.

Let's now look into **VaR and procyclicality**, when “risk management” amplifies risk.
A basic VaR formulation for a portfolio with (approximate) normal returns is:

$$VaR_{\alpha} \approx z_{\alpha}\,\sigma_P \sqrt{h}$$

At confidence level $\alpha$, VaR is "a bad-day loss estimate." $z_{\alpha}$ is a quantile (bigger for 99% than for 95%), $\sigma_P$ is the portfolio's volatility, and $h$ is the horizon (e.g., 1 day).
In a calm boom, $\sigma_P$ is low → VaR looks low → institutions can hold more risk for the same capital constraint. When volatility spikes, VaR jumps → institutions are forced to de-risk (sell assets) into falling markets.
Basel market risk rules embedded VaR and backtesting into capital requirements, including penalty multipliers when models performed poorly.
**Result:** when stress hits, constraints tighten precisely when everyone is least able to adjust smoothly. That's mechanical deleveraging, a core accelerant of 2008.

In the repo market, you borrow cash against securities as collateral. If a security has market value $P$ and the haircut is $h$, the borrowing capacity is:

$$B = (1-h)\,P$$

With a 2% haircut, you can borrow 98% of the collateral value; with a 20% haircut, you can borrow only 80%. If haircuts rise suddenly, your funding evaporates unless you post more collateral or sell assets.
In 2008, haircuts and margin requirements rose rapidly, turning solvency fears into immediate funding crises, even for firms that might have survived in a slower-moving world.

But how fire sales and feedback loops influenced the market, why prices overshoot on the way down?
A simple way to represent market impact is:

$$p = p_0 - \lambda q$$

The more quantity $q$ institutions try to sell, the more price $p$ falls below its pre-stress level $p_0$. The parameter $\lambda$ captures illiquidity.
Combine this with leverage targeting and VaR constraints, and you get a vicious circle: price drops → equity shrinks → leverage rises → forced sales → further price drops.

### From local housing trouble to global catastrophe: the cascade

By 2007, mortgage delinquencies rose and the market began repricing subprime risk. The ABX indices—benchmarks tied to subprime mortgage credit risk—collapsed, reflecting both worsening fundamentals and a sudden premium for illiquidity and fear.
This was the moment the system could have treated structured-credit losses as painful-but-contained. Instead, opacity and leverage transformed repricing into panic.

Bear Stearns was not brought down by a long, slow recognition of insolvency; it was brought down by a rapid loss of funding. The Federal Reserve describes how Bear informed regulators on March 13, 2008 that it expected it could not meet obligations the next day without support.
The Fed and JPMorgan created Maiden Lane structures to facilitate the resolution.
In other words, the system had already entered a phase where confidence, not just fundamental asset values, could decide whether an institution lived or died.

Now comes the moment of truth. Lehman Brothers filed for bankruptcy on **September 15, 2008**, the iconic rupture that convinced markets no one was safely “inside the perimeter.”
AIG (American International Group), heavily exposed through derivatives (including CDS) and facing collateral calls after downgrades, was pushed to the brink at the same time; the New York Fed notes that September 15 downgrades triggered collateral calls AIG could not meet.
Then came a crucial “plumbing” event: the **Reserve Primary Fund**, a money market fund, “broke the buck” (its net asset value fell below $1), catalyzing runs on money funds and intensifying the credit freeze.

During the worst phase, the spread between 3-month LIBOR and OIS (a proxy for bank funding stress and counterparty fear) spiked dramatically, peaking around 360 basis points in mid-October 2008 according to a Federal Reserve bulletin chart narrative.
John Hull’s analysis similarly documents an October 2008 peak around the mid-300s.
Banks didn’t trust other banks. When the institutions that provide short-term credit stop trusting each other, the entire economy starts running out of oxygen.

But why it went global? This crisis spread internationally for three intertwined reasons:
1- **Global distribution of U.S. structured products**. European banks and global investors held large volumes of U.S. mortgage-related securities.
2- **Dollar funding dependence**. Non-U.S. banks often funded dollar assets in short-term dollar markets. When dollar liquidity vanished, the strain went worldwide.
3- **Common risk models and correlated deleveraging**. Many institutions responded similarly—sell, de-risk, hoard liquidity—creating global synchronization in stress.

### Consequences: short-term shocks and long-term structural changes

#### The macro shock: output, jobs, and trade
The crisis produced the Great Recession. The Federal Reserve’s historical summary reports that U.S. real GDP fell **4.3%** from its peak in 2007Q4 to its trough in 2009Q2.
U.S. unemployment reached **10.2%** in October 2009, per the Bureau of Labor Statistics.
Global trade collapsed: the WTO forecast a roughly **9%** decline in world exports in volume terms in 2009 (one of the sharpest contractions in modern history).
These describe a sudden global stop in activity triggered by a seized-up credit system.

#### The financial shock: loss estimates and the scale problem
One reason 2008 was uniquely dangerous is scale. The IMF discussed estimates (from its crisis-era stability work) of very large losses on U.S.-based mortgage-related and other credits, on the order of trillions of dollars.
Once losses reach that magnitude inside leveraged institutions, the question is no longer “Who loses money?” but “Who can fund themselves tomorrow morning?”

#### Political and social aftershocks
Financial crises are not only recessions; they are legitimacy shocks. Bailouts, foreclosures, and unemployment reshaped public trust in institutions. The political consequences differed by country, but a common theme emerged: when the financial system is perceived as protected while households bear losses, social cohesion erodes.

#### Policy and regulation: emergency stabilization, then redesign
In the U.S., the Emergency Economic Stabilization Act establishing TARP became law on October 3, 2008, and the Treasury’s TARP documentation summarizes its role and implementation.
The post-crisis regulatory overhaul included the **Dodd–Frank Act**, signed July 21, 2010, with the Federal Reserve’s historical essay summarizing its aims and architecture.

One of the most sobering findings in post-crisis research is that output losses after major financial crises can be persistent. An IMF working paper<sup>[\*](https://www.imf.org/-/media/files/publications/wp/2019/wpiea2019083.pdf)</sup> reviewing the decade after 2008 emphasizes the durability of output shortfalls and highlights sluggish investment as a key channel.
A financial crisis can permanently bend the economy’s trajectory downward, not just produce a temporary dip.

### Lessons learned

*Leverage turns measurement error into existential risk*
If a system runs at high leverage, it cannot tolerate being “a little wrong” about asset risk. The leverage equation is merciless: small asset declines can erase equity. The practical implication is not “ban leverage,” but design leverage to be robust to stress, with buffers that are meaningful in bad states, not just optimized for good ones.

*Correlation is not a parameter, it’s a regime*
In calm periods, defaults look weakly correlated; in busts, correlations rise because the same macro factor hits everyone. Any framework that prices senior tranches or bank capital on the assumption that yesterday’s correlation is tomorrow’s law will eventually blow up. The policy implication: **stress tests and capital frameworks must target tail regimes**, not only average history.

*Liquidity is a state variable, not a footnote*
The crisis taught (again) that you can be solvent on paper and still fail by Tuesday because funding disappears. Repo haircuts, margin calls, and runs on money-like instruments are not secondary—they are the transmission mechanism. The result: **liquidity regulation, stable funding, and credible lender-of-last-resort backstops matter as much as capital.**

*“Market discipline” fails when markets can’t see*
Market discipline requires transparency. In 2008, structured products and counterparty exposures were too opaque; investors responded rationally by pulling back from everything. When nobody can distinguish healthy from unhealthy, the run becomes indiscriminate.

*Incentives create the crisis before the crisis arrives*
If you pay people for volume, they will produce volume. If you pay for short-term ROE, they will increase leverage. If rating agencies are paid by issuers, ratings will drift toward what issuers want—especially in booms. The implication: risk retention (“skin in the game”), **compensation reform, and governance that punishes tail-risk loading are not moral add-ons; they are systemic safeguards.**

*Macroprudential policy is not optional in a credit economy*
2008 made a strong case that supervising individual institutions is insufficient if the system can migrate risk into unregulated channels. The corollary: regulators need tools that target system-wide leverage, maturity mismatch, and interconnectedness, including outside traditional banks.

*Crisis response must be fast—but legitimacy must be protected*
In acute panic, speed matters, stop the run, stabilize funding, prevent a collapse of payments and credit. But legitimacy matters too, if crisis policy is perceived as protecting the system while ignoring households, the political aftershocks become part of the damage. What this reveals; resolution regimes, clear bailout rules, and household-side stabilization (unemployment insurance, mortgage relief mechanisms) are part of financial stability.

### Closing thought: Gravity, rebuilt

2008 was finance’s reminder that you can’t repeal gravity, you can merely engineer around it. For years, rising house prices, cheap short-term funding, and models calibrated to calm markets made risk feel weightless. Leverage let institutions fly higher on thinner equity, and securitization made fragile loans look like sturdy “safe assets.”
Then housing turned, correlations jumped, liquidity vanished, and the system discovered what gravity looks like in markets; margin calls, forced selling, runs, and rapid contagion. The crash wasn’t a surprise force, it was the moment the invisible constraint became visible motion.

The lesson isn’t “never fly.” It’s to build a system that can fly without pretending it will never fall: more real buffers, less dependence on fragile funding, and risk models that respect bad regimes
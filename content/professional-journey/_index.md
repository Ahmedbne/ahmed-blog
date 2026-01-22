+++
date = '2026-01-10T14:45:40+01:00'
draft = false
title = 'The Journey'
description = 'Passionate about finance and randomness, about that subtle dialogue between chance and decision, trained in modeling, theory, and scientific computation, with a strong desire to understand and structure the uncertainty of the real world.'
+++

<style>
.journey-intro {
  text-align: center;
  margin: 2rem 0 4rem 0;
  padding: 2rem;
  border-left: 3px solid var(--secondary);
  border-right: 3px solid var(--secondary);
}

.journey-intro blockquote {
  font-size: 1.3rem;
  font-style: italic;
  color: var(--secondary);
  margin: 0;
  border: none;
  padding: 0;
}

.timeline {
  position: relative;
  max-width: 900px;
  margin: 0 auto;
  padding: 2rem 0;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 2px;
  height: 100%;
  background: linear-gradient(to bottom, var(--secondary) 0%, var(--primary) 50%, var(--secondary) 100%);
}

.timeline-item {
  position: relative;
  margin: 3rem 0;
  padding: 0 2rem;
}

.timeline-item::before {
  content: '';
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 16px;
  height: 16px;
  background: var(--theme);
  border: 3px solid var(--primary);
  border-radius: 50%;
  z-index: 1;
}

.timeline-item:nth-child(odd) .timeline-content {
  margin-right: 52%;
  text-align: right;
}

.timeline-item:nth-child(even) .timeline-content {
  margin-left: 52%;
  text-align: left;
}

.timeline-content {
  background: var(--code-bg);
  padding: 1.5rem;
  border-radius: 8px;
  border: 1px solid var(--border);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.timeline-content:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(0,0,0,0.15);
}

.timeline-date {
  font-size: 0.85rem;
  color: var(--secondary);
  margin-bottom: 0.5rem;
  font-family: 'JetBrains Mono', monospace;
}

.timeline-title {
  font-size: 1.2rem;
  font-weight: 600;
  color: var(--primary);
  margin-bottom: 0.3rem;
}

.timeline-org {
  font-size: 0.95rem;
  color: var(--secondary);
  font-style: italic;
  margin-bottom: 0.8rem;
}

.timeline-desc {
  font-size: 0.9rem;
  line-height: 1.6;
  color: var(--content);
}

.timeline-tags {
  margin-top: 0.8rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  justify-content: flex-end;
}

.timeline-item:nth-child(even) .timeline-tags {
  justify-content: flex-start;
}

.timeline-tag {
  font-size: 0.75rem;
  padding: 0.2rem 0.6rem;
  background: rgba(255,255,255,0.05);
  border: 1px solid var(--border);
  border-radius: 12px;
  color: var(--secondary);
}

.chapter-marker {
  text-align: center;
  margin: 4rem 0;
  position: relative;
}

.chapter-marker h2 {
  display: inline-block;
  background: var(--theme);
  padding: 0.5rem 2rem;
  font-size: 1rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--secondary);
  border: 1px solid var(--border);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  margin: 2rem 0;
}

.skill-card {
  background: var(--code-bg);
  padding: 1.5rem;
  border-radius: 8px;
  border: 1px solid var(--border);
  text-align: center;
}

.skill-card h4 {
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--secondary);
  margin-bottom: 0.8rem;
}

.skill-card p {
  font-size: 0.9rem;
  line-height: 1.5;
  margin: 0;
}

.contact-section {
  text-align: center;
  margin: 4rem 0 2rem 0;
  padding: 2rem;
  border-top: 1px solid var(--border);
}

.contact-section h3 {
  font-size: 1.1rem;
  margin-bottom: 1rem;
  color: var(--secondary);
}

.contact-links {
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
}

.contact-links a {
  color: var(--primary);
  text-decoration: none;
  font-size: 0.9rem;
  transition: opacity 0.2s;
}

.contact-links a:hover {
  opacity: 0.7;
}

@media (max-width: 768px) {
  .timeline::before {
    left: 20px;
  }
  
  .timeline-item::before {
    left: 20px;
  }
  
  .timeline-item:nth-child(odd) .timeline-content,
  .timeline-item:nth-child(even) .timeline-content {
    margin-left: 50px;
    margin-right: 0;
    text-align: left;
  }
  
  .timeline-item:nth-child(odd) .timeline-tags,
  .timeline-item:nth-child(even) .timeline-tags {
    justify-content: flex-start;
  }
}
</style>

<div class="journey-intro">
<blockquote>
"The purpose of computing is insight, not numbers."<br>
<span style="font-size: 0.9rem;">— Richard Hamming</span>
</blockquote>
</div>

---

## ∴ Who I Am

I'm **Ahmed Bounadar** — a financial engineering student based in Casablanca, Morocco. My work lives at the intersection of **mathematics**, **economics**, and **computational methods**. I'm drawn to problems where rigorous thinking meets real-world uncertainty: pricing derivatives, modeling credit risk, understanding how markets breathe.

This page is less a résumé and more a map of how I got here — the experiences that shaped my thinking, and the questions I'm still chasing.

---

<div class="chapter-marker">
<h2>Chapter I — The Foundation</h2>
</div>

<div class="timeline">

<div class="timeline-item">
<div class="timeline-content">
<div class="timeline-date">Sep 2021 → Aug 2023</div>
<div class="timeline-title">Preparatory Classes (CPGE)</div>
<div class="timeline-org">Mathematics & Physics Track · Kenitra</div>
<div class="timeline-desc">
Two years of intensive mathematical training — the French system's trial by fire. Analysis, algebra, probability, physics. This is where I learned that struggle is the texture of understanding. Every theorem earned, not given.
</div>
<div class="timeline-tags">
<span class="timeline-tag">Analysis</span>
<span class="timeline-tag">Algebra</span>
<span class="timeline-tag">Probability</span>
</div>
</div>
</div>

<div class="timeline-item">
<div class="timeline-content">
<div class="timeline-date">Sep 2023 → Present</div>
<div class="timeline-title">Master of Engineering</div>
<div class="timeline-org">École Centrale Casablanca · CentraleSupélec Group</div>
<div class="timeline-desc">
Data Science specialization, but my heart pulled toward finance. Courses in stochastic processes, optimization, time series, partial differential equations — the language of modern quantitative finance. Here I learned to see markets as dynamical systems, risk as a measurable quantity.
</div>
<div class="timeline-tags">
<span class="timeline-tag">Stochastic Processes</span>
<span class="timeline-tag">Optimization</span>
<span class="timeline-tag">Time Series</span>
<span class="timeline-tag">PDEs</span>
</div>
</div>
</div>

</div>

<div class="chapter-marker">
<h2>Chapter II — Into the Markets</h2>
</div>

<div class="timeline">

<div class="timeline-item">
<div class="timeline-content">
<div class="timeline-date">Jul 2024 → Sep 2024</div>
<div class="timeline-title">Risk Quant Analyst</div>
<div class="timeline-org">Attijariwafa Bank · Casablanca</div>
<div class="timeline-desc">
My first real encounter with operational risk. I built an <strong>Advanced Measurement Approach (AMA)</strong> framework — calibrating frequency-severity models (Poisson, Negative Binomial, Log-normal, Pareto), running Monte Carlo simulations, stress testing tail scenarios. The math became real when it touched capital requirements.
</div>
<div class="timeline-tags">
<span class="timeline-tag">Operational Risk</span>
<span class="timeline-tag">Monte Carlo</span>
<span class="timeline-tag">AMA</span>
<span class="timeline-tag">Stress Testing</span>
</div>
</div>
</div>

<div class="timeline-item">
<div class="timeline-content">
<div class="timeline-date">May 2025 → Aug 2025</div>
<div class="timeline-title">Quantitative Economist</div>
<div class="timeline-org">BMCE Capital · Bank of Africa</div>
<div class="timeline-desc">
Fixed income became my obsession. I built <strong>Nelson-Siegel yield curve models</strong>, bootstrapped discount curves, and applied VAR/VECM factor models to forecast term structure dynamics. The elegance of seeing level, slope, and curvature as tradeable factors — that changed how I see bond markets.
</div>
<div class="timeline-tags">
<span class="timeline-tag">Yield Curves</span>
<span class="timeline-tag">Nelson-Siegel</span>
<span class="timeline-tag">VAR/VECM</span>
<span class="timeline-tag">Fixed Income</span>
</div>
</div>
</div>

<div class="timeline-item">
<div class="timeline-content">
<div class="timeline-date">Sep 2025 → Present</div>
<div class="timeline-title">Market Data Analyst</div>
<div class="timeline-org">Société Générale · Corporate & Investment Banking</div>
<div class="timeline-desc">
Working at the intersection of data infrastructure and quantitative research. I develop and validate market time series — rates, indices, FX, commodities — ensuring the numbers that feed pricing models and structuring desks are clean, consistent, and trustworthy. Global coordination across US, Asia, and Europe taught me that markets never sleep.
</div>
<div class="timeline-tags">
<span class="timeline-tag">Market Data</span>
<span class="timeline-tag">Data Quality</span>
<span class="timeline-tag">Global Markets</span>
<span class="timeline-tag">CIB</span>
</div>
</div>
</div>

</div>

<div class="chapter-marker">
<h2>Chapter III — Research & Projects</h2>
</div>

<div class="timeline">

<div class="timeline-item">
<div class="timeline-content">
<div class="timeline-date">Research Project</div>
<div class="timeline-title">Pandemic Impact & Species Competition</div>
<div class="timeline-org">Centrale Casablanca Research Center</div>
<div class="timeline-desc">
Generalized Lotka-Volterra models applied to pandemic dynamics. Simulations of inter-species competition, statistical analysis of emergent behaviors. A reminder that the mathematics of finance — systems, feedback, contagion — echoes everywhere.
</div>
<div class="timeline-tags">
<span class="timeline-tag">Dynamical Systems</span>
<span class="timeline-tag">Simulation</span>
<span class="timeline-tag">Complex Systems</span>
</div>
</div>
</div>

<div class="timeline-item">
<div class="timeline-content">
<div class="timeline-date">Coding Project</div>
<div class="timeline-title">Credit Default Prediction</div>
<div class="timeline-org">Centrale Casablanca</div>
<div class="timeline-desc">
Built a mathematical framework connecting stochastic processes to credit default. Modeled default probability as a random variable with time-dependent dynamics, studied convergence of estimators under noise, and linked ML methods (regression, random forests) to asymptotic statistics. Theory meeting practice.
</div>
<div class="timeline-tags">
<span class="timeline-tag">Credit Risk</span>
<span class="timeline-tag">Stochastic Modeling</span>
<span class="timeline-tag">Machine Learning</span>
</div>
</div>
</div>

</div>

---

## ∴ The Toolkit

<div class="skills-grid">

<div class="skill-card">
<h4>Languages</h4>
<p>Python · C++ · R · SQL</p>
</div>

<div class="skill-card">
<h4>Quantitative</h4>
<p>Time Series · Stochastic Calculus · Risk Models · Econometrics</p>
</div>

<div class="skill-card">
<h4>Libraries</h4>
<p>Pandas · NumPy · Scikit-learn · Statsmodels · XGBoost</p>
</div>

<div class="skill-card">
<h4>Human</h4>
<p>English (Fluent) · French (Fluent) · Arabic (Native)</p>
</div>

</div>

---

## ∴ What's Next

I'm currently in my **professional gap year**, seeking a second six-month internship to deepen my expertise in quantitative finance — whether in derivatives pricing, risk management, or systematic strategies. I want to be where mathematics meets markets, where models meet reality.

If you're working on interesting problems in this space, I'd love to connect.

<div class="contact-section">
<h3>Let's Talk</h3>
<div class="contact-links">
<a href="mailto:ahmed.bounadar@centrale-casablanca.ma">📧 ahmed.bounadar@centrale-casablanca.ma</a>
<a href="https://linkedin.com/in/ahmed-bounadar" target="_blank">💼 LinkedIn</a>
<a href="tel:+212659839054">📱 +212 659 839 054</a>
</div>
</div>

---

<p style="text-align: center; color: var(--secondary); font-style: italic; margin-top: 3rem;">
"The market is a device for transferring money from the impatient to the patient."<br>
— Warren Buffett
</p>
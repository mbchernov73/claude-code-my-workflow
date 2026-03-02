---
paths:
  - "scripts/**/*.R"
  - "explorations/**"
  - "papers/**"
---

# Research Knowledge Base: MPidentification

## Notation Registry

| Rule | Convention | Example | Anti-Pattern |
|------|-----------|---------|-------------|
| State vector | Lowercase bold $\mathbf{x}_t$ | $\mathbf{x}_t = (s_t, \pi_t, g_t, \dots)'$ | Using $X_t$ (uppercase for state) |
| Dynamics matrix | Uppercase $A$ | $\mathbf{x}_{t+1} = A \mathbf{x}_t + B \varepsilon_{t+1}$ | Using $\Phi$ without definition |
| Shock loadings | Uppercase $B$ | $B \varepsilon_{t+1}$ | Mixing $B$ and $\Sigma$ roles |
| Risk prices | Lowercase $\lambda_t$ | $\lambda_t = \lambda_0 + \lambda_1 \mathbf{x}_t$ | Using $\Lambda$ for time-varying prices |
| Taylor rule params | $\tau_\pi$, $\tau_g$ | $i_t = \tau_0 + \tau_\pi \pi_t + \tau_g g_t + s_t$ | Using $\phi_\pi$, $\phi_g$ without noting BCZZ convention |
| Discretion | $s_t$ | Taylor rule residual | Calling it "monetary policy shock" without qualification |
| Factor loadings | $d$ | Yield loadings on state | Using $b$ (conflicts with shock loadings $B$) |
| Pricing kernel | $M_{t+1}$ or $m_{t+1} = \log M_{t+1}$ | $M_{t+1} = \exp(m_{t+1})$ | Mixing log and level notation |
| Risk-neutral dynamics | Superscript $\mathbb{Q}$ | $A^{\mathbb{Q}}$, $\delta_1^{\mathbb{Q}}$ | Using tildes $\tilde{A}$ |
| Yield maturity | Subscript $n$ | $y_t^{(n)}$ for $n$-period yield | Using $\tau$ for maturity (conflicts with Taylor params) |

## Symbol Reference

| Symbol | Meaning | Source |
|--------|---------|-------|
| $\mathbf{x}_t$ | State vector | BCZZ eq. system |
| $A$, $B$ | VAR dynamics and shock loadings | BCZZ state-space |
| $\lambda_0$, $\lambda_1$ | Constant and state-dependent risk prices | Affine SDF |
| $\tau_\pi$, $\tau_g$ | Taylor rule response to inflation, output gap | BCZZ identification |
| $s_t$ | Discretionary component of monetary policy | BCZZ Taylor rule |
| $d_n$ | Yield factor loadings (maturity $n$) | Affine pricing |
| $A_n$, $B_n$ | Affine yield recursion coefficients | Duffie-Kan (1996) |
| $M_{t+1}$ | Stochastic discount factor (pricing kernel) | General asset pricing |
| $\varepsilon_t$ | Structural shocks | BCZZ identification |
| $y_t^{(n)}$ | $n$-period zero-coupon yield | Data / model |
| $\text{tp}_t^{(n)}$ | Term premium on $n$-period bond | Decomposition |

## Argument Progression

| # | Section | Core Question | Key Notation | Key Method |
|---|---------|--------------|-------------|------------|
| 1 | BCZZ Setup | How does BCZZ identify monetary policy shocks? | $A$, $B$, $\tau_\pi$, $\tau_g$, $s_t$ | Taylor rule restrictions in affine model |
| 2 | CK Critique | Why does CK claim LRN is violated? | LRN conditions, permanent component | Non-parametric LRN test |
| 3 | Counter: Scope | Does CK's critique apply to BCZZ's specific structure? | iid discretion $s_t$ | Structural vs. reduced-form identification |
| 4 | Counter: Robustness | Are BCZZ results robust to relaxing LRN? | Partial LRN, bounded departures | Sensitivity analysis |
| 5 | Counter: Empirical | Does the data support BCZZ or CK? | Sample periods, UMP | Re-estimation, subsample analysis |

## Empirical Applications

| Application | Paper | Dataset | Context | Purpose |
|------------|-------|---------|---------|---------|
| Taylor rule estimation | BCZZ (2022) | Treasury yields + macro | Full sample | Original identification |
| LRN violation test | CK (2026) | Similar yield data | UMP period emphasis | Critique basis |
| Subsample robustness | Response | Pre/post-ZLB yields | Split samples | Test CK claim |
| GMM re-estimation | Response | BCZZ replication data | Full + subsamples | Verify identification stability |

## Design Principles

| Principle | Evidence | Applied In |
|-----------|----------|-----------|
| Structural identification requires parametric restrictions | BCZZ Taylor rule structure | Sections 1-2 |
| Non-parametric tests have different null than parametric models | CK tests generic LRN, not BCZZ-specific LRN | Section 3 |
| UMP period is structurally different, not just "more data" | ZLB/QE change transmission mechanism | Section 5 |

## Anti-Patterns (Don't Do This)

| Anti-Pattern | What Happened | Correction |
|-------------|---------------|-----------|
| Treating LRN as binary (holds/fails) | Ignores partial violations and economic significance | Quantify departure magnitude and impact on estimates |
| Conflating CK's generic LRN with BCZZ's specific structure | Different identifying assumptions | Clearly distinguish what each paper assumes |
| Ignoring sample period sensitivity | Pre-2008 vs full sample may differ | Always report subsample results |
| Mixing annualized and per-period yields | Factor of ~12 or ~4 errors | State convention explicitly, verify units |

## Analytical Pitfalls

| Pitfall | Impact | Prevention |
|---------|--------|------------|
| Eigenvalue ordering in companion matrix | Wrong impulse responses, explosive dynamics | Verify all eigenvalues inside unit circle; sort by modulus |
| GMM weighting matrix sensitivity | Estimates vary with W choice | Report identity W and optimal W; check sensitivity |
| Yield convention (annualized vs. per-period) | Off by factor of 12 (monthly) or 4 (quarterly) | State convention in every table/figure |
| Mixing $\mathbb{P}$ and $\mathbb{Q}$ dynamics | Risk prices absorbed into wrong measure | Label every equation with measure |
| Confusing reduced-form and structural shocks | Identification breaks down | Clearly state rotation/ordering at each step |
| Ignoring Jensen's inequality in log yields | Bias in affine pricing | Include convexity adjustment $-\frac{1}{2} B_n' \Sigma B_n / n$ |

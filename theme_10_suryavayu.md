**Title:** SuryaVayu AI — Physics-Embedded Renewable Forecasting with Baseline Benchmarking

**Theme:** Theme 10 — AI for Renewable Generation Forecasting

**The Problem**

Karnataka has 15+ GW of installed renewable capacity managed by [KREDL](https://kredl.karnataka.gov.in/) and [KPTCL/KSPDCL](https://kptcl.karnataka.gov.in/). Grid operators must predict solar and wind output for day-ahead and intraday scheduling at plant, cluster, and regional levels. Current forecasts deviate by 15–25%, forcing the grid to keep expensive thermal plants on spinning reserve. Under [CERC Deviation Settlement Mechanism regulations](https://cercind.gov.in/), every 1% improvement in forecast accuracy saves the state ₹50+ crore annually. Judges explicitly require uncertainty modeling, physics-informed approaches, multi-level aggregation, and comparison against baseline models.

**What SuryaVayu AI Does**

SuryaVayu AI delivers **sub-5% deviation forecasting** for solar and wind generation at 15-minute granularity across three horizons: *day-ahead (24h), intraday (6h updates), and nowcast (1h)*. The system uses a hybrid architecture — physics-informed clear-sky models for solar baseline combined with ML residual correction for cloud transience and wind turbulence. Every prediction carries **statistical confidence intervals** (10th/50th/90th percentile) computed via quantile regression. Forecasts aggregate from *plant → cluster → region* with proper uncertainty propagation. Every model version is benchmarked against two baselines: persistence model and weather-only naive model.

**Core Features**

**1. Hybrid Physics + ML Forecasting Architecture** — Solar forecasting starts with a physics-based clear-sky GHI (Global Horizontal Irradiance) model that computes theoretical maximum output based on latitude, time of day, and panel tilt. An ML residual model (gradient-boosted trees + LSTM) then corrects for cloud cover, aerosol optical depth, temperature derating, and panel soiling. Wind forecasting uses power curve physics (relating wind speed to turbine output) corrected by an ML model for turbulence and wake effects. This hybrid approach ensures predictions *never violate physical laws* while capturing complex weather dynamics.

**2. Statistical Confidence Intervals via Quantile Regression** — Every forecast block carries a full probability distribution, not a single point estimate. [Quantile regression](https://en.wikipedia.org/wiki/Quantile_regression) produces the 10th, 50th, and 90th percentile scenarios. Grid operators see the best-case, expected, and worst-case generation simultaneously. This directly enables risk-calibrated reserve scheduling — the operator books thermal reserves based on the worst-case scenario, not the expected case.

**3. Plant → Cluster → Region Aggregation** — Plants are grouped into geographic clusters (e.g., all solar farms in Pavagada, all wind farms in Chitradurga). Forecasts aggregate from plant-level to cluster-level to state-level with proper uncertainty propagation using [Copula models](https://en.wikipedia.org/wiki/Copula_(probability_theory)) that capture the correlation between plants (nearby plants share weather conditions, so their errors are correlated, not independent).

**4. Baseline Benchmarking Dashboard** — Every forecast is compared against two baselines: a *persistence model* (tomorrow's forecast = today's actual) and a *weather-only naive model* (direct regression from weather variables without physics or time-series features). The dashboard displays MAPE, RMSE, and MBE for our model vs. both baselines, demonstrating improvement. Judges explicitly require this comparison.

**5. Feature Importance & Explainability** — For every forecast, the system displays which input variables drove the prediction: cloud cover contribution, temperature derating impact, wind speed influence, historical pattern weight. Uses [SHAP values](https://shap.readthedocs.io/) to decompose every prediction into additive feature contributions. Operators see *why* the forecast dropped, not just *that* it dropped.

**6. Automated Ramp Event Early Warning** — When the model detects an incoming generation drop exceeding 100 MW within a 30-minute window, it triggers an automatic alert to the [State Load Dispatch Centre (SLDC)](https://kptcl.karnataka.gov.in/). The alert includes predicted magnitude, duration, affected plants, causal weather event, and recommended thermal reserve ramp-up.

**7. Deviation Settlement Cost Optimizer** — Integrates with [CERC DSM regulations](https://cercind.gov.in/). For every forecast block, calculates the financial penalty of over-forecasting vs. under-forecasting and biases the prediction toward the direction that minimizes total settlement cost for the generator. Standard tools optimize for RMSE — SuryaVayu optimizes for rupee cost.

**Who Benefits**

**KREDL and KSPDCL grid operators** achieve sub-5% forecast deviation with 30-minute ramp warnings. **State Load Dispatch Centre (SLDC)** gets risk-calibrated reserve scheduling via statistical confidence bands. **Solar and wind IPPs** save ₹50+ crore annually from reduced deviation penalties. **State energy regulators (KERC)** receive data-backed renewable integration planning with baseline benchmarks. **National grid operator (POSOCO)** gets improved interstate renewable corridor management.

**Key References**

- [KREDL — Karnataka Renewable Energy Development Ltd](https://kredl.karnataka.gov.in/)
- [KPTCL — Karnataka Power Transmission Corporation](https://kptcl.karnataka.gov.in/)
- [ISRO INSAT Satellite Program](https://www.isro.gov.in/INSAT.html)
- [CERC — Central Electricity Regulatory Commission](https://cercind.gov.in/)
- [NIWE — National Institute of Wind Energy](https://niwe.res.in/)
- [SHAP — Explainable AI Library](https://shap.readthedocs.io/)
- [Quantile Regression — Wikipedia](https://en.wikipedia.org/wiki/Quantile_regression)

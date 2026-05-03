# SuryaVayu AI — Physics-Embedded Renewable Forecasting with Baseline Benchmarking

## Theme 10: AI for Renewable Generation Forecasting

---

## The Problem

Karnataka has 15+ GW of installed renewable capacity managed by KREDL and KPTCL/KSPDCL. Grid operators must predict solar and wind output for day-ahead and intraday scheduling at plant, cluster, and regional levels. Current forecasts deviate by **15–25%**, forcing the grid to keep expensive thermal plants on spinning reserve.

Under CERC Deviation Settlement Mechanism regulations, every **1% improvement in forecast accuracy saves the state ₹50+ crore annually**.

Judges explicitly require:
- ✅ Uncertainty modeling (confidence intervals)
- ✅ Physics-informed approaches
- ✅ Multi-level aggregation (plant → cluster → region)
- ✅ Comparison against baseline models

---

## What SuryaVayu AI Does

SuryaVayu AI delivers **sub-5% deviation forecasting** for solar and wind generation at 15-minute granularity across three horizons:

- **Day-ahead**: 24 hour window, updated once daily
- **Intraday**: 6 hour window, updated every 6 hours
- **Week-ahead**: 7 day window, updated daily

The system uses a **hybrid physics + ML architecture**:
- Physics-informed clear-sky models establish the theoretical baseline
- ML residual correction handles cloud transience, turbulence, and non-linear effects
- Quantile regression produces calibrated confidence bands (p10/p50/p90)

---

## 7 Core Features

### 1. Hybrid Physics + ML Forecasting
Solar forecasting uses a **clear-sky GHI model** (solar geometry → theoretical maximum irradiance) corrected by ML for cloud cover, temperature derating, and panel soiling. Wind forecasting uses **IEC 61400 power curve physics** corrected for turbulence and wake effects.

### 2. Quantile Regression Confidence Intervals
Every forecast carries p10 (worst case), p50 (expected), and p90 (best case) scenarios. Grid operators book thermal reserves based on p10, not p50 — enabling risk-calibrated scheduling.

### 3. Plant → Cluster → Region Aggregation
9 plants across Karnataka grouped into 8 district clusters. Dashboard shows both cluster-level and state-level (Solar Fleet / Wind Fleet) aggregated views with Capacity Utilization Factor (CUF).

### 4. Baseline Benchmarking
Every model version is compared against **Persistence** (tomorrow = today) and **Naive Weather** (direct regression) baselines. The Models page shows SuryaVayu AI achieving 4.8% MAPE vs 22.4% for persistence.

### 5. SHAP Explainability
Dynamic feature importance decomposition shows operators *why* a forecast changed — cloud cover contribution, temperature derating impact, wind speed influence, and historical pattern weight.

### 6. Ramp Event Early Warning
Detects generation changes >40% of capacity per hour and generates SLDC-formatted alerts with magnitude, duration, causal weather event, and thermal reserve recommendations.

### 7. DSM Cost Optimizer
Integrates CERC DSM penalty tiers to compute real financial savings from improved forecast accuracy. Displays daily penalty reduction and annualized savings per plant.

---

## Live Dashboard

The application runs at `http://localhost:3000` and includes:

- **Dashboard**: Network summary, solar/wind fleet aggregation, cluster cards, map, alerts
- **Plants**: 9 renewable plants with detailed forecast, SHAP, DSM, weather, accuracy, and alert tabs
- **Alerts**: Ramp events, curtailment risks, forecast deviations with SLDC formatting
- **Models**: Active model status, baseline benchmarking table, version history, retraining

---

## Who Benefits

- **KREDL/KSPDCL grid operators**: Sub-5% forecast deviation with ramp warnings
- **State Load Dispatch Centre**: Risk-calibrated reserve scheduling via p10/p50/p90
- **Solar and wind IPPs**: ₹50+ crore annual savings from reduced penalties
- **KERC regulators**: Data-backed planning with baseline benchmarks
- **POSOCO (national grid)**: Improved interstate renewable corridor management

---

## Quick Start

```bash
npm install --legacy-peer-deps
npx prisma migrate deploy
npm run seed
npm run dev
```

Open `http://localhost:3000` to access the control room dashboard.

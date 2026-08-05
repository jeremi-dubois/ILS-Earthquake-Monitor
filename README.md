# ILS Earthquake Monitor

Real-time earthquake monitoring and ILS portfolio impact assessment pipeline.

## What it does
- Monitors M≥5 seismic activity in real time across 5 ILS zones (USGS API)
- Estimates industry insured loss distribution using log-linear regression + GEV residuals
- Assesses breach probability and portfolio impact on simulated cat bonds

## Notebooks
- `calibration.ipynb` — Model calibration on EM-DAT historical data (2000-2024)
- `portfolio_impact.ipynb` — Real-time USGS monitoring + portfolio impact assessment

## Key result
Japan M6.8 Kumamoto (28 July 2026): p90 = $4.3bn consistent with
Verisk estimate ($1.4-2.1bn) and Euler estimate ($3-4.5bn).
Bond A ($2bn attachment): 21% breach probability.

## Data sources
- Real-time: USGS Earthquake API (public, free)
- Calibration: EM-DAT 2000-2024 (registration required at emdat.be)

## Methodology
Log-linear regression: log10(loss) ~ magnitude + log10(penetration)
GEV residuals selected over Normal by AIC (xi=0.458, Fréchet domain)
Covers industry loss triggers (~18.8% of cat bond market, Artemis 2025)

## Limitations
- Industry loss triggers only (18.8% of market)
- 76 calibration observations
- Indemnity triggers require RMS/AIR proprietary models

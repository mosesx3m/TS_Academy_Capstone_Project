# TS_Academy_Capstone_Project
## 🇳🇬 Food Basket Price & Food Inflation Forecasting
### TS Academy — Track 3: Time Series Analysis | Capstone Project

---

## Project Overview

Nigeria has experienced severe food price inflation over the past decade, with conditions worsening significantly following the removal of the fuel subsidy in May 2023. This capstone project builds a **time series forecasting system** for two critical economic indicators:

- **Basket Price** — a weighted composite of 14 staple food commodities reflecting the real cost of a typical Nigerian household's monthly food spend
- **CPI Food** — the official Consumer Price Index for food, as published by the National Bureau of Statistics (NBS)

By modelling both indicators simultaneously and linking them through a **cascade forecasting architecture**, we produce 6-month ahead forecasts that can inform household planning, policy decisions, and economic analysis.

---

## Problem Statement

Food affordability is one of the most pressing economic challenges facing Nigerian households today. Between 2022 and 2024, food prices surged by over 80% in nominal terms, driven by:

- The removal of the petrol subsidy in June 2023, which caused immediate and severe cost-of-living shocks
- Persistent naira depreciation against the US dollar, raising the cost of imported food and inputs
- Supply chain disruptions and structural inefficiencies in local food markets

Despite the severity of the crisis, reliable short-term forecasts for food prices remain scarce. Existing tools either rely on lagged official data or fail to account for structural breaks caused by policy changes.

This project addresses that gap by developing **data-driven time series models** that:

1. Explicitly model the 2023 structural break using shock dummy variables
2. Incorporate macroeconomic drivers (fuel price, exchange rate) as exogenous regressors
3. Validate a linked architecture where basket price forecasts improve CPI food predictions
4. Quantify forecast uncertainty through GARCH volatility modelling

---

## Project Objectives

- Achieve a **Mean Absolute Percentage Error (MAPE) below 5%** on both target variables
- Identify and account for the **structural break** caused by the 2023 fuel subsidy removal
- Build a **reproducible, modular forecasting pipeline** split across team notebooks
- Generate **6-month forward forecasts** (November 2025 – April 2026) for both targets
- Demonstrate the value of **linked modelling** — using basket price to improve CPI food predictions

---

## Dataset

| Detail | Description |
|--------|-------------|
| **Source** | `Inflation_data.csv`, `PMS_Price.csv`, `Exchange_rate.csv`, `Selected_food_price.csv` (all available in this repository) |
| **Coverage** | January 2017 – January 2026 (monthly frequency) |
| **Key variables** | Basket commodity prices (eggs, beans, bread, chicken, garri, maize, onions, palm oil, rice, tomatoes, vegetable oil, yam, sweet potato), CPI Food, CPI All Items, fuel price (PMS), exchange rate (NGN/USD) |
| **Frequency** | Monthly (`ME` — month-end) |
| **Missing values** | Handled via time-series interpolation |

### Basket Price Formula
The basket price is a **weighted sum** of 14 commodities, reflecting typical Nigerian household consumption quantities:
```python
basket_price = eggs + 3×beans + 4×bread + 2×chicken + 4×garri + 2×maize
             + onions + 2×palm_oil + 3×rice_local + 3×rice_imported
             + 3×tomatoes + 2×vegetable_oil + 2×yam + 3×sweet_potato
```


### Contributors
|Name|Email| Github Link|
|---|---|---|
|1. Ojumoola Paul|ojumoolatimi@gmail.com|https://github.com/ojumoolatimi |
|2. JOHN MERCY OMETERE| princessade463@gmail.com|https://github.com/MercyJ01 |
|3. Abdulmalik Abdulrashid|abdulmalikabdulrashid1@gmail.com|https://github.com/Abd00lmalik |
|4. Chinecherem Victoria Isaac|chinecheremisaac25@gmail.com| |
|5. Fayemi Anthony Olatokunbo|tonitokunbo@gmail.com|https://github.com/tonitokunbo |
|6. Agunbiade Simbiat Mogbonjubola| mogbonjubola1999@gmail.com|https://github.com/simbiatagunbiade |
|7. Abeeb Olasupo| olasupohabeeb219@gmail.com|https://github.com/habeeb-szn |
|8. Ademola Adeyemi| Ademolaadeyemi719@gmail.com|https://github.com/Demola111 |
|9. Odukaiye Moses| mosesx3m0@gmail.com|https://github.com/mosesx3m |
|10. Orinya Samuel Obande| samuelorinys7@gmail.com|https://github.com/Phanerusis |
|11. Olayinka Yusuf| yusufolayinka92@gmail.com|https://github.com/Sahdam |
|12. Maria Ebimo Ebiakofa| Mariaebimo@gmail.com|https://github.com/Mia-Ebimo |
|13. Sopuruchi | | sopuruchilizbeth@gmail.com|

---

## Team & Role Assignments

> **Team Lead** participates in and oversees all sections of the project.

| Role | Section | Notebook | Team Members |
|------|---------|----------|--------------|
| **Team Lead** | All sections | All notebooks | Team Lead *Olayinka Yusuf* |
| **Team A** | Exploratory Data Analysis |`00_data_preprocessing_eda.ipynb` | Agunbiade Simbiat Mogbonjubola, Abeeb Olasupo, Chinecherem Victoria Isaac |
| **Team B** | Stationarity & ACF/PACF | `01_stationarity_acf_pacf.ipynb` | JOHN MERCY OMETERE, Ademola Adeyemi , Odukaiye Moses |
| **Team C** | basket_price Modelling | `02_basket_price_models.ipynb` | Ojumoola Paul, Orinya Samuel Obande, Abdulmalik Abdulrashid |
| **Team D** | cpi_food Modelling & Forecasts | `03_cpi_food_and_forecasts.ipynb` | Maria Ebimo Ebiakofa, Fayemi Anthony Olatokunbo, @Sopuruchilizbeth |

### What Each Team Does

**Team Lead — Setup & Data Preprocessing**
- Creates and manages the GitHub repository
- Reviews and integrates all team submissions
- Work with every team in their respective notebooks

**Team A — Exploratory Data Analysis** (`00_data_preprocessing_eda.ipynb`)
- Runs data loading, cleaning, type conversion, and interpolation
- Engineers the basket price composite and derived features
- Produces the clean `df` dataframe used by all teams
- Time series plots for basket_price and cpi_food (level, MoM%, YoY%)
- Correlation heatmap of all variables
- Written markdown interpretations of all findings

**Team B — Stationarity & Diagnostics** (`01_stationarity_acf_pacf.ipynb`)
- Seasonal decomposition (trend, seasonal, residual components)
- ADF and KPSS tests on both series at the level and first difference
- ACF and PACF plots on differenced series
- Written stationarity conclusions and ARIMA order recommendations

**Team C — basket_cost Modelling & Forecasts** (`02_basket_price_models.ipynb`)
- Train/test split (train: Jan 2017 – Jul 2025 | test: Aug – Oct 2025)
- ARIMA baseline model
- SARIMAX with and without exogenous variables
- GARCH(1,1) volatility analysis on residuals
- 6-month forward forecasts for basket_cost (Nov 2025 – Apr 2026)
- Model comparison table and actual vs predicted visualisation

**Team D — cpi_food Modelling & Forecasts** (`03_cpi_food_and_forecasts.ipynb`)
- Shock dummy creation (shock_onset: Mar–Dec 2023, shock_persist: 2024)
- cpi_food standalone SARIMAX model
- cpi_food linked model (using basket_price forecasts as regressor)
- 6-month forward forecasts for food inflation (Nov 2025 – Apr 2026)
- Model comparison table and actual vs predicted visualisation
- Final dual-panel visualisations

---

## Repository Structure
```
TS_Academy_Capstone_Project/
│
├── Project_Data - Sheet1.csv          # Raw dataset
├── README.md                          # This file
│
├── 00_data_preprocessing_eda_decomposition.ipynb         # Team A: EDA
├── 01_stationarity_acf_pacf.ipynb    # Team B: stationarity
├── 02_basket_price_models.ipynb      # Team C: basket_price models
└── 03_cpi_food_and_forecasts.ipynb   # Team D: cpi_food + forecasts
```

---

## How to Run

1. Open [Google Colab](https://colab.research.google.com)
2. Go to **File > Open notebook > GitHub tab**
3. Search for `TS_Academy_Capstone_Project`
4. Open your assigned notebook
5. Run the dataset loading cell at the top **before any other cell**
6. Work through your assigned cells
7. Save back to GitHub via **File > Save a copy in GitHub**

> **Never work from a Google Drive copy. Always open directly from GitHub.**

---

## Dependencies
```python
pandas
numpy
matplotlib
statsmodels
pmdarima
scikit-learn
arch
```
## EDA — Plot Analyses

---

### Basket Cost Time Series

**Observation**  
Basket cost remained largely flat between ₦17,000–₦20,000 from 2017 to 2019, with gradual growth to ₦35,000 by mid-2023. After the June 2023 subsidy removal, prices surged aggressively, peaking above ₦100,000 in early 2025 before a modest decline to ~₦94,000 by 2026.

**Key Findings**
- The 2019 border closure and 2020 COVID lockdown produced no visible level shift — prices absorbed both events without structural disruption
- The June 2023 subsidy removal + FX unification is the dominant event — basket cost nearly **tripled** within 18 months
- The 2024 further FX depreciation accelerated the surge to its peak
- Post-2025 decline suggests some price stabilisation but at a permanently higher plateau

**Modelling Implication**  
The sharp non-linear jump confirms the need for shock dummy variables. A model trained on pre-2023 data alone would severely underestimate current price levels.

---

### Food CPI Time Series

**Observation**  
CPI Food grew steadily from ~230 in 2017 to ~650 by mid-2023, then accelerated sharply to a peak of ~1,240 by late 2025, before declining slightly to ~1,160 in early 2026.

**Key Findings**
- Growth was continuous and persistent even before the shock — food inflation was already structurally elevated
- The border closure (2019) and COVID lockdown (2020) caused brief pauses but no reversals
- The subsidy removal triggered the steepest acceleration — CPI Food nearly **doubled** within 18 months of the shock
- The slight decline in 2026 mirrors the basket cost pattern — both indicators are cooling from their peaks but remain historically high

**Key Difference from Basket Cost**  
CPI Food began accelerating earlier (from 2022 onward), suggesting it captured global commodity price pressures from the Russia-Ukraine war before they fully transmitted into raw basket commodity prices.

---

### Basket Cost MoM & YoY Time Series

**Observation**  
MoM% (red) remained low and stable throughout the sample, fluctuating between −5% and +15%. YoY% (blue) tells a dramatically different story — climbing from ~20% in 2020 to a peak of **127% in early 2024**, then declining sharply toward 0% and briefly negative by 2026.

**Key Findings**
- MoM% spikes are short-lived and mean-reverting — individual months of sharp increase are always followed by moderation
- The YoY% peak of 127% in early 2024 reflects the full annualised impact of the June 2023 shock
- The rapid YoY% decline from 2024 onward is a **base effect** — as the shock period enters the comparison window, the year-on-year gap narrows even if prices remain high
- Negative YoY% approaching 2026 signals that basket prices are now **lower than a year earlier** — a genuine cooling from the peak

**Modelling Implication**  
The volatility spike in MoM% post-2023 justifies GARCH modelling — variance is clearly not constant across the sample.

---

### Food CPI MoM & YoY Time Series

**Observation**  
MoM% (red) remained extremely stable between 0–3% throughout the full period with only minor post-2023 spikes. YoY% (blue) climbed from ~13% in 2018 to a peak of ~40% in early 2024, then declined sharply to ~9% by early 2026.

**Key Findings**
- CPI Food MoM is far more stable than basket cost MoM — the official index is smoother by construction
- The YoY% peak of ~40% (early 2024) is lower than basket cost's 127% peak, confirming CPI measures a broader, more buffered indicator
- The sharp YoY% decline from 2024 to 2026 is primarily a base effect, not a genuine deflation
- The brief negative MoM% dip in 2025 is notable — it reflects months where CPI Food actually fell month-on-month, likely driven by seasonal harvest improvements

---

### Basket Cost MoM Distribution

**Observation**  
The distribution is roughly bell-shaped and centred near 0%, with most months recording MoM changes between −3% and +5%. There are right-skewed outliers extending to +13–15%, and a small number of negative outliers around −7%.

**Key Findings**
- The near-zero centre confirms basket cost is relatively stable month-to-month in normal conditions
- The right tail (extreme positive months) corresponds to shock-period months in 2023–2024
- The distribution is **positively skewed** — large positive surprises are more common than large negative ones
- The outliers at +13–15% are the shock-onset months and should be treated as structural rather than random

**Modelling Implication**  
The fat right tail and positive skew justify using Student-t distributed errors in GARCH — a normal distribution would underestimate tail risk.

---

### Food CPI MoM Distribution

**Observation**  
Unlike basket cost, this distribution is **heavily right-skewed with no left tail**. Almost all observations are positive (0% to 4%), with two isolated extreme outliers near −6% and −2%.

**Key Findings**
- CPI Food almost never declines month-on-month — the two negative outliers are rare anomalies
- The concentration between 1–3% MoM reflects the persistent, structural nature of food inflation in Nigeria
- There is no symmetric distribution here — this is a **one-directional inflation process**
- The outliers at −6% are likely data revisions or seasonal deflation episodes (e.g. post-harvest gluts)

**Modelling Implication**  
The absence of a left tail means standard symmetric error distributions (Gaussian) are inappropriate. This supports the use of non-normal residual distributions in model fitting.

---

### Pre vs Post Shock (Basket Cost & CPI Food)

**Observation**  
Both panels clearly show two distinct regimes separated by the June 2023 dashed line. The pre-shock green zone shows gradual growth; the post-shock red zone shows near-vertical acceleration.

**Key Findings**
- **Basket Cost**: pre-shock range was ₦17,000–₦35,000 over 6 years; post-shock range is ₦35,000–₦103,000 — a **194% increase in under 2 years**
- **CPI Food**: pre-shock range was 230–650; post-shock range is 650–1,240 — a **91% increase** in the same period
- The slope change at the shock date is visually unambiguous in both panels
- Both series show slight moderation post-2025 peak but remain firmly in the post-shock regime

**Modelling Implication**  
The visual regime change confirms the structural break. Any model without shock dummies will have systematically biased residuals across the post-2023 period.

---

### Correlation Heatmap

**Observation**  
The entire heatmap is uniformly dark green — all correlations are between **0.89 and 1.00**. There are no negative or even moderate correlations anywhere in the matrix.

**Key Findings**
- **Basket Cost** correlates at 0.97–1.00 with bread, local rice, foreign rice, and vegetable oil — these are its primary price drivers
- **Food CPI** correlates at 0.94–0.99 with all commodities and macro drivers — it moves closely with the entire system
- **Exchange Rate** (0.99) and **Fuel Price** (0.97) are both near-perfectly correlated with basket cost — confirming their role as macro drivers
- **Tomatoes** (0.91–0.95) and **Brown Beans** (0.89–0.97) show slightly lower correlations — reflecting more volatile, weather-dependent supply
- **Chicken** shows the lowest correlation with Food CPI (0.98) — still very high but slightly more independent, possibly due to poultry-specific supply dynamics

**Key Caution**  
The uniformly high correlations are partly driven by the shared upward trend (non-stationarity). These correlations reflect co-movement over time, not necessarily causal relationships. Always interpret alongside differenced or detrended analysis.

---

### Scatter Plot: Basket Cost vs Exchange Rate & Fuel Price

**Observation**  
Both scatter plots show near-perfect linear relationships — overall fit r=0.99 (exchange rate) and r=0.97 (fuel price). Pre-shock blue dots cluster tightly at low values; post-shock red dots extend to the upper right.

**Key Findings**
- **Exchange Rate**: pre-shock r=0.92, post-shock r=0.93 — strong and consistent across both periods, with the post-shock period extending the range to ₦800–₦1,700/USD
- **Fuel Price**: pre-shock r=0.87, post-shock r=0.86 — similarly strong, with fuel price jumping from ~₦180/litre to over ₦1,200/litre post-shock
- The pre- and post-shock regression lines follow nearly identical slopes — the **transmission rate** did not change, only the *level* of the drivers did
- A few post-shock red dots fall below the regression line — months where exchange rate spiked but basket prices had not yet fully adjusted

**Modelling Implication**  
The strong, stable linear relationships across both periods validate exchange rate and fuel price as exogenous regressors in SARIMAX. The relationship is structural, not regime-specific.

---

### Rolling 12-Month Correlation

**Observation**  
Both panels show a clear strengthening of correlation after June 2023, though with different patterns.

| Driver | Pre-Shock Avg | Post-Shock Avg | Pattern |
|---|---|---|---|
| Exchange Rate | r = 0.41 | r = 0.69 | Volatile pre-shock, strong then collapsed in 2025 |
| Fuel Price | r = 0.27 | r = 0.72 | Episodic pre-shock, sustained post-shock |

**Key Findings**
- **Exchange Rate**: the correlation was already climbing toward 1.0 pre-2023 (from 2020 onward), suggesting FX pressure was building before the official shock. The collapse toward 0 in late 2025 indicates a period where exchange rate stabilised while basket prices continued moving independently
- **Fuel Price**: transformed from a cyclical, episodic relationship to a sustained high correlation post-shock — confirming fuel became a **continuous structural driver** after subsidy removal
- **Fuel price (r=0.72) is the more reliable post-shock driver** — it remained consistently above 0.7 without the volatility seen in the exchange rate correlation

**Modelling Implication**  
Both macro drivers are justified as exogenous regressors. The post-shock sustained correlations confirm they belong in the model, and the pre-shock instability explains why shock dummies are necessary to handle the regime change.

---

### Individual Commodity Price Trends

**Observation**  
All 14 commodities clustered tightly below ₦500/unit from 2017–2022, then diverged sharply post-2023. By 2025, prices had separated into distinct tiers.

**Key Findings**
- **Eggs** and **Local Rice** are the highest-priced commodities — eggs spiked to ~₦7,500 and local rice peaked at ~₦6,500 in 2025 before partial correction
- **Chicken** reached ~₦6,500 at peak — reflecting sensitivity to both feed costs (maize-driven) and cold chain fuel costs
- The majority of commodities (maize, garri, yam, tomatoes, onions, vegetable oil, palm oil) converged to a ₦1,000–₦2,500 range post-shock — a **4–8× increase** from pre-shock levels
- **Bread** shows a relatively flatter post-shock trajectory — reflecting some price stickiness at retail level
- The spike-and-partial-correction pattern in eggs and local rice suggests **speculative price overshooting** followed by market correction

---

### Stacked Area Chart: Commodity Contributions

**Observation**  
The total weighted basket was stable at ~₦17,000–₦20,000 from 2017 to 2020, grew gradually to ~₦35,000 by 2023, then surged to a peak of ~₦103,000 in 2025. The composition of contributions also widened dramatically.

**Key Findings**
- **Pre-shock**: all commodity layers were thin and evenly distributed — no single commodity dominated
- **Post-shock**: the stack more than doubled in height, with **garri, local rice, vegetable oil, and chicken** showing the most visible expansion
- **Garri and local rice** — despite being locally produced staples — show large post-shock contribution expansions, driven by transport cost inflation and domestic supply disruptions
- The visible thickening of almost every layer confirms the shock was **broad-based** — all 14 commodities contributed to the surge

---

### % Change in Weighted Contribution (Pre vs Post Shock)

**Observation**  
Every single commodity recorded a positive post-shock contribution increase, ranging from **+158.3% (chicken)** to **+473.3% (yam)**. All bars are red — no commodity was immune to the shock.

| Rank | Commodity | % Change | Reason |
|---|---|---|---|
| 1st | Yam | +473.3% | Highly transport-dependent, no cold storage, severe logistics cost pass-through |
| 2nd | Potatoes | +349.3% | Similar logistics exposure, perishable |
| 3rd | Local Rice | +340.6% | Domestic supply chain + fuel costs for milling and transport |
| 4th | Brown Beans | +332.9% | Major Northern supply regions hit by insecurity + transport costs |
| 5th | Maize | +316.0% | Feed grain for poultry and livestock — ripple effect across animal products |
| Last | Chicken | +158.3% | Partially buffered by vertical integration in the poultry industry |

**Key Findings**
- The **top 5 are all locally produced staples** — contradicting the assumption that import-dependent items suffer most. Local food supply chains proved equally vulnerable to fuel cost transmission
- **Chicken's relatively low increase** (+158%) reflects that large-scale poultry producers partially absorbed cost increases through operational efficiencies
- The uniformity of increases across all 14 items confirms a **systemic shock** rather than commodity-specific disruptions

**Modelling Implication**  
The broad-based nature of the shock validates using a single structural break dummy for the entire basket rather than commodity-specific interventions.

---

### Basket Cost and Food Inflation CUMSUM

The CUSUM analysis provides formal statistical confirmation of the structural 
break identified visually in the level plots. Key findings:

1. **Basket Cost structural break**: June 2023 — coincides exactly with the fuel 
   subsidy removal and CBN exchange rate unification, confirming these policy 
   events as the primary driver of the price regime change.

2. **CPI Food structural break**: August 2022 — approximately 10 months earlier,
   reflecting global commodity shocks (Russia-Ukraine war) and pre-existing 
   naira weakness that transmitted into broader food inflation before the 
   official policy shock.

3. Both series breach the ±2σ statistical bounds, confirming the breaks are 
   genuine regime changes and not random variation.

4. The V-shaped recovery in both series confirms that post-shock price growth 
   was so rapid it fully offset years of below-average readings, establishing 
   a permanently higher price plateau.

These findings justify the use of shock dummy variables (shock_onset and 
shock_persist) in all SARIMAX specifications, and confirm that any model 
trained on pre-2022 data alone would severely underestimate current and 
future food price levels.

---

---

## Basket Cost Seasonal Decomposition (Multiplicative)

**Observation**  
The multiplicative decomposition separates basket cost into three components: a dominant upward trend, a stable repeating seasonal pattern, and a residual that amplifies post-2023.

**Trend Component (orange)**  
- Flat and near-zero growth from 2017–2020, confirming basket cost was structurally stable in this period
- Gradual acceleration from 2020–2022 as COVID supply chain effects and pre-shock inflation built up
- Sharp exponential-style surge from mid-2023 onward, reaching ~₦100,000 by 2025
- The trend component smoothly captures the regime change — confirming the shock was a **permanent level shift**, not a temporary spike

**Seasonal Component (green)**  
- Oscillates consistently between **0.99 and 1.02** across the entire 2017–2026 period
- The pattern repeats identically every 12 months — confirming a **stable annual seasonality** (m=12)
- Seasonal amplitude is very small (~±1%) relative to the overall price level — meaning seasonality explains only a minor fraction of total price variation
- The consistency of the seasonal pattern across both the pre- and post-shock periods confirms that the shock did not distort the seasonal cycle — it only shifted the trend level

**Residual Component (red)**  
- Residuals remained tightly clustered around 1.0 (the neutral line) from 2017–2023 — confirming the model fits well in the stable period
- Post-2024, residuals become more volatile, oscillating between 0.93 and 1.06 — reflecting price volatility that the trend and seasonal components cannot fully explain
- The increased residual variance post-2023 is direct evidence of **heteroskedasticity** (non-constant variance)

**Modelling Implication**  
- The stable seasonal component confirms `m=12` and `D=1` (seasonal differencing) are appropriate in SARIMAX
- The increasing residual variance post-2023 justifies **GARCH modelling** on the residuals to capture time-varying volatility
- The smooth trend confirms shock dummies are needed to model the level shift, as the trend component alone cannot replicate the abrupt acceleration

---

## Food CPI Seasonal Decomposition (Multiplicative)

**Observation**  
The decomposition reveals a consistently growing trend, a very weak but stable seasonal pattern, and residuals that are well-behaved pre-2023 but diverge sharply post-2024.

**Trend Component (orange)**  
- Unlike basket cost, the CPI Food trend shows **no flat period** — it has grown continuously since 2017 without pause
- Growth is smooth and accelerating — the curve is concave upward throughout, steepening noticeably from 2022 onward
- The trend reaches ~1,200 by late 2025, closely tracking the original series — confirming the trend component captures the bulk of variation in CPI Food
- The absence of a flat early period (unlike basket cost) reflects that CPI inflation was already structurally embedded before the 2023 shock

**Seasonal Component (green)**  
- Oscillates between **0.9950 and 1.0060** — an even narrower range than basket cost (~±0.5%)
- The seasonal pattern is highly consistent and repeats exactly every 12 months
- A clear within-year pattern is visible: CPI Food tends to spike in **mid-year (around Q2–Q3)** and dip in **early year (Q1)**, likely reflecting harvest and festive demand cycles
- Seasonality is weaker in CPI Food than in basket cost, which makes sense as the official index applies weighting and smoothing that dampens raw commodity seasonality

**Residual Component (red)**  
- Pre-2023 residuals are remarkably stable, oscillating tightly between 0.98 and 1.02 — the model fits almost perfectly in this period
- A notable dip below 1.0 in 2020–2021 reflects COVID-related demand suppression that the model does not fully explain
- Post-2024 residuals become highly volatile, with spikes reaching 1.03 and 1.08 and drops to 0.97 — significantly larger than the pre-shock range
- The sharp upward spike at the very end of the series (early 2026) suggests a recent price acceleration that the trend component has not yet caught up with

**Modelling Implication**  
- The very weak seasonal component (±0.5%) explains why `D=0` (no seasonal differencing) was selected for the CPI Food SARIMAX model — seasonal differencing would overcorrect a signal this small
- The contrast with basket cost (where `D=2` performed better) reflects a fundamental difference: CPI Food is trend-dominated, while basket cost has a stronger seasonal structure
- The post-2024 residual volatility confirms GARCH is equally applicable to CPI Food residuals — volatility clustering is present in both series

---

## Comparative Summary — Basket Cost vs Food CPI Decomposition

| Component | Basket Cost | Food CPI |
|---|---|---|
| **Trend shape** | Flat 2017–2020, exponential post-2023 | Continuously growing, steepening from 2022 |
| **Seasonal amplitude** | ±1.0% (moderate) | ±0.5% (very weak) |
| **Seasonal stability** | Consistent across full period | Consistent across full period |
| **Residual pre-shock** | Tight (0.95–1.05) | Very tight (0.98–1.02) |
| **Residual post-shock** | Volatile (0.93–1.06) | Highly volatile (0.97–1.08) |
| **Key implication** | Seasonal differencing warranted (D=1 or D=2) | Seasonal differencing not needed (D=0) |
| **GARCH justified?** | Yes — residual variance increases post-2023 | Yes — residual variance increases post-2024 |

---
---

## Basket_cost Model Results & Selection

### Model Comparison Table

| Model | MSE | MAE | MAPE | Role |
|---|---|---|---|---|
| SARIMAX(2,2,3)(0,1,1,12) + exog | 11,498,346.40 | 2,814.17 | **2.73%** | ✅ Primary |
| SARIMAX(2,2,3)(0,1,1,12) no exog | 19,006,908.38 | 3,947.19 | 3.87% | Comparable |
| ARIMA(2,2,3) | 18,389,113.64 | 3,906.64 | 3.92% | Baseline |

---

## Model Selection Rationale

**Primary Model: SARIMAX(2,2,3)(0,1,1,12) + exog**  
Selected based on superior performance across all three metrics. Adding exogenous variables (fuel price, exchange rate, shock dummies) reduced MAPE from 3.87% to **2.73%** — a **29.5% improvement** over the same SARIMAX specification without exog, and a **30.4% improvement** over the ARIMA baseline. All three targets comfortably beat the 5% MAPE project threshold.

---

## Key Findings

- **Exogenous variables matter significantly** — the gap between SARIMAX+exog (2.73%) and SARIMAX no-exog (3.87%) confirms that fuel price, exchange rate, and shock dummies carry genuine predictive signal beyond what the ARIMA structure captures alone
- **Seasonal structure adds marginal value** — SARIMAX no-exog (3.87%) and ARIMA (3.92%) perform almost identically, suggesting the seasonal component (0,1,1,12) contributes only ~0.05 MAPE points on its own; the real gain comes from the exogenous regressors
- **MSE gap is the most striking metric** — the primary model's MSE (11.5M) is nearly **half** that of the no-exog and baseline models (~18.4–19.0M), indicating the exogenous variables substantially reduce large forecast errors, not just average errors
- **MAE of ₦2,814** means the primary model's average forecast error is ~₦2,814 per month — on a basket averaging ~₦60,000–₦90,000 in the test period, this is an economically small error

---

## Modelling Implication

The results confirm the core hypothesis of this project: **macroeconomic drivers (fuel price, exchange rate) and the 2023 structural break (shock dummies) are not optional controls — they are the primary sources of forecast accuracy improvement**. A pure time series model (ARIMA) without these regressors leaves nearly 30% of forecastable error on the table.

---
## Comparative Summary — Food CPI GARCH vs Basket Cost GARCH

| Feature | Basket Cost | Food CPI |
|---|---|---|
| **Residual scale** | Large (±15 scaled) | Very small (±0.17 scaled) |
| **Dominant volatility spike** | 2017 + 2018 | 2017 only |
| **Calm period** | 2019–2023 | 2019–2023 |
| **Post-shock volatility** | Rising, episodic | Rising, episodic but smaller |
| **nu (ν)** | 3.91 (very fat tails) | 4.90 (moderate fat tails) |
| **Student-t justified?** | Yes — strongly | Yes — moderately |
| **Pre-shock avg σ** | ₦1,639 | 21 units |
| **Post-shock avg σ** | ₦2,195 (34% higher) | 14 units (inflated by 2017) |
| **ARIMA forecast bias** | Upward | Upward |
| **SARIMAX+exog improvement** | Correctly identifies moderation | Correctly identifies moderation |

**Conclusion**
Both series exhibit IGARCH persistence, fat-tailed residuals, and
post-shock volatility elevation — confirming GARCH was appropriate for
both. Food CPI residuals are better behaved than basket cost residuals,
reflecting that the official index is smoother by construction. In both
cases, SARIMAX + exog substantially outperforms the ARIMA baseline by
correctly capturing post-peak moderation that pure time series models
miss entirely.

---
## Project Conclusion

### Forecasting Nigerian Food Prices: A Time Series Approach to
### Understanding Structural Shocks, Macro Drivers, and Inflation Dynamics

---

### Overview

This project set out to build a reliable, data-driven forecasting system
for two critical indicators of Nigerian food affordability, the weighted
household **Basket Cost** and the official **Food CPI**, using monthly
data spanning January 2017 to January 2026. The central challenge was
not merely technical: it was to build models that could honestly reflect
the economic reality of a food system that was fundamentally and
permanently altered by one of the most consequential policy decisions
in Nigeria's recent history, the removal of the petrol subsidy in
June 2023.

Both targets exceeded the project's primary performance threshold of
5% MAPE, with the primary models achieving:

| Target | Model | MAPE | MAE |
|---|---|---|---|
| **Basket Cost** | SARIMAX(2,2,3)(0,1,1,12) + exog | **2.73%** | ₦2,814 |
| **Food CPI** | SARIMAX(2,2,2)(0,0,1,12) + exog | **3.06%** | 37.3 pts |

These results were not achieved by model complexity alone, they were
achieved by correctly understanding and encoding the economic structure
of Nigerian food markets into the modelling framework.

---

### What the Data Told Us

The exploratory analysis told a story that statistics alone is not sufficient. From 2017 to early 2023, Nigerian food prices grew gradually — absorbing the 2016 recession, the 2019 land border
closure, and the COVID-19 disruptions without permanent structural
damage. Basket cost moved from ₦17,000 to ₦35,000 over six years.
Food CPI climbed from 230 to 650 over the same period. These were
significant increases, but they followed a predictable trajectory that
conventional time series tools could track.

Then June 2023 arrived.

Within 18 months of the subsidy removal and simultaneous naira
unification, basket cost nearly tripled to over ₦100,000. Food Inflation
almost doubled to 1,240. The CUSUM analysis formally confirmed what
the level plots showed visually, June 2023 was the exact month of
maximum statistical deviation for basket cost, while Food CPI had
already begun its structural break in August 2022, reflecting earlier
transmission of global commodity shocks through import-dependent food
categories.

The commodity deep-dive made the human cost of this explicit. Every
single one of the 14 basket commodities recorded post-shock price
increases exceeding 150%. Yam, a locally produced staple with no
import dependency increased by 473%, driven entirely by fuel cost
transmission through transport and logistics. This finding directly
challenged the assumption that import-dependent commodities suffer
most during FX shocks. In Nigeria's food system, where fuel is
embedded at every stage from farm to market, the transport cost
channel proved equally or more destructive than the import price
channel.

---

### What the Models Confirmed

The modelling phase validated four core hypotheses:

**1. Exogenous macro drivers are not optional, they are essential**

The comparison between SARIMAX with and without exogenous variables
was definitive. Without fuel price, exchange rate, and shock dummies,
both ARIMA and SARIMAX models forecast continued upward momentum into
2026, getting the direction of movement entirely wrong. The actual
series was declining from its 2025 peak while the no-exog models
confidently projected further acceleration. This is not a marginal
difference in accuracy — it is a fundamental failure of the model to
understand what is driving prices.

Including exogenous regressors reduced basket cost MAPE by 29.5% and
corrected the directional forecast for Food CPI entirely. Fuel price
and exchange rate are not control variables, they are the primary
transmission channels through which government policy and global
markets reach Nigerian dinner tables.

**2. The 2023 structural break required explicit modelling**

Standard time series models assume the process generating the data
remains stable throughout the sample. The June 2023 shock violated
this assumption catastrophically. They were the mechanism by which the models distinguished between the pre-shock gradual growth regime and the post-shock permanent price plateau. Without them, every model would have been biased
across the entire post-2023 period.

**3. Volatility is not constant and pretending it is understates risk**

The GARCH(1,1) analysis revealed that basket cost residuals exhibit
IGARCH persistence (α + β = 1.0) with Student-t distributed errors
(ν = 3.91). This means volatility shocks in Nigerian food prices do
not decay, they persist indefinitely, consistent with a permanent
regime change. The fat tails (ν < 5) confirm that extreme price months
occur far more frequently than a normal distribution would predict.

For Food CPI, the GARCH results were similarly revealing  ν = 4.9
and IGARCH persistence, though the series was smoother and better
behaved than basket cost by construction. Post-shock conditional
volatility rose in both series, confirming that the new price regime
is not only higher in level but higher in uncertainty.

The practical implication is direct: any confidence interval or risk
estimate built on the assumption of constant variance will
systematically underestimate downside risk during periods of macro
stress, exactly when accurate uncertainty quantification matters most.

**4. The linked architecture improved Food CPI forecasting**

Using basket cost forecasts as an exogenous regressor in the Food CPI
model, the linked SARIMAX architecture outperformed the standalone
specification. This confirms that basket cost is not just a parallel
indicator to Food CPI but a genuine leading signal that carries
predictive information about where the official inflation index is
heading. The two series are structurally connected through the same
underlying commodity markets and macro drivers, and modelling that
connection explicitly improved forecast accuracy.

---

## The Broader Economic Narrative

The numbers in this project tell a story about policy consequences that
extends far beyond forecasting methodology.

Nigeria's June 2023 dual shock, fuel subsidy removal and FX
unification, was economically necessary in the long run. The subsidy
had become fiscally unsustainable, consuming over ₦4 trillion annually
by 2022. The multiple exchange rate windows distorted capital allocation
and encouraged rent-seeking. The reforms were inevitable.

But the data shows with uncomfortable clarity what "inevitable" meant
for Nigerian households. A family spending ₦35,000 per month on food
in May 2023 was spending over ₦100,000 for the same basket by early
2025, a 186% increase in 20 months. Yam prices increased 473%.
Local rice increased 341%. Brown beans increased 333%. These are not
abstract index movements, they represent millions of Nigerian
households being priced out of adequate nutrition.

The rolling correlation analysis showed that fuel price became a
**continuous structural driver** of food costs after June 2023, no
longer the episodic, government-controlled variable it was during the
subsidy era, but a market-driven cost that now flows permanently and
continuously into every stage of food production and distribution. The
pre-shock average rolling correlation between fuel price and basket
cost was r = 0.27. The post-shock average is r = 0.72 and sustained.
This is the statistical signature of a structural transformation, not
a temporary disruption.

---

### Limitations and Honest Caveats

This project was conducted with methodological rigour, and that rigour
requires acknowledging its boundaries:

**Data quality** — Basket cost data for November 2025 to January 2026
was identified as forward-filled rather than independently observed.
All evaluation metrics were computed on the confirmed three-month test
period (August–October 2025) only. Forward forecasts beyond this point
are genuine predictions, not evaluations.

**Short post-shock sample** — With approximately 30 post-shock
observations, GARCH parameter estimates carry wide confidence intervals.
The IGARCH finding (α + β = 1.0) is directionally valid but should be
interpreted as indicative of high persistence rather than a definitive
permanent-volatility conclusion.

**Constant exog assumption** — The 6-month forward forecasts assume
fuel price and exchange rate remain at their 3-month rolling average
values. Any significant policy change — further naira depreciation,
fuel price adjustments, or external commodity shocks — would shift
the central forecast materially. The widening confidence intervals
honestly reflect this uncertainty.

**Causal inference** — The high correlations observed throughout this
project reflect co-movement over time, not established causal
relationships. The models are optimised for forecasting accuracy, not
causal identification.

---

## Final Remarks

This project demonstrated that forecasting Nigerian food prices is
fundamentally an exercise in understanding Nigerian economic policy.
The best statistical model in the world cannot outperform a model that
correctly identifies the forces driving the series, and in Nigeria's
food market, those forces are fuel costs, exchange rates, and the policy
decisions that determine them.

The SARIMAX + exog framework, supported by GARCH volatility modelling
and grounded in a thorough structural understanding of the June 2023
shock, produced forecasts that not only met the 5% MAPE target but
correctly identified the direction, magnitude, and uncertainty of
food price movements in the post-shock period.

For policymakers, the message is clear: food price stability in Nigeria
is inseparable from energy price stability and exchange rate management.
For households, the data confirms what they already know: the cost of
feeding a family in Nigeria has reached a level that demands urgent and
sustained policy attention.

For the field of time series analysis, this project adds to the growing
evidence that the economic and institutional context is not a supplement to
Good modelling, but it is the foundation.

---

*TS Academy — Track 3: Time Series Analysis*
*Capstone Project: Nigerian Food Basket Price & Food CPI Forecasting*
*Group 7*

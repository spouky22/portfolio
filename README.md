# portfolio
[Zouaoui Med Aziz](#top)[Projects](#projects)[Experience](#experience)[Education](#education)[Contact](#contact)

Zouaoui Med Aziz Business Analytics · Tunis, Tunisia

# Zouaoui Med Aziz, business analyst.

I turn sales and pricing data into decisions. Business Analyst at Délice Holding, Master’s student in Business Analytics, and a former team leader and mentor in Enactus. I build dashboards and decision tools with SQL, R, Python and Power BI.

[View my work](#projects)[LinkedIn](https://linkedin.com/in/zaouaoui-med-aziz-a84668175)[Email me](mailto:mohamedaziz.zouaoui@msb.tn)

**4 years**leading teams in Enactus, 2022–2026

**Master’s**Business Analytics, MSB, 2025–2027

**4 languages**English, Arabic, French, German

**Aug 2026**Business Analyst at Délice Holding

## Projects

Each project starts from a business question and ends with a decision.

FeaturedDélice Holding

### Pricing decision-support system

Python · Streamlit · pandas · Internship project

For every **customer × product**, the system tells the pricing team whether a discount would create profit or destroy it, with transparent confidence levels. It replaces slow manual reviews with a guided, repeatable workflow.

UploadCostsMappingQualityDashboardScenariosExport

**Smart onboarding**Auto-detects columns in the uploaded file, then the user confirms the mapping.

**Data quality gate**Cleans the data and produces a quality report before any analysis runs.

**Pricing analytics**Baseline, price elasticity, discount simulation and optimization.

**Clear recommendations**KPIs, insights and recommendations per customer and product.

```
app/streamlit_app.py   # UI and navigation only
engine/*               # all analytics: elasticity, simulation, optimization
engine/config          # thresholds and field mapping, no hard-coded rules
```

Design choice: the interface contains no analytics. Everything lives in the engine, so each method can be tested and changed on its own.

#### The analysis behind it: pricing opportunity review

**Question:** should we cut prices for specific customers? I screened 7,287 customer-product pairs (217 products, 729 customers) from JD Edwards sales transactions, over a window of about two weeks.

ScreenSimulateSegment

Screen: keep pairs with enough purchase history. Simulate: project quantity, revenue and profit at each discount level using category-level price sensitivity. Segment: sort each pair into Opportunity, Low-sensitivity, Risk or Insufficient data.

**249 opportunity pairs**60 of them high-confidence. Mostly juices and milkshakes, where extra volume covers the lower margin.

**146 risk pairs**Mostly staple dairy, where a discount just gives margin away because customers don’t buy more.

**90% not yet scoreable**Set aside for lack of history instead of forcing a guess.

**35 customers in both lists**They buy an opportunity item and a risk item, so pricing has to be decided product by product, not customer by customer.

**Recommendation:** an 8-week pilot on the top 15 to 20 juice and milkshake pairs, staples untouched, with a control group to measure real volume and profit before any wider rollout.

Honest limits: price sensitivity is assumed at category level, not yet measured, and the window is short. The direction is firm, the exact figures are not. Financial figures are left out because the data is confidential.

#### Inside the engine

**1 · Elasticity in three tiers**Measured per customer × product with a log-log regression and a time trend. When the data is too thin, it falls back to a pooled estimate for the product, then to a category prior. Slopes outside −3.0 to −0.05 are rejected as artifacts of narrow price windows.

**2 · Discount simulation**Quantity responds as (1 − discount)^elasticity, so it never goes negative. Eight discount levels, from 1% to 20%, are tested for every pair, projecting volume, revenue, profit and the break-even volume increase.

**3 · Three safety tests**For each pair, the largest discount that keeps baseline profit, keeps profit positive, or keeps the margin above a floor. Each test is checked independently.

**4 · KPIs and auto-insights**Revenue, volume, margin and elasticity coverage, plus automatic flags for top opportunities, margins below 15% and data-quality gaps. Every result carries its source, so measured figures and assumptions are never mixed up.

Category priors run from −0.3 for milk to −0.8 for juices and milkshakes. They are economic assumptions, not estimates from this data, which is why the pilot is needed to measure the real response.

**Code:** \[GitHub link, if approved\]

FeaturedFinal-year thesis (PFE)

### Stationarity and volatility of cryptocurrency returns

ESCT, University of Manouba · Supervisor: Haykel Hamdi · Econometrics

**Question:** do crypto prices follow stable patterns that can be measured and predicted with economic tools? I analyzed six assets (BTC, ETH, LTC, USDT, LINK, XRP) on daily data from January 2019 to December 2024, covering bull and bear markets and COVID-19.

Descriptive statsDickey-FullerLjung-BoxARCH-LMGARCH(1,1)Residual checks

**Returns are stationary**The Dickey-Fuller test rejects a unit root for all six assets at the 1% level.

**Volatility clusters**GARCH(1,1) shows shocks fade slowly: persistence runs from 0.944 (BTC) to 0.978 (ETH).

**Fat tails, downside risk**Kurtosis is far above normal and normality is rejected. BTC and ETH are negatively skewed.

**Model fits**No ARCH effects remain in the residuals (p-values above 0.5).

| Asset | α₁ shock | β₁ persistence | α₁ + β₁ |
| --- | --- | --- | --- |
| Bitcoin | 0.1161 | 0.8281 | 0.9442 |
| Ethereum | 0.1023 | 0.8759 | 0.9782 |
| Chainlink | 0.1180 | 0.8552 | 0.9732 |
| Litecoin | 0.0874 | 0.8856 | 0.9730 |
| Tether | 0.0587 | 0.9082 | 0.9669 |
| XRP | 0.0541 | 0.9035 | 0.9576 |

**Takeaway:** returns are stationary but volatility is dynamic, and GARCH captures that risk well. The results support tools like VaR and stress testing, and they argue for caution in institutional adoption and for regulation.

**Links:** \[thesis PDF\] · \[code or notebook\]

Pythonpandas

### Reducing product returns

E-commerce analysis · Memo to management

Analyzed which products, customers and periods drive returns, and wrote a decision memo for management.

**Finding:** \[key number\]

Tableau

### Equipment downtime dashboard

Telemetry analysis · Data analysis task

Defined an “unhealthy” status with a calculated field and compared downtime by plant and device type.

**Finding:** \[key number\]

EconometricsStata

### Credit spread determinants

QMM 502 · Team of four · Dr. Anis Samet · June 2026

Do legal institutions in an issuer’s home country change the cost of corporate debt? OLS with robust standard errors on 3,322 international bonds, controlling for firm fundamentals and bond structure.

**Rating dominates**−28.1 bps per rating notch (p\<0.001). R² = 0.49.

**Callable premium**+56.1 bps overall, +36.9 for investment grade, and gone for junk bonds.

**Enforcement helps**Efficient debt enforcement lowers spreads (−0.70 per point). Creditor rights show a positive sign (+6.86), probably because risky markets adopt stronger laws.

**Legal origin is fragile**Civil law is insignificant in the full sample (p=0.596) but turns significant without callable bonds (−24.5) and for junk issuers (+135.7).

Checks: Breusch-Pagan χ²=1979.7, so robust errors throughout. Max VIF 2.98. Leverage swap, investment-grade and junk subsamples.

**My role:** \[your part in the team\]

Power BIDAX

### Customer churn dashboard

Power BI · Churn analysis

Measures churned customers and churn rate, then shows who leaves, why and where.

**Data check**Customers vs unique customers, to validate the data before measuring.

**Churn measures**Number of churned customers and churn rate as reusable measures.

**Why they leave**Bar chart by churn reason and pie chart by churn category.

**Where**Map by state combining churn rate and customer count.

**Finding:** \[churn rate and top reason\]

Power BIDAX

### Sales analysis dashboard

Power BI · Sales and discount analysis

Tracks total sales and sales after discount, and explains where revenue comes from.

**Headline cards**Total sales vs total sales after discount.

**Mix**Sales by product, customer segment and sales channel.

**Price and discount**Revenue against quantity, average discount and average unit price.

**Delivery and Pareto**Delivery performance donut and a cumulative-sales Pareto of products.

**Finding:** \[key number\]

Power BIPareto

### Customer Pareto (80/20)

Power BI · Delivery case analysis

Ranks customers by sales and shows how few of them make up 80% of revenue.

**Ranking table**Customer rank, total sales and cumulative sales %.

**Pareto chart**Columns for sales with a cumulative line and an 80% goal line.

**Ask in plain words**Q&A visuals let a user query the data in natural language.

**Finding:** \[share of customers behind 80% of sales\]

## Experience

Analytics at work, backed by years of leading and coaching teams.

**Business Analyst · Délice Holding**August 2026 – present

Analyze and transform business data with SQL, R, VS Code and Power BI. Build interactive dashboards and analytical interfaces for sales, pricing and profitability insights.

**Facilitator · Enactus National Exposition**July 2026

**Regional Mentor · Enactus Tunisia**September 2025 – July 2026

Coached teams on project structure, business model and impact, tracked KPIs, delivered trainings (pitching, BMC, finance basics) and prepared teams for national competitions.

**Sales Intern · Opus Lab Tunis**June – September 2025

Prospected and qualified leads with CRM tools, ran market and competitor research, and supported campaigns that helped hit monthly KPIs.

**Team Leader · Enactus ESCT**2024 – 2025

Led a multidisciplinary team running social entrepreneurship projects, with partnerships, planning and recruitment.

**Head of Partnership and Public Relations · Enactus ESCT**2023 – 2024

**Part-time Trainer · Graines d’Entrepreneur**2023 – 2024

Delivered workshops on entrepreneurship fundamentals to aspiring young entrepreneurs.

## Education and recognition

### Master’s in Business Analytics

Mediterranean School of Business · 2025–2027

### Licence in Economics

Financial and Economic Engineering · Manouba Business School · 2022–2025

### Scientific Baccalaureate

With honours · Lycée Tabarka · 2018–2022

Member of the Month 2023, Enactus ESCTCertificate of recognition 2024, Graines d’EntrepreneurTeam Leader certificate 2025, Enactus ESCT

Languages: English, Arabic, French (basic), German (basic). Outside work: reading, gaming, and former member of the Tunisian national basketball team.

## Let’s talk

Open to analyst roles and internships, in Tunisia and abroad.

[mohamedaziz.zouaoui@msb.tn](mailto:mohamedaziz.zouaoui@msb.tn)[zouaouiaziz300@gmail.com](mailto:zouaouiaziz300@gmail.com)[LinkedIn](https://linkedin.com/in/zaouaoui-med-aziz-a84668175)

© 2026 Zouaoui Med Aziz. Highlighted text marks placeholders to replace with your results and links.

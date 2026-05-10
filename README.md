# Cellphone Market & Consumer Behaviour — Exploratory Data Analysis

> **MBA Data Analytics Minor Project** | Tools: Python · Pandas · Seaborn · Matplotlib · SciPy  
> Dataset: 990 records · 22 variables · 10 brands · 8 Indian cities

---

## Business problem

Mobile phone brands and retailers in India need to understand **what drives pricing, who buys what, and how hardware specs correlate with consumer demographics**. This project analyses a real-world cellphone transaction dataset to surface actionable insights for product strategy and market segmentation.

---

## Dataset overview

| Attribute | Detail |
|---|---|
| Records | 990 transactions |
| Variables | 22 (11 numerical, 11 categorical) |
| Brands covered | Apple, Samsung, OnePlus, Xiaomi, Vivo, Oppo, Motorola, Google, Sony, Asus |
| Operating systems | Android, iOS |
| User cities | Delhi, Mumbai, Bangalore, Hyderabad, Chennai, Pune, Kolkata, Ahmedabad |
| Price range | ₹11,268 – ₹1,74,525 |
| User profiles | Age, gender, occupation, salary, city |

---

## What this project covers

### 1. Data pre-processing
- Null value detection and duplicate row check — dataset confirmed clean
- Auto-incremented `Record_id` created as surrogate key
- `release date` column converted from object to proper datetime format
- Numerical vs categorical variable split for targeted analysis

### 2. Outlier analysis — boxplots for all numerical variables
Boxplots generated for: performance, selfie camera, main camera, RAM, internal memory, battery size, screen size, weight, price (INR), user age, and salary.

**Key findings:**
- **Price** is strongly right-skewed — a small number of flagship phones (₹1L+) pull the distribution upward; most phones sit in the ₹25K–₹75K mid-range band
- **Battery size** shows almost zero variation across brands — modern smartphones have standardised around 4,000–5,000 mAh
- **Screen size** is highly concentrated between 6.4–6.8 inches, reflecting industry-wide convergence
- **Main camera** has the highest outlier range (up to 200 MP) — premium phones are the clear driver
- **RAM** shows a bimodal split between budget (4–6 GB) and flagship (12 GB+) segments

### 3. Correlation heatmap
Pearson correlation matrix across all numerical features.

**Notable correlations:**
- `price(INR)` ↔ `internal memory` → **0.83** (strongest relationship in dataset)
- `price(INR)` ↔ `RAM` → **0.70**
- `weight` ↔ `screen size` → **0.82** (larger screens = heavier phones)
- `RAM` ↔ `internal memory` → **0.67**
- `price(INR)` ↔ `main camera` → **−0.24** *(interesting anomaly — higher-priced phones don't always lead on raw MP count)*
- `age` and `Salary_in_INR` show near-zero correlation with hardware specs → **purchasing behaviour is not income/age-driven**

### 4. Categorical distributions — count plots
Count plots for: brand, operating system, gender, occupation, city, and more.

### 5. Statistical hypothesis testing

#### t-Tests (SciPy)

| Test | Hypothesis | Result |
|---|---|---|
| iOS vs Android price | H₀: No price difference | **Rejected** — iOS significantly more expensive (p ≈ 0) |
| Selfie camera > 8 MP | H₀: Mean selfie camera ≤ 8 MP | **Rejected** — average selfie camera exceeds 8 MP (p ≈ 0) |
| Battery size > 4000 mAh | H₀: Mean battery ≤ 4000 mAh | **Rejected** — confirmed modern phones exceed 4000 mAh standard |
| Delhi vs Mumbai salary | H₀: No salary difference | **Rejected** — Mumbai users earn significantly more (p ≈ 0) |

#### ANOVA Tests

| Test | Result |
|---|---|
| Price across brands | **Significant** — brands price very differently (p ≈ 0) |
| Price across occupations | **Not significant** — occupation does not predict spend (p = 0.69) |
| Performance rating by age group | **Not significant** — age doesn't drive performance preference (p = 0.79) |
| Battery size across brands | **Significant** — brand-level battery strategy varies (p ≈ 0) |
| Screen size across OS | **Significant** — Android phones are generally larger-screened (p ≈ 0) |
| RAM across OS | **Significant** — Android vs iOS RAM profiles differ markedly (p ≈ 0) |
| Main camera across brands | **Significant** — camera specs are a key brand differentiator (p ≈ 0) |

#### Chi-Square Tests

| Test | Result |
|---|---|
| OS choice vs gender | **Not significant** — gender does not influence OS choice (p = 0.97) |
| Brand choice vs OS | **Significant** — brand and OS are strongly linked (p ≈ 0) |
| Brand choice vs occupation | **Not significant** — occupation doesn't predict brand preference (p = 0.99) |

---

## Key business insights

1. **Price is driven by specs, not demographics** — RAM and internal memory are the strongest predictors of price. A user's age, salary, or occupation barely influences which price segment they buy in.

2. **iOS commands a premium** — statistically confirmed. Marketers should not assume Android and iOS buyers are price-equivalent segments.

3. **Camera MP is not the same as camera quality** — the negative correlation between price and main camera MP suggests flagship phones invest in sensor quality, not just megapixel count. A counter-intuitive but business-relevant finding.

4. **Battery and screen have converged** — brands have effectively standardised these specs. Competing on battery or screen size alone is no longer a differentiator.

5. **Brand, not occupation** determines OS and camera choice — this has implications for ad targeting: demographic targeting by job title is less effective than brand-loyalty-based targeting.

---

## Tech stack

```
Python 3.x
├── pandas          — data loading, cleaning, transformation
├── numpy           — numerical operations
├── matplotlib      — base visualisation
├── seaborn         — statistical plots (boxplot, heatmap, countplot)
└── scipy.stats     — t-test, ANOVA (f_oneway), chi-square (chi2_contingency)
```

---

## How to run

```bash
git clone https://github.com/anjalysmohan1993-sketch/mba-analytics-projects
cd mba-analytics-projects/cellphone-eda
jupyter notebook Low_Code_Notebook_Anjali.ipynb
```

Place `cellphone_data.csv` in the same directory before running.

---

## About the analyst

**Anjali S Mohan** — Data Analytics Team Lead with 7+ years of experience in real estate data, ETL pipelines, and business intelligence. Currently pursuing MBA (Specialization: Data Science & Analytics) at Jain Deemed to be University.

[LinkedIn](https://linkedin.com/in/anjali-s-mohan) · [GitHub](https://github.com/anjalysmohan1993-sketch)

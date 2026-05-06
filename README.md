# Hypertension & Cardiovascular Risk Factors — Exploratory Data Analysis

> **Can population-level health data reveal which BMI and lifestyle factors most strongly associate with hypertension and stroke outcomes?**
> This project applies exploratory data analysis to a real-world healthcare dataset to surface patterns relevant to preventive care prioritisation.

---

## Business Context

Hypertension affects around 1 in 3 adults in the UK and is one of the leading preventable causes of stroke and cardiovascular disease. Early identification of high-risk population segments is critical for NHS resource allocation, preventive care targeting, and public health policy.

This analysis approaches the dataset as a data analyst would in a healthcare consulting or public sector technology context — framing the exploration around questions that matter to decision-makers, not just descriptive statistics.

**Key questions driving the analysis:**
1. Which BMI categories carry the highest hypertension prevalence, and how steep is the gradient?
2. Do individuals with hypertension show meaningfully higher stroke rates than those without?

---

## Dataset

| Property | Detail |
|---|---|
| Source | [Kaggle — Healthcare Dataset Stroke Data](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset) |
| Records (raw) | 5,110 patient records |
| Records (cleaned) | 4,909 (after removing 201 rows with missing BMI) |
| Key variables | Age, BMI, average glucose level, smoking status, hypertension status, stroke incidence, work type, residence type |

> The dataset is not included in this repository. Download from Kaggle and place the CSV in the `data/` folder as `healthcare-dataset-stroke-data.csv`.

---

## Methodology

```
Raw data → Data profiling → Cleaning decisions → Feature engineering → Analysis → Visualisation → Insight summary
```

**1. Data profiling**
- Inspected shape (5,110 rows × 12 columns), dtypes, null counts, and value distributions
- Identified 201 missing BMI values (~3.9% of records) as the only column with nulls

**2. Cleaning decisions**
- Removed duplicate rows
- Coerced `hypertension` and `stroke` columns to numeric to ensure valid group comparisons
- Dropped rows missing BMI, hypertension, or stroke values — these are essential to both analysis questions

**3. Feature engineering**
- Binned continuous BMI into standard clinical categories using `pd.cut`:
  - Underweight: < 18.5 (337 patients)
  - Normal: 18.5–25 (1,243 patients)
  - Overweight: 25–30 (1,409 patients)
  - Obese: ≥ 30 (1,920 patients)

**4. Analysis & visualisation**
- Calculated hypertension prevalence rate per BMI group using `groupby().mean()`
- Calculated stroke rate by hypertension status using `groupby().mean()`
- Produced a crosstab (percentage breakdown) of stroke by hypertension group
- Visualised both findings as bar charts using Matplotlib

---

## Key Findings

### Finding 1 — Hypertension prevalence rises sharply with BMI

| BMI Group | Hypertension Rate |
|---|---|
| Underweight | 0.6% |
| Normal | 4.4% |
| Overweight | 8.4% |
| Obese | 14.4% |

The obese group shows a hypertension rate **24× higher** than the underweight group and **more than 3× higher** than the normal weight group. The gradient is consistent and steep, suggesting BMI is a meaningful population-level signal for hypertension risk.

### Finding 2 — Hypertension is strongly associated with stroke

| Hypertension Status | Stroke Rate |
|---|---|
| No hypertension | 3.3% |
| Hypertension | 13.3% |

Individuals with hypertension show a stroke rate **4× higher** than those without (13.3% vs 3.3%). This reinforces hypertension as a clinically significant stroke risk factor within this dataset.

> **Note:** All findings are descriptive and observational. This analysis does not establish causation and should not be used for clinical decision-making. Missing BMI values were excluded rather than imputed, which may introduce selection bias.

---

## Recommendations (analytical framing)

Based on the patterns observed, a public health or healthcare technology team might consider:

- **BMI-based screening triage** — the steep and consistent gradient across BMI groups suggests BMI could serve as a low-cost, scalable variable for hypertension risk stratification in preventive care programmes
- **Prioritising the obese group** — with a 14.4% hypertension prevalence rate, this segment represents the highest-yield population for early intervention
- **Hypertension-targeted stroke prevention** — the 4× higher stroke rate in the hypertension group supports allocating preventive care resources toward already-hypertensive patients as a stroke risk reduction strategy

---

## Limitations & Next Steps

**Limitations**
- Dataset may not be representative of the general population
- 201 rows removed due to missing BMI — this could bias results if missingness is non-random
- EDA shows association, not causation
- No adjustment for confounders (e.g. age, glucose level, smoking interacting with BMI and hypertension)

**Next steps**
- Explore additional risk factors: age distribution by hypertension status, glucose level patterns, smoking status
- Check for confounding — e.g. whether the BMI–hypertension relationship is partially explained by age
- Build a baseline predictive model (logistic regression) for stroke risk

---

## Tools & Environment

| Tool | Purpose |
|---|---|
| Python 3 | Core language |
| pandas | Data loading, cleaning, groupby analysis, crosstabs |
| NumPy | Numerical operations |
| Matplotlib | Bar chart visualisations |
| Jupyter Notebook | Analysis environment |
| Git & GitHub | Version control and documentation |

---

## Repository Structure

```
hypertension-risk-factors-eda/
│
├── Hypertension_Risk_Factors_EDA.ipynb   # Main analysis notebook
├── requirements.txt                       # Python dependencies
├── README.md                              # This file
└── data/                                  # Add dataset here (not tracked)
    └── healthcare-dataset-stroke-data.csv
```

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/usamah-bit/hypertension-risk-factors-eda.git
cd hypertension-risk-factors-eda

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download the dataset from Kaggle and place in data/ folder

# 4. Launch the notebook
jupyter notebook Hypertension_Risk_Factors_EDA.ipynb
```

---

## About

Built as part of a self-directed data science programme (2025–present), focused on applying analytical thinking to real-world datasets with public sector and business relevance.

**Background:** BSc Biomedical Sciences (2:1), Manchester Metropolitan University — providing domain grounding in healthcare data interpretation and clinical context.

**Connect:** [github.com/usamah-bit](https://github.com/usamah-bit) | usamah.shafi@hotmail.co.uk

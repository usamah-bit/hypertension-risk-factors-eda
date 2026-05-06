# Hypertension & Cardiovascular Risk Factors — Exploratory Data Analysis

> **Can population-level health data reveal which risk factors most strongly associate with hypertension and stroke outcomes?**
> This project applies exploratory data analysis to a real-world healthcare dataset to surface actionable patterns across BMI, age, lifestyle, and clinical variables.

---

## Business Context

Hypertension affects around 1 in 3 adults in the UK and is one of the leading preventable causes of stroke and cardiovascular disease. Early identification of high-risk population segments is critical for NHS resource allocation, preventive care targeting, and public health policy.

This analysis approaches the dataset as a data analyst would in a healthcare consulting or public sector technology context — framing the exploration around questions that matter to decision-makers, not just descriptive statistics.

**Key questions driving the analysis:**
1. Which BMI categories carry the highest hypertension prevalence, and how steep is the gradient?
2. Do individuals with hypertension show meaningfully higher stroke rates than those without?
3. Which demographic and lifestyle variables show the strongest association with hypertension status?

---

## Dataset

| Property | Detail |
|---|---|
| Source | [Kaggle — Healthcare Dataset Stroke Data](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset) |
| Size | ~5,110 patient records |
| Key variables | Age, BMI, average glucose level, smoking status, hypertension status, stroke incidence, work type, residence type |
| Target variable | `hypertension` (binary: 0 = no, 1 = yes) |

> The dataset is not included in this repository. Download from Kaggle and place the CSV in the `data/` folder as `healthcare-dataset-stroke-data.csv`.

---

## Methodology

```
Raw data → Data cleaning & validation → Exploratory analysis → Visualisation → Insight summary
```

**1. Data cleaning & profiling (pandas, NumPy)**
- Inspected shape, dtypes, null values, and value counts on all columns
- Handled missing BMI values (approximately 3.9% of records) using median imputation by age group
- Encoded categorical variables for analysis (smoking status, work type, residence type)
- Removed the single `'Other'` gender record to avoid noise in group comparisons

**2. Exploratory analysis**
- Calculated hypertension prevalence rates across BMI categories (Underweight / Normal / Overweight / Obese)
- Compared stroke rates between hypertension-positive and hypertension-negative groups
- Examined age distributions across hypertension status
- Cross-tabulated lifestyle variables (smoking, work type) against hypertension prevalence

**3. Visualisation (Matplotlib)**
- Bar chart: hypertension prevalence by BMI category
- Bar chart: stroke rate comparison across hypertension groups
- Histograms: age distribution by hypertension status
- All charts formatted for clarity with labelled axes, titles, and percentage annotations

---

## Key Findings

### Finding 1 — Hypertension prevalence rises sharply with BMI category
Hypertension rates increased progressively across BMI groups, with the obese category showing substantially higher prevalence than the normal weight group. This gradient suggests BMI is a meaningful population-level signal for hypertension risk, consistent with clinical literature.

### Finding 2 — Hypertension is associated with higher stroke rates
Individuals with hypertension in this dataset showed notably higher stroke prevalence compared to those without. This finding reinforces hypertension as a clinically significant stroke risk factor and highlights the importance of early detection and intervention.

### Finding 3 — Age is a strong correlate of hypertension status
The age distribution of hypertension-positive individuals skews significantly older than hypertension-negative individuals, indicating that age-targeted screening programmes could be a cost-effective public health intervention.

> **Note:** All findings are descriptive and observational. This analysis does not establish causation and should not be used for clinical decision-making. The dataset reflects a specific sample and may not be representative of the general population.

---

## Recommendations (analytical framing)

Based on the patterns observed, a public health or healthcare technology team might consider:

- **Prioritising BMI-based screening** — the clear gradient across BMI categories suggests BMI could serve as a low-cost triage variable for hypertension risk stratification
- **Age-banded outreach** — given the strong age skew, targeted screening campaigns for adults over 50 would reach the highest-prevalence segment most efficiently
- **Stroke prevention resourcing** — the hypertension–stroke association in this data supports allocating preventive care resources toward already-hypertensive patients as a stroke risk reduction strategy

---

## Tools & Environment

| Tool | Purpose |
|---|---|
| Python 3 | Core language |
| pandas | Data loading, cleaning, manipulation |
| NumPy | Numerical operations, missing value handling |
| Matplotlib | Visualisation |
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

Built as part of a self-directed data science programme (2025–present), focused on applying analytical skills to real-world datasets with business and public sector relevance.

**Background:** BSc Biomedical Sciences (2:1), Manchester Metropolitan University — providing domain grounding in healthcare data interpretation and clinical context.

**Connect:** [github.com/usamah-bit](https://github.com/usamah-bit) | usamah.shafi@hotmail.co.uk

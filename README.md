# Diabetes Hospital Readmission and Diabetes Medications

Exploratory analysis of whether 30-day hospital readmission among patients with diabetes is related to the diabetes medications they received and to medication changes during the stay.

**Tools:** Python, pandas, NumPy, matplotlib, seaborn, SciPy, Jupyter

## Question

Among hospitalized patients with diabetes, how does the 30-day readmission rate differ by medication, by medication status (steady, dose up, dose down, not prescribed), and by whether medications were changed during the stay?

## Data

- Source: [Diabetes 130-US Hospitals for Years 1999-2008, UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008)
- 101,766 hospital encounters from 130 US hospitals, with 23 diabetes medication columns.
- Not included in this repo. Download `diabetic_data.csv` and save it as `data/diabetic_data.csv`.
- Outcome: readmitted within 30 days (`readmitted` equal to `<30`) versus not.

## What the notebook does

1. Defines the 30-day readmission outcome and the overall rate.
2. Shows how often each medication was prescribed.
3. Tabulates readmission rate by medication and status, hiding groups with fewer than 100 encounters.
4. Compares insulin and metformin in detail.
5. Compares patients on versus not on each drug (drugs given to at least 1,000 patients), in percentage points.
6. Compares encounters with and without medication changes.
7. Runs chi-square tests on the main differences.

Each section has a plain-language explanation of what the chart shows and how to read it.

## How to run

```bash
pip install -r requirements.txt
jupyter notebook Diabetes_Readmission_by_Medications.ipynb
```

## Key findings

- Overall 30-day readmission rate: **11.2%** of 101,766 encounters.
- **Insulin** was associated with higher readmission: about 2 percentage points above patients not on insulin, and highest when the dose was changed (about 13 to 14% for dose up or down, versus about 10% for no insulin).
- **Metformin** was associated with lower readmission: about 2 percentage points below patients not on it.
- Encounters with a medication change during the stay had a higher readmission rate (**11.8%**) than those without (**10.6%**).
- Chi-square tests are included to check whether these gaps are larger than chance.

![Readmission rate by insulin and metformin status](figures/insulin_metformin_readmission.png)

## Limitations

- Comparisons are unadjusted for age, diagnoses, length of stay and illness severity.
- Results show association, not causation. Sicker patients are more likely to receive insulin or have doses changed.
- Data covers 1999 to 2008, and prescribing practice has changed since.
- Several drugs were given to very few patients, so their rates are unreliable.

## Possible next steps

Logistic regression adjusting for age, prior inpatient visits and diagnoses, to test whether the medication associations hold after accounting for patient differences.

## Repository layout

```
.
├── Diabetes_Readmission_by_Medications.ipynb
├── README.md
├── requirements.txt
├── figures/
└── data/            (add the CSV locally, it is git-ignored)
```

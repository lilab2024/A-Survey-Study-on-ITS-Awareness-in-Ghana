# Awareness and Perceived Benefits of Intelligent Transport Technologies in Ghana: Evidence from a University-Connected Sample

This repository contains the data and analytical pipeline for the paper "**Awareness and Perceived Benefits of Intelligent Transport Technologies in Ghana: Evidence from a University-Connected Sample**". The study describes familiarity with intelligent transportation systems (ITS), recognition of specific transport technologies, perceived benefits, and hypothetical service-use willingness among 480 respondents in a predominantly young, university-connected convenience sample in Ghana.

## Paper Overview

Key contributions include:

* **Awareness and Perception Profile**: Assessment of ITS familiarity, technology recognition, perceived benefits and stated willingness to use ITS-enabled services among 480 respondents, 79% of whom are aged 18–34.
* **Methodological Pipeline**: Descriptive statistics, bivariate associations (Cramér's V), ordinary least squares regression on sociodemographic correlates, K-means clustering of respondent profiles, and comparison of willingness–familiarity segments.
* **Awareness–Willingness Gap**: Stated willingness to use ITS services is high (87.5%) although only 9.6% report being very familiar with ITS; willingness is only weakly associated with familiarity and sociodemographic characteristics, and safety- and reliability-oriented benefits are rated highest.
* **Policy Implications**: Recommendations on information provision and service design, framed as perceptions within the surveyed sample rather than evidence of actual demand or readiness.

## Datasets Used

* **Ghana ITS Perception Survey**:
  * **Source**: Structured online questionnaire disseminated through university and social-media networks in southern, middle and northern Ghana (non-probability convenience sample).
  * **Data URL**: [`ITS Survey(1-494).xlsx`](https://github.com/lilab2024/A-Survey-Study-on-ITS-Awareness-in-Ghana/blob/main/ITS%20Survey(1-494).xlsx)
  * **Description**: 483 recorded responses; three respondents did not consent and answered no further items, leaving 480 valid responses. The file is the survey platform export with time-stamp, e-mail and name columns removed.
  * **Key Variables**: ITS familiarity (four levels), recognition of six listed technologies, transport-app use frequency, belief that ITS can improve transportation, willingness to learn more, willingness to use an ITS-enabled service, six benefit ratings (five-point scale), transport challenges, open-ended comments, and sociodemographic characteristics (age, gender, income, education, residence, place of upbringing).

## Code

All analysis is in `ghana_its_analysis.ipynb`, in the order of Section 4 of the paper:

| Notebook section | Paper |
|---|---|
| 1. Sample characteristics | Table A1 |
| 2. Perceived benefits | Figures 3–4 |
| 3. Familiarity and willingness by age and gender | Figures 1, 5, 6, 7 |
| 4. Technology recognition | Figure 2 |
| 5. Awareness and income versus willingness | Figures 8–9 |
| 6. Cramér's V | Table 1, Figure 10 |
| 7. Sociodemographic correlates (OLS) | Table 2 |
| 8. Respondent profiles (K-means) | Figures 11–13 |
| 9. Willingness–familiarity segments | Table 3 |

Figures are saved to `figures/` under the manuscript file names and tables to `outputs/`, including `outputs/ITS_Survey_Coded.csv`, a numeric version of the analysed items. Random procedures use `random_state = 42`.

## How to Run

```bash
pip install pandas numpy matplotlib scipy statsmodels scikit-learn openpyxl jupyter
jupyter notebook ghana_its_analysis.ipynb
```

The notebook reads `ITS Survey(1-494).xlsx` from the repository root; set the environment variable `ITS_SURVEY` to use another path.

## Citation

Please cite the paper when using the data or code. Citation details will be added on publication.

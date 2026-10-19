# Awareness and Perceived Benefits of Intelligent Transport Technologies in Ghana: Evidence from a University-Connected Sample

This repository contains the de-identified data and the analytical pipeline for the paper "**Awareness and Perceived Benefits of Intelligent Transport Technologies in Ghana: Evidence from a University-Connected Sample**". The study describes familiarity with intelligent transportation systems (ITS), recognition of specific transport technologies, perceived benefits, and hypothetical service-use willingness among 480 respondents in a predominantly young, university-connected convenience sample in Ghana.

## Paper Overview

The paper provides exploratory, descriptive evidence on how a university-connected sample in Ghana perceives ITS, in the context of rapid urbanization in Sub-Saharan Africa. Key contributions include:

* **Awareness and Perception Profile**: Assessment of ITS familiarity, technology recognition, perceived benefits and stated willingness to use ITS-enabled services among 480 respondents, 79% of whom are aged 18–34.
* **Methodological Pipeline**: Integration of descriptive statistics, bivariate associations (cross-tabulations and Cramér's V), ordinary least squares regression on sociodemographic correlates, K-means clustering of respondent profiles, and comparison of willingness–familiarity segments (Kruskal–Wallis tests, multinomial logit and within-segment logit).
* **Awareness–Willingness Gap**: Finding that stated willingness to use ITS services is high (87.5%) even though only a minority report being very familiar with ITS (9.6%), that willingness is only weakly associated with familiarity and sociodemographic characteristics, and that safety- and reliability-oriented benefits (enforcement cameras, GPS fleet management) are rated highest.
* **Policy Implications**: Recommendations on information provision, service design and the scope of further research, stated as perceptions within the surveyed sample rather than as evidence of actual demand, adoption, or institutional and infrastructure readiness.

## Datasets Used

The study uses a single primary dataset collected through a cross-sectional web-based survey:

* **Ghana ITS Perception Survey**:
  * **Source**: Structured online questionnaire (Microsoft Forms) disseminated through university and social-media networks in southern, middle and northern Ghana; non-probability convenience sample.
  * **Data URL**: [`data/ITS_Survey_Deidentified.xlsx`](https://github.com/lilab2024/A-Survey-Study-on-ITS-Awareness-in-Ghana/blob/main/data/ITS_Survey_Deidentified.xlsx)
  * **Description**: 483 responses were recorded. Three respondents did not consent to participate and answered no further items; the code excludes them, leaving 480 valid responses. The shared file is the platform export with the time-stamp, e-mail and name columns removed; the questionnaire itself did not ask for names or contact details, and the account e-mail recorded automatically by the platform is not part of the shared data. The form's running ID is kept so that rows can be referenced.
  * **Key Variables**: ITS familiarity (four levels); recognition of six listed technologies (multiple choice); frequency of transport-app use; belief that ITS can improve transportation; willingness to learn more; willingness to use an ITS-enabled service; ratings of six benefit items on a five-point scale (smart signals, transit apps, tolling, enforcement cameras, GPS fleet management, self-driving/connected vehicles); transport challenges (multiple choice); open-ended comments; and sociodemographic characteristics (age, gender, income, education, current residence, place of upbringing).
  * **Coding**: Columns are addressed by position because the export has no stable header text. The full codebook (answer text → numeric value) is in Section 0 of the notebook, and running the notebook writes `outputs/ITS_Survey_Coded.csv`, a numeric version of the analysed items derived from that codebook.

## Repository Structure

```
data/ITS_Survey_Deidentified.xlsx   de-identified survey export (483 rows)
ghana_its_analysis.ipynb            the complete analysis, in the order of Section 4 of the paper
figures/                            written by the notebook; file names match the manuscript
outputs/                            tables (CSV) written by the notebook
README.md
```

## Analytical Pipeline

All analysis is in one notebook, `ghana_its_analysis.ipynb`. Each section produces one figure or table of the paper; nothing else is computed.

| Notebook section | Paper | Output files |
|---|---|---|
| 0. Setup, codebook, data loading | §3.2 | — |
| 1. Sample characteristics | §4.1, Table A1 | `outputs/tableA1_sample_characteristics.csv` |
| 2. Perceived benefits | §4.1, Figures 3–4 | `figures/benefit ranking.png`, `figures/likert_stacked.png` |
| 3. Familiarity and willingness by age and gender | §4.1–4.2, Figures 1, 5, 6, 7 | `figures/Age Group.png`, `age_use.png`, `gender_fam.png`, `gender_vs_willingness.png` |
| 4. Technology recognition | §4.1, Figure 2 | `figures/familiar_techs_bar.png`, `outputs/fig4_technology_recognition.csv` |
| 5. Awareness and income versus willingness | §4.2, Figures 8–9 | `figures/income_vs_willingness.png`, `awareness_vs_willingness.png` |
| 6. Cramér's V | §4.2, Table 1, Figure 10 | `outputs/table1_cramers_v.csv`, `figures/cramersv.png` |
| 7. Sociodemographic correlates (OLS) | §4.3, Table 2 | `outputs/table2_sociodemographic_correlates.csv` |
| 8. Respondent profiles (K-means) | §4.4, Figures 11–13 | `figures/fig12_attitudes.png`, `fig13_tech_engagement.png`, `fig14_adoption_readiness.png`, `outputs/cluster_diagnostics.csv` |
| 9. Willingness–familiarity segments | §4.6, Table 3 | `outputs/table3_panelA.csv`, `table3_panelB_*.csv`, `table3_panelC.csv` |
| 9b. Coded data export | — | `outputs/ITS_Survey_Coded.csv` |
| 10. Data checks | §3.2 | codebook coverage, multi-select audit (printed) |

Notes on specific items:

* **Cramér's V (Table 1, Figure 10)**: Gender is coded male / female / other; "Prefer not to say" is kept as a category for age, income, current residence and place of upbringing, and "No Income" is a separate income level. Each pair is computed on the respondents who answered both items.
* **Table 2**: Ordinary least squares with the ordinal outcomes treated as numeric; "Prefer not to say" is treated as missing, giving n = 410. Classical and HC3 robust p-values are both printed.
* **Figures 11–13**: K-means with k = 3 fixed for comparability across the figures. `outputs/cluster_diagnostics.csv` holds the silhouette scores for k = 2 to 5 and the bootstrap adjusted Rand indices referred to in Section 4.4.
* **Section 4.5** (open-ended responses) was summarised manually and has no code.

## Requirements

* Python 3.9 or later
* `pandas`, `numpy`, `matplotlib`, `scipy`, `statsmodels`, `scikit-learn`, `openpyxl`, `jupyter`

```bash
pip install pandas numpy matplotlib scipy statsmodels scikit-learn openpyxl jupyter
```

## How to Run

```bash
jupyter notebook ghana_its_analysis.ipynb
```

Run the cells from top to bottom. The notebook reads `data/ITS_Survey_Deidentified.xlsx` by default; set the environment variable `ITS_SURVEY` to use another path. Figures are saved at 300 dpi to `figures/` under the file names used in the manuscript, and tables to `outputs/`. All random procedures (K-means, bootstrap) use `random_state = 42`, so repeated runs reproduce the published numbers exactly.

## Citation

Please cite the paper when using the data or code. Citation details will be added on publication.

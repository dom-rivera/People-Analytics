# People Analytics Portfolio

Hands-on people analytics projects built from scratch in Python and Google Colab. Each project starts with a business question, works through cleaning, analysis and modeling, and ends with a plain-language answer for HR leaders.

This repository also tracks a practice roadmap of **16 free HR datasets**, grouped by the people analytics skill each one trains.

---

## Table of contents

- [Current project: Employee attrition (IBM)](#current-project-employee-attrition-ibm)
- [How to run](#how-to-run)
- [Practice roadmap: 16 datasets](#practice-roadmap-16-datasets)
  - [1. Attrition and turnover](#1-attrition-and-turnover)
  - [2. Core HRIS, recruitment and data modeling](#2-core-hris-recruitment-and-data-modeling)
  - [3. Promotion, performance and talent](#3-promotion-performance-and-talent)
  - [4. Compensation and pay equity](#4-compensation-and-pay-equity)
  - [5. Absence and wellbeing](#5-absence-and-wellbeing)
  - [6. Employee surveys and engagement](#6-employee-surveys-and-engagement)
  - [7. Workforce planning](#7-workforce-planning)
  - [8. Statistics, networks and text](#8-statistics-networks-and-text)
- [Skills map](#skills-map)
- [Learning path](#learning-path)
- [Data ethics](#data-ethics)
- [Sources](#sources)

---

## Current project: Employee attrition (IBM)

**Notebook:** [`People_Analytics_Attrition.ipynb`](People_Analytics_Attrition.ipynb)
**Business question:** Who is leaving, why, and where should HR focus retention effort?
**Data:** [IBM HR Analytics Employee Attrition & Performance](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset), a fictional dataset of 1,470 employees and 35 columns created by IBM data scientists.

### Lessons

| # | Lesson | What it covers | Status |
| --- | --- | --- | --- |
| 1 | Load and inspect | Shape, data types, missing values, summary statistics, variable types | Done |
| 2 | Clean and prepare | Drop constant columns, 0/1 outcome, ordinal labels, age/tenure/income bands | Done |
| 3 | Descriptive analytics | Attrition rate, leavers and share of leavers by segment; crosstabs | In progress |
| 4 | Visualization | Charts an HR leader can read in five seconds | Planned |
| 5 | Statistical testing | Chi-square, Mann-Whitney, effect sizes | Planned |
| 6 | Explanatory modeling | Logistic regression and odds ratios | Planned |
| 7 | Predictive modeling | Model comparison, class imbalance, decision thresholds | Planned |
| 8 | Business story | Cost of attrition, recommendations, one-page memo | Planned |

### Findings so far

- **Attrition rate:** 237 of 1,470 employees left (**16.1%**). That is somewhat above typical voluntary turnover benchmarks (about 13% in the US in 2025, and 8–17% across Philippine industries). The comparison is rough because the dataset has no time period and no voluntary/involuntary split.
- **Data quality:** no missing values. Three columns are constant for every employee (`EmployeeCount`, `StandardHours`, `Over18`) and were dropped.
- **Variable types:** `JobSatisfaction`, `Education`, `PerformanceRating` and similar columns are **ordinal** codes, not true measurements, so averages of them need care.
- **Rating inflation:** `PerformanceRating` only contains 3 (Excellent) and 4 (Outstanding), so it barely helps explain attrition.

---

## How to run

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dom-rivera/People_Analytics/blob/main/People_Analytics_Attrition.ipynb)

1. Click the badge to open the notebook in Colab.
2. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) and upload the CSV using the folder icon on the left.
3. Run all cells (**Runtime → Run all**).

---

## Practice roadmap: 16 datasets

Most popular HR datasets are **synthetic**. Use them to learn methods, then test yourself on the **real** ones. Most are also cross-sectional snapshots, so "prediction" really means classification at one point in time.

### 1. Attrition and turnover

#### IBM HR Analytics Employee Attrition & Performance
[Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) · Synthetic · 1,470 employees × 35 columns, no missing values, about 16% attrition.

- [x] Calculate the overall attrition rate and attrition rate by department, job role, and overtime
- [ ] Chi-square tests: is attrition independent of overtime, business travel, marital status?
- [ ] Compare monthly income of leavers vs stayers (t-test or Mann-Whitney) with an effect size
- [ ] Logistic regression on attrition; interpret odds ratios in plain language
- [ ] Random forest or gradient boosting; compare AUC, precision and recall with the logistic model
- [ ] Handle class imbalance (class weights or SMOTE) and pick a decision threshold that fits the business cost
- [ ] Explain the model with SHAP values; write three retention recommendations
- [ ] Estimate the cost of attrition (e.g. 50% of annual salary per leaver) and the savings from a 10% reduction

#### HR Analytics / HR_comma_sep
[Kaggle mirror](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction) · Synthetic · 14,999 rows × 10 columns: satisfaction, last evaluation, projects, monthly hours, tenure, accident, promotion, department, salary band.

- [ ] Scatter plot of satisfaction vs last evaluation, coloured by who left
- [ ] K-means clustering of leavers; name the clusters (burned-out stars, disengaged, underused)
- [ ] Workload analysis: attrition by number of projects and monthly hours bands
- [ ] Decision tree for attrition and turn its top rules into a manager checklist

#### Employee turnover (Babushkin)
[AIHR case with data download](https://www.aihr.com/blog/applying-survival-analysis-reduce-employee-turnover-practical-case/) · Real · 1,785 employees, tenure in months, prepared for survival analysis.

- [ ] Kaplan-Meier curve: median tenure and the months when exits peak
- [ ] Compare survival curves by hiring channel, industry and gender (log-rank test)
- [ ] Cox proportional hazards model; check the proportional hazards assumption
- [ ] Write why survival analysis beats a simple turnover rate for this question

### 2. Core HRIS, recruitment and data modeling

#### Human Resources Data Set (Huebner & Patalano, HRDataset_v14)
[Kaggle](https://www.kaggle.com/datasets/rhuebner/human-resources-data-set) · Synthetic · Built for a graduate HR metrics course. Demographics, department, position, pay, manager, hire and termination dates and reasons, recruitment source, performance, engagement, satisfaction, absences.

- [ ] Clean the data: fix date formats, standardize categories, derive age and tenure
- [ ] Build a headcount and turnover KPI page: headcount, hires, exits, turnover rate by year
- [ ] Termination reason analysis: voluntary vs involuntary, top reasons by department
- [ ] Recruitment source quality: compare performance score and tenure by hiring source
- [ ] Manager analysis: highest turnover and lowest engagement (watch small team sizes)
- [ ] Pay analysis: pay rate by position and gender; flag outliers

#### Employee/HR Dataset (All In One)
[Kaggle](https://www.kaggle.com/datasets/ravindrasinghrana/employeedataset) · Synthetic · Separate tables for employees, engagement survey, recruitment, and training & development (about 3,000 rows each).

- [ ] Load the tables into SQLite or PostgreSQL and draw the data model (keys and joins)
- [ ] Write SQL for 10 standard HR metrics (headcount, turnover, average tenure, training hours per employee, cost per hire)
- [ ] Recruitment funnel: applicants by status and conversion rates by job title
- [ ] Training effectiveness: do employees with more training have higher performance ratings?
- [ ] Build a multi-page Power BI or Tableau dashboard joining all tables

### 3. Promotion, performance and talent

#### HR Analytics: Employee Promotion Data
[Kaggle](https://www.kaggle.com/datasets/arashnic/hr-ana) · Synthetic · 54,808 employees: department, region, education, gender, recruitment channel, trainings, age, previous rating, tenure, KPIs met, awards, training score, promoted.

- [ ] Promotion rate by department, education, gender and recruitment channel
- [ ] Adverse impact check: apply the four-fifths (80%) rule to promotion rates by gender
- [ ] Logistic regression: is gender still linked to promotion after controlling for KPIs, rating and awards?
- [ ] Gradient boosting classifier; report F1 (classes are imbalanced, about 9% promoted)
- [ ] Fairness audit of the model: compare false negative rates across groups

#### HR Analytics: Job Change of Data Scientists
[Kaggle](https://www.kaggle.com/arashnic/hr-analytics-job-change-of-data-scientists) · CC0 · About 19,000 candidates: experience, education, company size and type, training hours, city development index, looking for a job change.

- [ ] Missing data audit: which columns are missing, and is missingness itself predictive?
- [ ] Impute missing values two ways and compare model results
- [ ] Which candidate profiles are most open to a move? Translate into a sourcing strategy
- [ ] Target encoding for high-cardinality city codes

### 4. Compensation and pay equity

#### Glassdoor Gender Pay Gap
[Kaggle](https://www.kaggle.com/datasets/nilimajauhari/glassdoor-analyze-gender-pay-gap) · Synthetic · 1,000 employees: job title, gender, age, performance evaluation, education, department, seniority, base pay, bonus.

- [ ] Raw (unadjusted) gap: median and mean base pay, men vs women
- [ ] Adjusted gap: regress log(base pay) on gender plus controls; read the gender coefficient as a % gap
- [ ] Decompose: how much of the raw gap is explained by job title (occupational sorting)?
- [ ] Bonus gap and total compensation gap
- [ ] One-page pay equity memo with the remediation cost to close the adjusted gap

#### UK Gender Pay Gap reporting (2018–2023)
[GOV.UK service](https://gender-pay-gap.service.gov.uk/) · [Kaggle compilation](https://baselight.app/u/kaggle/dataset/umerhaddii_uk_gender_pay_gap_data_2018_2023) · Real · Mandatory annual reports from UK employers with 250+ staff.

- [ ] Distribution of median gaps by industry (SIC code) and employer size
- [ ] Trend: did gaps narrow from 2018 to 2023? Paired comparison for employers present every year
- [ ] Pay quartile analysis: share of women in the top quartile vs the overall gap
- [ ] Benchmark one sector and write how a company in it compares

### 5. Absence and wellbeing

#### Absenteeism at Work (UCI)
[UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/445/absenteeism+at+work) · Real · 740 absence records from a Brazilian courier company, July 2007–July 2010, CC BY 4.0. Python: `pip install ucimlrepo`, id 445.

- [ ] Bradford Factor per employee (spells² × days) and the top 10% of absence
- [ ] Absence hours by reason, month, day of week and season
- [ ] Is distance to work or workload related to absence hours? (Spearman correlation)
- [ ] Model absence hours with Poisson and negative binomial regression; compare fit
- [ ] Separate levers HR controls (workload, commute support) from health factors it should not act on directly

### 6. Employee surveys and engagement

#### Employee Survey Responses (Pierce County, WA)
[Maven Analytics Data Playground](https://mavenanalytics.io/data-playground/employee-survey-responses) · Real · 499 responses × 25 fields from a government engagement survey. Public domain.

- [ ] Favorability score per question (% agree + strongly agree); rank highest and lowest
- [ ] Results by department and role, suppressing any group under 5 respondents
- [ ] Scale reliability: Cronbach's alpha for the engagement items
- [ ] Exploratory factor analysis: which questions group into themes?
- [ ] Key driver analysis: which items best predict overall engagement or satisfaction
- [ ] One-page action plan based on the low-favorability, high-impact items

#### Canada Public Service Employee Survey (PSES)
[2022/2023 results](https://baselight.app/u/canadagov/dataset/canada_gov_9f9501f3_8188_4386_87ba_50730a979044) · Real · 189,584 respondents across 90 federal departments, aggregated by department, demographic group and year.

- [ ] Trend in engagement and wellbeing questions across survey waves
- [ ] Gaps between demographic groups on inclusion and harassment items
- [ ] Benchmark departments on leadership questions
- [ ] Survey results dashboard with filters for department and demographic group

### 7. Workforce planning

#### US OPM Federal Workforce Data
[Data downloads](https://data.opm.gov/explore-data/data/data-downloads) · [Getting started](https://data.opm.gov/info-and-help/getting-started) · Real · Record-level federal employment, accessions and separations, published monthly. Older FedScope cubes on [opm.gov](https://www.opm.gov/data/datasets/).

- [ ] Read the data dictionary and load one month of employment data (use Python or DuckDB, not Excel)
- [ ] Headcount stock-and-flow: opening headcount + accessions − separations = closing headcount, by agency
- [ ] Separation mix: retirement vs resignation vs other, by agency and age group
- [ ] Retirement risk: share of each agency's workforce aged 55+ with long service
- [ ] Forecast headcount 12 months ahead with a simple time-series model
- [ ] Scenario model: headcount in 3 years if hiring stays flat and separations rise 10%

### 8. Statistics, networks and text

#### peopleanalyticsdata (Keith McNulty)
[Free book](https://peopleanalytics-regression-book.org) · [R package](https://keithmcnulty.r-universe.dev/peopleanalyticsdata) · Fictional · Datasets from *Handbook of Regression Modeling in People Analytics*.

- [ ] Work through the book's chapter exercises in order
- [ ] Linear regression on the undergraduate test data
- [ ] Binomial logistic regression on salespeople promotion
- [ ] Multinomial and ordinal regression on the performance-rating datasets
- [ ] Hierarchical (mixed) model: employees nested in teams
- [ ] Survival analysis chapter

#### onadata (Keith McNulty)
[Free book](https://ona-book.org) · [R package](https://rdrr.io/cran/onadata/) · [Python port](https://pypi.org/project/onadata/) · Datasets from *Handbook of Graphs and Networks in People Analytics*.

- [ ] Build a graph from an edge list; compute degree, betweenness and eigenvector centrality
- [ ] Community detection (Louvain) and compare communities with formal departments
- [ ] Identify brokers and isolated people; write what HR would do with each

#### Enron Email Corpus
[CMU Enron dataset](https://www.cs.cmu.edu/~enron/) · Real · About 619,000 emails from 158 employees.

- [ ] Build a sender–recipient network from email headers (metadata only)
- [ ] Compare centrality rankings across measures
- [ ] Network density over time: before vs during the 2001 crisis
- [ ] Short note on the privacy rules required before running ONA on real employee email

#### Glassdoor Job Reviews
[Kaggle](https://www.kaggle.com/datasets/davidgauthier/glassdoor-job-reviews-2) · Real reviews (several GB) · Ratings, pros, cons, job title, employment status by company.

- [ ] Sample 50,000 reviews of one industry to keep it manageable
- [ ] Sentiment scoring of pros and cons text; compare with star ratings
- [ ] Topic modeling (BERTopic or LDA) on cons: what drives low ratings?
- [ ] Compare current vs former employees' themes (an exit-interview proxy)

---

## Skills map

| Skill area | Datasets |
| --- | --- |
| Data cleaning, SQL, HR metrics | Huebner, All-in-One |
| Dashboards and storytelling | Huebner, All-in-One, Pierce County |
| Statistical inference | IBM, Glassdoor pay gap |
| Regression (linear, logistic, ordinal, multilevel) | peopleanalyticsdata, IBM, Promotion |
| Predictive modeling and explainability | IBM, HR_comma_sep, Promotion |
| Survival analysis | Babushkin |
| Pay equity and DEI | Glassdoor pay gap, UK GPG, Promotion, Canada PSES |
| Recruitment analytics | Huebner, All-in-One, Job Change |
| Survey analytics | Pierce County, Canada PSES |
| Absence and wellbeing | UCI Absenteeism |
| Workforce planning and forecasting | US OPM |
| Organizational network analysis | onadata, Enron |
| Text analytics on employee voice | Glassdoor reviews |

## Learning path

1. Huebner or All-in-One for SQL, metrics and a first dashboard
2. IBM for statistics and attrition modeling *(current project)*
3. Babushkin for survival analysis
4. Glassdoor pay gap, then UK GPG, for pay equity
5. Pierce County, then Canada PSES, for survey analytics
6. McNulty's two free books for regression depth and ONA
7. US OPM as a real-world capstone: a full workforce plan for one agency

## Data ethics

- All data here is public, synthetic or anonymized. No real employee data from any employer is used.
- Group results under about 5–10 people are not reported, since small cells can identify individuals.
- Models are checked for fairness across gender and age before any recommendation.
- Findings are described as associations, not causes, unless the design supports a causal claim.

## Sources

- [AIHR – 9 HR datasets to practice people analytics](https://www.aihr.com/blog/hr-data-sets-people-analytics/)
- [AIHR – Survival analysis to reduce employee turnover](https://www.aihr.com/blog/applying-survival-analysis-reduce-employee-turnover-practical-case/)
- [Mercer – Results of the 2025 US Turnover Surveys](https://www.imercer.com/content/article/employee-turnover.aspx)
- [Malaya Business Insight – Mercer Philippine attrition figures](https://malaya.com.ph/business/enterprise/9-in-10-firms-have-incentive-plans-wages-to-rise-5-5)
- [UCI – Absenteeism at Work](https://archive.ics.uci.edu/dataset/445/absenteeism+at+work)
- [OPM – Federal Workforce Data downloads](https://data.opm.gov/explore-data/data/data-downloads)
- [Maven Analytics – Employee Survey Responses](https://mavenanalytics.io/data-playground/employee-survey-responses)
- [peopleanalyticsdata package](https://keithmcnulty.r-universe.dev/peopleanalyticsdata)
- [Network and sentiment analysis of Enron emails (F1000Research)](https://f1000research.com/articles/13-1485)

---

**Author:** [dom-rivera](https://github.com/dom-rivera)

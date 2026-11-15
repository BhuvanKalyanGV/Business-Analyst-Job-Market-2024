# Business Analyst Job Market 2024 – LinkedIn Job Market Analysis

## Project Overview

This project analyses Business Analyst job advertisements collected from LinkedIn during January 2024. The objective is to identify patterns in job demand, employer requirements, geographic distribution and the capabilities requested across Business Analyst roles.

The project was developed to provide a US consulting company with insights into the Business Analyst job market and consists of two stages:

- **Assignment 1 – Preliminary Analysis:** Explores job characteristics, geographic distribution and skill requirements using integrated LinkedIn datasets.
- **Assignment 2 – Individual Analysis (RQ3):** Conducts a deeper investigation into the capabilities most frequently required in Business Analyst job advertisements.

The project follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** framework, covering business understanding, data understanding, data preparation, analysis and evaluation.

---

# 1. Business Objective

The main objective is to identify meaningful patterns in Business Analyst-related employment opportunities and provide useful labour-market insights.

The project investigates:

- Types of Business Analyst roles being advertised.
- Employers advertising Business Analyst positions.
- Geographic distribution of job opportunities.
- Skills and capabilities frequently requested by employers.
- Data quality issues and limitations affecting the analysis.

The findings are intended to support an understanding of employer requirements rather than provide a complete representation of the entire Business Analyst labour market.

---

# 2. Research Questions

### RQ1 – Job Characteristics and Demand

**What types of Business Analyst roles are being advertised, and how is demand distributed across job titles and employers?**

This analysis examines job titles, employers, job levels, job types and the concentration of advertisements across titles and companies.

### RQ2 – Geographic Distribution

**Where are Business Analyst job opportunities concentrated geographically?**

This analysis examines search-country distributions, actual job locations, major cities and geographic concentration.

The distinction between `search_country` and `job_location` is maintained because they represent different geographic information.

### RQ3 – Skills and Capability Requirements

**What capabilities are most frequently required in Business Analyst job advertisements?**

This research question is explored in two stages:

- Assignment 1 examines individual skill frequencies and preliminary skill patterns.
- Assignment 2 provides a more detailed analysis of skill prevalence, capability categorisation and category co-occurrence.

---

# 3. Assignment 1 – Preliminary Analysis

## 3.1 Dataset Sources

The preliminary analysis uses three related LinkedIn datasets:

**1. LinkedIn Job Postings**

Contains structured job advertisement information, including:

- `job_link`
- `job_title`
- `company`
- `job_location`
- `search_city`
- `search_country`
- `job_level`
- `job_type`
- `first_seen`

**2. Job Skills**

Contains skills associated with individual advertisements. The `job_skills` field stores multiple comma-separated skill labels.

**3. Job Summary**

Contains unstructured job advertisement information, including responsibilities, qualifications, education, experience and other requirements.

The three datasets were integrated using `job_link`.

## 3.2 Dataset Preparation

The initial extraction identified 3,813 Business Analyst postings. An alternative dataset provided by a teammate contained 4,576 postings.

The comparison identified 763 additional `job_link` values, and the 4,576-record dataset was retained as the revised starting population.

The job-posting, skills and summary datasets were integrated using an inner join.

### Final Integrated Dataset

| Measure | Result |
|---|---:|
| Starting population | 4,576 |
| Final integrated postings | 4,440 |
| Variables | 11 |
| Integration coverage | 97.03% |
| Excluded postings | 136 |
| Excluded percentage | 2.97% |
| Missing values in final dataset | 0 |
| Duplicate job links | 0 |
| Unique job links | 4,440 |

All 136 excluded postings were missing both skills and job-summary information.

## 3.3 Data Quality Assessment

The preliminary dataset was assessed for completeness, uniqueness, validity, consistency, timeliness and skill-data quality.

Key observations included:

- All 11 variables in the final integrated dataset were complete.
- All 4,440 job links were unique.
- The `first_seen` dates ranged from 12 January 2024 to 17 January 2024.
- The mean number of skills per advertisement was 25.01, with a median of 22.
- Duplicate skill entries were identified in 435 advertisements, accounting for 779 additional entries.

Repeated skill entries were removed when calculating skill frequencies.

## 3.4 Preliminary Findings

### RQ1 – Job Characteristics and Demand

The most common job title was **Business Analyst**, with 988 postings.

Other frequently occurring titles included Senior Business Analyst, JDE Business Analyst (Supply Chain), JD Edwards Business Analyst and IT Business Analyst.

The largest employer by number of postings was LATICRETE International, with 296 postings, followed by Dice and Tata Consultancy Services.

The results suggest that Business Analyst opportunities were distributed across a wide range of job titles and employers.

### RQ2 – Geographic Distribution

The United States accounted for 3,638 postings (82.0%) based on the search-country field.

Other search-country distributions included:

- United Kingdom – 335 (7.5%)
- Canada – 246 (5.5%)
- Australia – 221 (5.0%)

Frequently occurring actual job locations included New York, Atlanta, Boston, London and Chicago.

### RQ3 – Preliminary Skill Requirements

The most frequently recorded skills included:

| Skill | Job Count | Percentage |
|---|---:|---:|
| Communication | 2,069 | 46.6% |
| Business Analysis | 1,943 | 43.8% |
| Problem Solving | 1,511 | 34.0% |
| Project Management | 1,507 | 33.9% |
| Data Analysis | 1,452 | 32.7% |
| SQL | 1,044 | 23.5% |
| Analytical Skills | 902 | 20.3% |
| Requirements Gathering | 776 | 17.5% |
| Teamwork | 664 | 15.0% |
| Agile | 657 | 14.8% |

These preliminary findings indicated that Business Analyst roles commonly involve a combination of business, analytical, technical and interpersonal skills.

---

# 4. Assignment 2 – Individual Analytical Report (RQ3)

## 4.1 Research Objective

Assignment 2 extends the preliminary skill analysis by investigating:

**What capabilities are most frequently required in Business Analyst job advertisements?**

The analysis focuses on identifying frequently mentioned skills, grouping them into meaningful capability categories and examining which categories commonly occur together.

## 4.2 Dataset

The individual analysis uses `FINAL_US_BA_3606_JOBS.csv`, containing 3,610 US Business Analyst advertisements with available skill information.

The working dataset contains seven variables:

- `job_link`
- `job_title`
- `job_location`
- `search_country`
- `explicit_ba_title`
- `location_country_issue`
- `job_skills`

All 3,610 records had explicit Business Analyst titles, available skill information and no flagged location-country issues.

The working dataset contains four more records than the 3,606 specified in the original analysis plan. The 3,610-record dataset was retained for the individual analysis.

## 4.3 Data Cleaning and Standardisation

The extracted skill information was cleaned before performing the analysis.

Key data preparation steps included:

- Parsing comma-separated skill entries.
- Removing repeated skill labels within individual advertisements.
- Standardising capitalisation and whitespace.
- Removing leading asterisk markers and extraction artefacts.
- Consolidating equivalent skill-name variations.
- Retaining distinct technical capabilities separately.

The cleaning process reduced the skill entries from 92,719 to 92,090.

The 700 most frequently occurring standardised skill labels were manually reviewed. Of these, 653 were retained for capability analysis and 47 were excluded.

The retained labels accounted for 51,144 of the 92,090 cleaned skill mentions (55.54%).

## 4.4 Skill Prevalence Analysis

Each retained skill was counted once per advertisement to prevent repeated mentions from inflating its frequency.

Skill prevalence was calculated using:

**Skill Prevalence (%) = (Number of advertisements mentioning a skill ÷ 3,610) × 100**

The most frequently mentioned individual capabilities were:

| Capability | Job Count | Prevalence |
|---|---:|---:|
| Business Analysis | 1,480 | 41.00% |
| Data Analysis | 1,255 | 34.76% |
| Problem Solving | 1,239 | 34.32% |
| Project Management | 1,235 | 34.21% |
| Communication | 1,094 | 30.30% |
| SQL | 921 | 25.51% |
| Analytical Skills | 750 | 20.78% |
| Requirements Gathering | 634 | 17.56% |
| Communication Skills | 616 | 17.06% |
| Excel | 592 | 16.40% |

## 4.5 Capability Categorisation

The 653 retained skill labels were organised into nine capability categories:

1. Business Analysis & Requirements
2. Technical & Data
3. Analytical & Problem-Solving
4. Communication & Interpersonal
5. Project & Process Management
6. Business & Domain Knowledge
7. Personal & Professional Attributes
8. Testing & Quality Assurance
9. Methodologies & Frameworks

Each retained skill label was assigned one primary category.

The most frequently represented categories were:

| Capability Category | Job Count | Prevalence |
|---|---:|---:|
| Technical & Data | 2,977 | 82.47% |
| Business Analysis & Requirements | 2,701 | 74.82% |
| Communication & Interpersonal | 2,634 | 72.96% |
| Analytical & Problem-Solving | 2,519 | 69.78% |
| Project & Process Management | 2,144 | 59.39% |
| Business & Domain Knowledge | 1,500 | 41.55% |
| Personal & Professional Attributes | 1,260 | 34.90% |
| Testing & Quality Assurance | 1,252 | 34.68% |
| Methodologies & Frameworks | 1,213 | 33.60% |

Category percentages are not mutually exclusive because an advertisement may contain capabilities from multiple categories.

## 4.6 Capability Category Co-occurrence

A category-level co-occurrence analysis was performed to identify which capability areas appeared together within the same advertisements.

Each advertisement was counted once for each unique category pair.

The most common combinations were:

| Capability Category Combination | Job Count | Prevalence |
|---|---:|---:|
| Business Analysis & Requirements + Technical & Data | 2,260 | 62.60% |
| Communication & Interpersonal + Technical & Data | 2,227 | 61.69% |
| Analytical & Problem-Solving + Technical & Data | 2,192 | 60.72% |
| Analytical & Problem-Solving + Communication & Interpersonal | 2,097 | 58.09% |
| Business Analysis & Requirements + Communication & Interpersonal | 2,069 | 57.31% |

The findings indicate that technical capabilities frequently appear alongside business analysis, analytical and communication requirements.

## 4.7 Key Interpretation

The individual analysis suggests that Business Analyst roles require a combination of technical, analytical, business and interpersonal capabilities.

Technical & Data capabilities were represented in 82.47% of advertisements, while Business Analysis & Requirements appeared in 74.82%.

The most common category combination was Business Analysis & Requirements with Technical & Data, appearing together in 62.60% of advertisements.

These results highlight the importance of developing a balanced capability set rather than focusing on technical proficiency alone.

## 4.8 Limitations

The findings should be interpreted within the scope of the selected dataset.

Important limitations include:

- The analysis covers 3,610 LinkedIn advertisements associated with the United States and collected during 2024.
- Extracted skill labels may not capture every capability in the original advertisements.
- Only the 700 most frequent standardised labels were manually reviewed.
- The 653 retained labels accounted for 55.54% of cleaned skill mentions.
- Manual classification involved judgement, and some capabilities could reasonably fit multiple categories.
- Skill mention frequency does not directly measure the importance of a capability to job performance or actual employer demand.

---

# 5. Tools and Technologies

The project uses the following tools and technologies:

- **Python** – Data processing and analysis.
- **Pandas** – Data manipulation and cleaning.
- **Matplotlib** – Data visualisation.
- **Seaborn** – Exploratory data visualisation.
- **Google Colab** – Development and execution of Python notebooks.
- **GitHub** – Version control and project documentation.

---

# 6. Visualisations

The repository includes visualisations supporting the preliminary and individual analyses.

### Assignment 1 – Preliminary Analysis

Visualisations cover:

- Integration coverage and data completeness.
- Job-link uniqueness.
- Job-level and job-type distributions.
- Search-country distribution.
- First-seen date distribution.
- Skills-per-job distribution.
- Duplicate skill analysis.
- Top job titles and employers.
- Job-title and company concentration.
- Geographic distribution.
- Frequently occurring skills.

### Assignment 2 – Individual Analysis

The individual analysis includes:

- Prevalence of Business Analyst capability categories.
- Most commonly co-occurring capability categories.

These visualisations support the findings presented in the individual analytical report.

---

# 7. Repository Structure

```text
Business-Analyst-Job-Market-2024/
│
├── README.md
├── LICENSE
│
├── report/
│   ├── a3196649_Report.docx
│   └── Individual Analytical Report.docx
│
├── code/
│   ├── Individual_work.ipynb
│   ├── Final_Preliminary_Exploration.ipynb
│   └── Assignment 2 Python Colab Notebook (.ipynb)
│
├── extracted datasets/
│   ├── Business_Analyst_Integrated_Dataset.xlsx
│   ├── Individual_BA_Integrated_Dataset.xlsx
│   ├── business_analyst_jobs.csv
│   ├── business_analyst_skills.csv
│   └── BA_job_summary.csv
│
└── Visualisations/
    ├── dq analysis/
    └── final preliminary analysis/
```

*The repository structure above summarises the main project components. Refer to the repository for the complete file listing.*

---

# 8. How to Access the Analysis

1. Clone or download this repository.
2. Open the required Jupyter Notebook from the `code/` directory.
3. For Google Colab, upload the notebook or open it through the GitHub integration.
4. Ensure the relevant datasets are accessible to the notebook.
5. Run the notebook cells in sequence to reproduce the analysis.

The Assignment 2 notebook contains the Python workflow for the individual RQ3 analysis, including data preparation, skill standardisation, prevalence calculations, capability classification, co-occurrence analysis and visualisation.

Dataset paths and file locations may need to be adjusted depending on the execution environment.

---


---

## About

An analytical project exploring the 2024 Business Analyst job market using LinkedIn job advertisements, with a focus on job demand, geographic distribution, employer requirements and Business Analyst capabilities.

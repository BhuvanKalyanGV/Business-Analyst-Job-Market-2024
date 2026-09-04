# Business Analyst Job Market 2024 — LinkedIn Job Market Analysis

## Overview

This project analyses the 2024 Business Analyst job market using LinkedIn job advertisements. The analysis was developed to provide a US consulting company with insights into the demand for Business Analyst-related roles, employer requirements, geographic distribution, and the skills requested by employers.

The project uses LinkedIn job-posting, job-skills and job-summary datasets. Due to the size of the available data and the scope of the project, the analysis was narrowed to three main research areas:

1. **Job characteristics and demand**
2. **Geographic distribution**
3. **Skills associated with Business Analyst roles**

The analysis follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** framework, with particular emphasis on business understanding, data understanding, data preparation, preliminary analysis and evaluation of data quality.

---

## Business Objective

The objective of this project is to identify meaningful patterns in Business Analyst-related employment opportunities and provide useful labour-market insights for a consulting company.

The analysis focuses on:

- The types of Business Analyst roles being advertised
- The employers advertising Business Analyst positions
- The geographic distribution of opportunities
- The skills most frequently requested by employers
- The quality and limitations of the available data

The preliminary analysis is intended to identify meaningful patterns and establish a basis for further analysis rather than provide a definitive representation of the entire 2024 Business Analyst job market.

---

## Research Questions

### RQ1 — Job Characteristics and Demand

**What types of Business Analyst roles are being advertised, and how is demand distributed across job titles and employers?**

This research question examines:

- Job titles
- Employers
- Job levels
- Job types
- Concentration of postings across titles
- Concentration of postings across employers

### RQ2 — Geographic Distribution

**Where are Business Analyst job opportunities concentrated geographically?**

This research question examines:

- Search-country distribution
- Actual job locations
- Major cities and locations
- Geographic concentration of postings

The analysis distinguishes between `search_country` and `job_location`, because the search-country field represents the country associated with the search that retrieved the job, while `job_location` represents the location associated with the advertised position.

### RQ3 — Skills Requirements

**What skills are most frequently associated with Business Analyst job advertisements?**

This research question examines:

- Individual skill frequencies
- Technical skills
- Business skills
- Soft skills
- Number of skills recorded per job
- Standardisation of obvious skill-name variations
- Duplicate skill entries within individual job postings

---

# Dataset

The project uses three related LinkedIn datasets:

### 1. LinkedIn Job Postings

Contains structured information about job advertisements, including:

- `job_link`
- `job_title`
- `company`
- `job_location`
- `search_city`
- `search_country`
- `job_level`
- `job_type`
- `first_seen`

### 2. Job Skills

Contains the skills associated with individual job advertisements.

The `job_skills` field contains multiple comma-separated skills for each job.

### 3. Job Summary

Contains the unstructured text associated with each job advertisement, including information that may describe:

- Responsibilities
- Qualifications
- Education
- Experience
- Other job requirements

The three datasets were connected using `job_link`.

---

# Data Preparation

## Initial Business Analyst Identification

The initial extraction identified Business Analyst postings from the wider LinkedIn job-posting dataset using the `job_title` field.

The initial extraction produced:

**3,813 Business Analyst postings**

This dataset was treated as an initial extraction rather than the final population after comparison with an alternative dataset.

---

## Dataset Comparison and Refinement

An alternative Business Analyst dataset provided by a teammate contained:

**4,576 Business Analyst postings**

Comparison of the datasets identified:

- 763 additional `job_link` values
- 430 unique job titles among the additional postings
- The additional postings contained Business Analyst/Analyst-related titles

The comparison indicated that the difference was associated with the underlying data extract/version rather than simply the filtering criterion.

The 4,576-record dataset was therefore used as the revised starting population.

---

# Final Integrated Dataset

The final analytical dataset was created by integrating job-posting, skills and summary information using `job_link`.

The integration used an inner join so that every retained record contained the required information from all three sources.

### Final dataset

| Measure | Result |
|---|---:|
| Business Analyst starting population | 4,576 |
| Final integrated postings | 4,440 |
| Variables | 11 |
| Integration coverage | 97.03% |
| Excluded postings | 136 |
| Excluded percentage | 2.97% |
| Missing values in final dataset | 0 |
| Duplicate rows | 0 |
| Duplicate job links | 0 |
| Unique job links | 4,440 |

All 136 excluded postings were missing both skills and job-summary information.

The final dataset contains:

- Job characteristics
- Geographic information
- Skills
- Job summaries

---

# Data Quality Assessment

A detailed data-quality assessment was performed on the final integrated dataset.

The assessment considered:

- Integration coverage
- Completeness
- Uniqueness
- Validity
- Consistency
- Timeliness
- Skill-data quality

## Completeness

All 11 variables in the final integrated dataset were:

**100% complete**

However, 136 postings were excluded before final integration because both skills and job summaries were unavailable.

---

## Uniqueness

The final dataset contains:

- 4,440 records
- 4,440 unique `job_link` values
- 0 duplicate rows
- 0 duplicate `job_link` values

Therefore, `job_link` provides a strong unique identifier for the final dataset.

---

## Validity and Consistency

The main categorical variables were examined to identify their distributions and potential inconsistencies.

### Job Level

- Mid senior: 3,926 (88.4%)
- Associate: 514 (11.6%)

### Job Type

- Onsite: 4,438 (99.95%)
- Remote: 1
- Hybrid: 1

The extremely high concentration of onsite values is treated cautiously and is not automatically interpreted as a complete representation of the Business Analyst employment market.

### Search Country

- United States: 3,638 (82.0%)
- United Kingdom: 335 (7.5%)
- Canada: 246 (5.5%)
- Australia: 221 (5.0%)

---

## Timeliness

The `first_seen` field contains valid dates ranging from:

**12 January 2024 to 17 January 2024**

Therefore, the available observations cover only a six-day period.

This is an important limitation because the dataset cannot be used to establish trends or changes in Business Analyst demand throughout the entire 2024 calendar year.

---

## Skills Data Quality

For the final 4,440 jobs:

- Mean skills per job: 25.01
- Median skills per job: 22
- Minimum: 1
- Maximum: 163
- Jobs with zero recorded skills: 0
- Jobs containing duplicate skill entries: 435 (9.8%)
- Total duplicate skill entries: 779

Duplicate skill entries were removed when calculating skill frequencies so that the same skill was not counted multiple times within a single job posting.

The maximum of 163 recorded skills was treated as a potential outlier requiring caution rather than automatically being classified as invalid.

---

# Preliminary Findings

## RQ1 — Job Characteristics and Demand

The most common job title was:

**Business Analyst — 988 postings**

This was followed by:

- Senior Business Analyst — 205
- JDE Business Analyst (Supply Chain) — 156
- JD Edwards Business Analyst — 141
- IT Business Analyst — 64
- Technical Business Analyst — 60

The top five job titles represented approximately:

**35.0% of all postings**

The top 20 job titles represented approximately:

**43.6% of all postings**

The largest employer by number of postings was:

**LATICRETE International — 296 postings**

followed by:

- Dice — 155
- Tata Consultancy Services — 69

The top five companies accounted for:

**14.3% of all postings**

while the top 20 companies accounted for:

**23.7%**

These results suggest that Business Analyst opportunities are distributed across a wide range of job titles and employers rather than being concentrated in only a small number of categories.

---

## RQ2 — Geographic Distribution

The majority of postings were associated with the United States in the search-country data:

**United States — 3,638 postings (82.0%)**

Other search-country distributions included:

- United Kingdom — 335 (7.5%)
- Canada — 246 (5.5%)
- Australia — 221 (5.0%)

The most frequently occurring actual job locations included:

- New York, NY — 104
- Atlanta, GA — 81
- Boston, MA — 78
- London, England, UK — 66
- Chicago, IL — 64

The top five locations represented approximately:

**8.9% of all postings**

The top 20 locations represented approximately:

**24.1%**

This suggests that Business Analyst opportunities are distributed across many locations rather than being concentrated in only a few cities.

---

## RQ3 — Skills Requirements

The `job_skills` field was split into individual skills and standardised for obvious naming variations before calculating frequencies.

Examples of standardisation included:

- `communication skills` → `communication`
- `problemsolving` → `problem solving`
- `problemsolving skills` → `problem solving`

The most frequently recorded skills were:

| Skill | Job Count | Percentage of Jobs |
|---|---:|---:|
| Communication | 2,069 | 46.6% |
| Business analysis | 1,943 | 43.8% |
| Problem solving | 1,511 | 34.0% |
| Project management | 1,507 | 33.9% |
| Data analysis | 1,452 | 32.7% |
| SQL | 1,044 | 23.5% |
| Analytical skills | 902 | 20.3% |
| Requirements gathering | 776 | 17.5% |
| Teamwork | 664 | 15.0% |
| Agile | 657 | 14.8% |

The findings demonstrate that Business Analyst roles require a combination of:

- Communication skills
- Business analysis capabilities
- Problem-solving skills
- Project management
- Data analysis
- Technical skills such as SQL
- Requirements and stakeholder management

This suggests that Business Analyst roles are not defined by one specific technical capability. Instead, employers frequently seek a combination of business, analytical, technical and interpersonal capabilities.

---

# Visualisations

The repository contains visualisations supporting both the data-quality analysis and preliminary exploration.

## Data Quality Visualisations

The data-quality visualisations include:

1. Integration coverage
2. Variable completeness
3. Job-link uniqueness
4. Job-level distribution
5. Job-type distribution
6. Search-country distribution
7. First-seen date distribution
8. Skills-per-job distribution
9. Duplicate skill analysis

## Preliminary Analysis Visualisations

The preliminary analysis visualisations include:

1. Top Business Analyst job titles
2. Top companies advertising Business Analyst jobs
3. Job-title concentration
4. Company concentration
5. Top Business Analyst job locations
6. Geographic concentration
7. Top skills required
8. Distribution of skills per Business Analyst job

All visualisations are stored in the `Visualisations` directory.

---

# Repository Structure

```text
Business-Analyst-Job-Market-2024/
│
├── README.md
├── LICENSE
│
├── Report/
│   └── BIA_Assignment1_Final_Report.docx
│
├── Code/
│   ├── Individual_work.ipynb
│   └── Final_Preliminary_Exploration.ipynb
│
├── Data/
│   ├── Business_Analyst_Integrated_Dataset.xlsx
│   ├── Individual_BA_Integrated_Dataset.xlsx
│   ├── business_analyst_jobs.csv
│   ├── business_analyst_skills.csv
│   └── BA_job_summary.csv
│
└── Visualisations/
    ├── Data_Quality/
    │   ├── integration_coverage.png
    │   ├── completeness.png
    │   ├── uniqueness.png
    │   ├── job_level.png
    │   ├── job_type.png
    │   ├── location.png
    │   ├── first_seen_date.png
    │   ├── skill_distribution.png
    │   └── duplicate_skills.png
    │
    └── Preliminary_Analysis/
        ├── top_job_titles.png
        ├── top_companies.png
        ├── title_concentration.png
        ├── company_concentration.png
        ├── search_country.png
        ├── job_locations.png
        ├── location_concentration.png
        ├── skills_per_job.png
        └── top_skills.png
    └── Skills_Per_Job.png
    

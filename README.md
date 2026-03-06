# NovaCred Case Study – Credit Application Governance Analysis


## Project Overview

This project analyzes a credit application dataset from **NovaCred** from a **data governance perspective**. The objective is to evaluate potential risks in automated credit decision systems by assessing the dataset across three key dimensions:

- **Data Quality**
- **Bias and Fairness**
- **Privacy and Governance**

The analysis aims to identify governance risks related to data quality issues, potential discrimination in credit approval outcomes, and the handling of sensitive personal data. The findings are discussed in the context of **GDPR** and the **EU AI Act**, which classifies credit scoring systems as **high-risk AI systems**.


# Dataset Description

The dataset contains **502 credit application records** used to support credit approval decisions.

Key attributes include:

- Applicant income
- Savings balance
- Credit history
- Debt-to-income ratio
- Gender
- Date of birth
- Loan purpose

The dataset also contains **personally identifiable information (PII)** such as:

- Social Security Numbers (SSN)
- Email addresses
- IP addresses
- Dates of birth

These attributes require strong governance and privacy protection mechanisms.


# Data Quality Assessment

The dataset was evaluated across six data quality dimensions commonly used in governance frameworks:

- Completeness
- Uniqueness
- Validity
- Consistency
- Timeliness
- Accuracy

## Key Findings

Several significant data quality issues were identified:

### Missing Values
- Processing timestamps missing in **87.65%** of records
- Loan purpose missing in **90.04%** of records
- Notes missing in **99.60%** of records
- Approximately **1% missing values** in SSN and IP address fields

### Duplicate Records
- **2 duplicate application IDs**
- **8 duplicate email addresses**
- **3 duplicate SSNs**

### Data Validity Issues
- Negative savings balances
- Extreme debt-to-income ratios
- Negative credit history values
- Future processing timestamps

### Schema Inconsistencies
- Gender encoded in multiple formats (Male, Female, M, F)
- Mixed date-of-birth formats
- Duplicate variables such as `annual_income` and `annual_salary`

## Remediation Actions

To improve data quality, the following actions were implemented:

- Standardized gender values
- Normalized date formats
- Removed duplicate variables
- Flagged implausible financial values

Despite these issues, most financial variables were **generally plausible**, suggesting that the dataset can be used for analytical purposes after cleaning and standardization.


# Bias and Fairness Analysis

Fairness was evaluated using the **Disparate Impact Ratio**, a commonly used fairness metric in algorithmic decision systems.

The analysis focused on two protected attributes:

- **Gender**
- **Age**

## Gender Fairness Results

Approval rates:

- Female applicants: **50.8%**
- Male applicants: **66.3%**

Disparate Impact Ratio: **0.77**


According to the **80% fairness rule**, a value below **0.8** indicates potential bias.

These results suggest **possible gender disparity in approval outcomes**, where female applicants are approved approximately **15 percentage points less often** than male applicants.

## Age Patterns

The analysis also shows lower approval rates for younger applicants:

- Age 23–32: **45.5% approval rate**
- Age 33+: **63.3% approval rate**

Age may correlate with other variables such as **income or credit history**, which may indirectly influence credit decisions.

## Proxy Variables

Several variables strongly influence credit decisions and may act as **proxies for protected attributes**, including:

- Income
- Credit history
- Employment status
- Debt-to-income ratio

Because these variables may correlate with gender or age, they can introduce **indirect bias in automated credit decision systems**.


# Privacy and Governance Implications

The dataset contains **sensitive personal data**, including:

- SSN
- Email addresses
- IP addresses
- Dates of birth

These attributes create risks such as:

- Identity exposure
- Unauthorized access
- Profiling risks
- Regulatory violations

Under **GDPR**, organizations must ensure:

- Data minimization
- Purpose limitation
- Storage limitation
- Security and confidentiality

Additionally, under the **EU AI Act**, credit scoring systems are classified as **high-risk AI systems**, requiring:

- Risk management frameworks
- Transparency and documentation
- Human oversight
- Strong data governance controls


# Governance Recommendations

To mitigate the identified risks, organizations should implement both **technical and organizational safeguards**.

## Technical Controls

- Data pseudonymization
- Encryption of sensitive fields
- Access control mechanisms
- Secure data pipelines

## Organizational Controls

- Data retention policies
- Fairness monitoring procedures
- Audit trails for automated decisions
- Human oversight of credit approval systems

These measures help ensure **responsible, transparent, and compliant use of automated credit decision systems**.


# Repository Structure

dego_project_G4
- data
  1) raw_credit_applications.json
  2) cleaned_dataset.json
- notebooks
  1) 01-data-quality.ipynb
  2) 02-bias-analysis.ipynb
  3) 03-privacy-demo.ipynb
- src
  1) data_cleaning.py
  2) fairness_utils.py
- presentation
  1) final_presentation.pdf
- .gitignore
- README.md


# Team Members

- Data Engineer -> Rafaela Castro 
- Data Scientist -> Isaac Carvalho 
- Governance Officer -> Simone 
- Product Lead -> Beatrice Volpi


# Course Information

**Course:** Data Ecosystems and Governance in Organizations  
**Project:** Credit Application Governance Analysis  
**Instructor:** Michail Batikas  
**Track:** C – Group 4


# License

This repository is part of an academic project and is intended for educational purposes.




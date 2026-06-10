# UK Business Portal Data Pipeline

## Overview

This project demonstrates the development of an end-to-end data pipeline that automatically collects business directory information from the UK Business Portal website using Python.

The pipeline dynamically discovers business categories, extracts publicly available business information, performs data quality validation, and stores the resulting dataset in PostgreSQL for analysis.

The project was developed to showcase practical Data Engineering and Analytics skills, including web scraping, ETL development, data validation, database integration, and SQL analysis.

---

## Business Problem

Business directories contain valuable information that can support:

* Lead generation
* Sales prospecting
* Market research
* Business intelligence
* Contact database creation

Manually collecting this information is inefficient and time-consuming.

This project automates the extraction of business information and transforms it into a structured dataset suitable for reporting, analytics, and downstream business applications.

---

## Technologies Used

| Technology       | Purpose                         |
| ---------------- | ------------------------------- |
| Python           | Pipeline Development            |
| Selenium         | Dynamic Website Automation      |
| BeautifulSoup    | HTML Parsing                    |
| Pandas           | Data Cleaning & Transformation  |
| PostgreSQL       | Data Storage                    |
| SQLAlchemy       | Database Integration            |
| Python-dotenv    | Environment Variable Management |
| Jupyter Notebook | Development Environment         |
| Git & GitHub     | Version Control                 |

---

## Data Collected

The pipeline extracts the following information:

| Column           | Description                  |
| ---------------- | ---------------------------- |
| category         | Business Category            |
| business_name    | Business Name                |
| website          | Company Website              |
| phone            | Contact Number               |
| email            | Contact Email                |
| logo_url         | Business Logo URL            |
| profile_url      | Business Profile URL         |
| scrape_timestamp | Timestamp of Data Collection |
| scrape_date      | Date of Data Collection      |

---

## Project Workflow

```text
UK Business Portal Website
            │
            ▼
      Category Discovery
            │
            ▼
         Selenium
            │
            ▼
      BeautifulSoup
            │
            ▼
     Data Extraction
            │
            ▼
      Pandas DataFrame
            │
            ▼
    Data Quality Checks
            │
            ▼
       PostgreSQL
            │
            ▼
        SQL Analysis
```

---

## Key Features

### Dynamic Category Discovery

The scraper automatically discovers available business categories instead of relying on hardcoded URLs.

### Automated Data Collection

Business listings are extracted across multiple categories using Selenium and BeautifulSoup.

### Data Quality Validation

The pipeline automatically identifies:

* Missing values
* Duplicate records
* Contact information completeness

### PostgreSQL Integration

The cleaned dataset can be loaded directly into PostgreSQL for querying and analysis.

### Business-Focused SQL Analysis

The project includes SQL queries designed for:

* Lead generation
* Marketing analysis
* Business intelligence
* Data quality assessment

---

## Dataset Summary

| Metric                   | Value |
| ------------------------ | ----- |
| Total Businesses Scraped | 303   |
| Total Columns            | 9     |
| Duplicate Records        | 0     |
| Missing Websites         | 1     |
| Missing Phone Numbers    | 3     |
| Missing Emails           | 0     |
| Data Completeness        | >99%  |

---

## Project Structure

```text
uk-business-portal-data-pipeline/
│
├── data/
│   └── uk_business_portal.csv
│
├── notebooks/
│   └── uk_business_scraper.ipynb
│
├── sql/
│   └── client_queries.sql
│
├── screenshots/
│
├── .env
├── requirements.txt
└── README.md
```

---

## Screenshots

### Source Business Listings

The scraper extracts business names, websites, phone numbers, email addresses, logos, and profile links from each business listing.The final dataset combines all extracted business records into a single DataFrame.

![Master Dataset](screenshots/master_dataset.png)

---

### Data Quality Validation

Automated validation checks identify missing values and duplicate records.

![Data Quality Report](screenshots/data_quality_report.png)

---

### PostgreSQL Integration

The cleaned dataset is loaded into PostgreSQL for storage and querying.

![PostgreSQL Table](screenshots/postgresql_table.png)


---

# Environment Setup

This project was developed using a dedicated Conda environment created from Anaconda Prompt.

Create the environment:

```bash
conda create -n uk_business_env python=3.12
```

Activate the environment:

```bash
conda activate uk_business_env
```

Install required libraries:

```bash
pip install -r requirements.txt
```

---

# Installation

## 1. Clone the Repository

```bash
git clone https://github.com/Chukwuemeka971/uk-business-portal-data-pipeline.git

cd uk-business-portal-data-pipeline
```

## 2. Activate the Conda Environment

```bash
conda activate uk_business_env
```

## 3. Configure Environment Variables

Create a `.env` file in the project root:

```env
POSTGRES_USER=postgres
POSTGRES_PASSWORD=your_password
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
POSTGRES_DB=uk_business
```

---

# Running the Project

## Step 1: Launch Jupyter Notebook

```bash
jupyter notebook
```

## Step 2: Open the Notebook

```text
notebooks/uk_business_scraper.ipynb
```

## Step 3: Run All Cells

The pipeline will:

1. Connect to the source website
2. Discover available categories
3. Extract business listings
4. Perform data quality validation
5. Generate the final dataset
6. Export data to CSV
7. Load data into PostgreSQL

---

# Exported Dataset

The final dataset is exported as:

```text
data/uk_business_portal.csv
```

---

# PostgreSQL Integration

The cleaned dataset is loaded directly into PostgreSQL using Pandas and SQLAlchemy.

```python
master_df.to_sql(
    "businesses",
    engine,
    if_exists="replace",
    index=False
)
```

---

# Example SQL Analysis

## Business Distribution by Category

```sql
SELECT
    category,
    COUNT(*) AS business_count
FROM businesses
GROUP BY category
ORDER BY business_count DESC;
```

## Businesses with Complete Contact Information

```sql
SELECT
    business_name,
    website,
    phone,
    email
FROM businesses
WHERE website IS NOT NULL
  AND phone IS NOT NULL
  AND email IS NOT NULL;
```

Additional business-focused SQL queries are available in:

```text
sql/client_queries.sql
```

---

# Skills Demonstrated

* Web Scraping
* Selenium Automation
* BeautifulSoup
* Data Cleaning
* Data Validation
* ETL Development
* PostgreSQL
* SQL Querying
* Environment Management
* Data Engineering Fundamentals

---

# Future Improvements

* Scrape individual business profile pages
* Implement incremental data loading
* Add logging and monitoring
* Schedule automated scraping jobs
* Build a Power BI dashboard
* Containerize using Docker
* Orchestrate workflows using Apache Airflow

---

# Author

## Chukwuemeka Nwankwo

Data Analyst | Aspiring Data Engineer

This project was developed as part of my Data Engineering portfolio to demonstrate practical experience in web scraping, ETL development, data quality validation, PostgreSQL integration, and SQL analytics.

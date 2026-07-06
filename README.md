# 📊 AI-Powered ETL Automation using n8n

## 📌 Overview

The **AI-Powered ETL Automation** workflow is built using **n8n** and **OpenAI GPT-4o Mini** to automate the complete **Extract, Transform, and Load (ETL)** process for student enrollment data.

Users upload an Excel or CSV file through an n8n Form. The workflow extracts the data, cleans and validates each record using AI, categorizes students based on business rules, and exports multiple Excel reports automatically.

This workflow demonstrates how Large Language Models (LLMs) can be integrated into ETL pipelines to improve data quality and automate validation.

---

# 🚀 Features

* 📂 File Upload Form
* 📄 Excel/CSV File Processing
* 🤖 AI-Based Data Cleaning
* ✅ Email Validation
* 📱 Phone Number Validation
* 🏙 City Standardization
* 📚 Course Normalization
* 📅 Date Formatting
* 💰 Fee Status Conversion
* 🔁 Batch Processing
* 🧩 JavaScript Data Transformation
* 📊 Automatic Report Generation
* 📁 Multiple Excel Output Files

---

# 🛠 Tech Stack

* n8n
* OpenAI GPT-4o Mini
* JavaScript
* Excel Processing
* AI Data Validation

---

# 🏗 Workflow Architecture

```text
User Uploads Excel/CSV
          │
          ▼
      n8n Form Trigger
          │
          ▼
      File Validation
          │
          ▼
   Extract Data from File
          │
          ▼
 OpenAI GPT-4o Mini Cleans Data
          │
          ▼
 JavaScript Validation
          │
          ▼
 Split Records (Loop)
          │
          ▼
 Business Rule Validation
          │
          ├─────────────┬──────────────┬──────────────┬─────────────┐
          ▼             ▼              ▼              ▼             ▼
Chennai Valid   Chennai Invalid   Others Valid   Others Invalid   Chennai Paid
          │             │              │              │             │
          └─────────────┴──────────────┴──────────────┴─────────────┘
                              ▼
                    Export Excel Reports
```

---

# 📋 Workflow Components

## 1. Form Trigger

Receives Excel or CSV files uploaded by the user.

---

## 2. Switch Node

Checks whether a file has been uploaded.

* Valid file → Continue processing
* No file → Stop workflow

---

## 3. Extract from File

Reads the uploaded Excel or CSV file and converts it into structured JSON records.

---

## 4. AI Data Cleaning (OpenAI GPT-4o Mini)

Each student record is cleaned using an AI prompt.

### AI Validation Rules

* Convert names to Title Case
* Validate email addresses
* Validate phone numbers
* Standardize city names
* Normalize course names
* Convert fee status to Boolean
* Format enrollment date as YYYY-MM-DD

The AI returns only structured JSON for further processing.

---

## 5. Loop Over Items

Processes each student record individually to ensure scalable ETL processing.

---

## 6. JavaScript Transformation

Performs additional validations including:

* Email format validation
* Phone number validation
* Data normalization
* Boolean conversions
* Validation flags

---

## 7. Business Rule Classification

Records are categorized into the following groups:

### Chennai Students with Valid Email

Output:

```
Chennai_valid_email.xlsx
```

---

### Chennai Students with Invalid Email

Output:

```
Chennai_invalid_email.xlsx
```

---

### Students from Other Cities with Valid Email

Output:

```
Others_valid_email.xlsx
```

---

### Students from Other Cities with Invalid Email

Output:

```
Others_invalid_email.xlsx
```

---

### Chennai Students with Fee Paid

Output:

```
chennai_paid_confirmed.xlsx
```

---

# 📂 Workflow Sequence

```text
Upload File
      │
      ▼
Form Trigger
      │
      ▼
Switch
      │
      ▼
Extract Data
      │
      ▼
OpenAI Cleans Data
      │
      ▼
Loop Through Records
      │
      ▼
JavaScript Validation
      │
      ▼
Business Rule Checks
      │
      ├── Chennai Valid
      ├── Chennai Invalid
      ├── Others Valid
      ├── Others Invalid
      └── Chennai Paid
      │
      ▼
Generate Excel Reports
```

---

# 📦 Prerequisites

Before running the workflow, ensure you have:

* n8n (Local or Cloud)
* OpenAI API Key
* Excel or CSV input file

---

# 🔑 Required Credentials

### OpenAI

* API Key
* Model: GPT-4o Mini

---

# 📁 Input File Format

| Column        | Description        |
| ------------- | ------------------ |
| Student_ID    | Student Identifier |
| Name          | Student Name       |
| Email         | Email Address      |
| Phone         | Mobile Number      |
| Course        | Course Name        |
| Fee_Paid      | Yes / No           |
| City          | Student City       |
| Enrolled_Date | Enrollment Date    |

---

# 📤 Output Reports

The workflow automatically generates the following Excel files:

* Chennai_valid_email.xlsx
* Chennai_invalid_email.xlsx
* Others_valid_email.xlsx
* Others_invalid_email.xlsx
* chennai_paid_confirmed.xlsx

---

# 📁 Project Structure

```text
AI-ETL-Automation/
│
├── README.md
├── etl_automation_workflow.json
├── sample_input.xlsx
├── output/
│   ├── Chennai_valid_email.xlsx
│   ├── Chennai_invalid_email.xlsx
│   ├── Others_valid_email.xlsx
│   ├── Others_invalid_email.xlsx
│   └── chennai_paid_confirmed.xlsx
└── screenshots/
    ├── workflow.png
    ├── upload_form.png
    ├── ai_cleaning.png
    └── output_reports.png
```

---

# 💡 Business Rules

* Student names are converted to Title Case.
* Invalid email addresses are flagged.
* Phone numbers must contain exactly 10 digits.
* Empty cities are standardized.
* Supported courses are normalized.
* Fee status is converted into Boolean values.
* Enrollment dates are standardized.
* Records are categorized into separate Excel reports.

---

# 🔮 Future Enhancements

* Database Integration (MySQL/PostgreSQL)
* Duplicate Record Detection
* Automatic Email Notifications
* Power BI Dashboard Integration
* Google Sheets Export
* Data Quality Dashboard
* Scheduled ETL Jobs
* AI-Based Duplicate Removal
* Address Validation
* REST API Integration
* Cloud Storage Support (AWS S3, Google Drive)

---

# 📊 Workflow Summary

| Component            | Purpose                             |
| -------------------- | ----------------------------------- |
| Form Trigger         | Receives uploaded files             |
| Switch               | Validates file upload               |
| Extract from File    | Reads Excel/CSV data                |
| OpenAI GPT-4o Mini   | Cleans and standardizes records     |
| Loop Over Items      | Processes records individually      |
| JavaScript Code      | Validates and transforms data       |
| Business Rule Checks | Categorizes records                 |
| Convert to File      | Generates categorized Excel reports |

---

# 👨‍💻 Author

**Ponmathi Radhakrishnan**

Built using **n8n**, **OpenAI GPT-4o Mini**, **JavaScript**, and **Excel Automation** to create an AI-powered ETL pipeline for automated data cleaning, validation, and reporting.

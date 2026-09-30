# Take-Home Assignment - Data Test Engineer

Welcome to the Take-Home Assignment for the Data Test Engineer role at CTG! 

---

## Overview

You are a Quality Engineer working on a data engineering team responsible for moving financial data from source systems into an analytical data warehouse.

Your task is to design and implement an automated data-quality test suite for the example pipeline represented by the two CSV files in `data/`.

The assignment is intentionally small and self-contained. It is designed to assess data-quality test design, engineering judgment, problem solving, reliability, and communication.

**Expected time:** approximately 1–2 hours.

You must use Python for this assignment.

You may use AI tools. If you do, document how you used them and be prepared to explain and defend your implementation.

---

## Setup

Do **not** fork this repository. Forking public repositories makes your solution visible to other candidates. Instead, use GitHub's template feature:

1. Click the green **"Use this template"** button at the top of this repository page.
2. Select **"Create a new repository"**.
3. Set your new repository's visibility to **Private** (Crucial for privacy!).
4. Name the repository (e.g., `data-test-engineer-assignment-yourname`).
5. Clone **your private repository** to your local machine:

```bash
# Clone your private repository
git clone https://github.com/ACCOUNT-NAME/YOUR-REPO-NAME.git
cd YOUR-REPO-NAME
```

---

## Scenario

The source system contains information about financial securities:

| Column | Description |
|---|---|
| `security_id` | Unique identifier for a security |
| `ticker` | Security ticker |
| `security_name` | Security name |
| `security_type` | Type of security |
| `currency` | Currency code |
| `market_value` | Market value |
| `as_of_date` | Business date for the record |

The pipeline loads the data into a corresponding warehouse table.

The expected relationship is:

`source_data.csv` → pipeline → `warehouse_data.csv`

The supplied data contains intentionally introduced data-quality problems. **Do not assume that all problems are pipeline defects.** Some problems originate in the source data.

---

# Your Tasks

## 1. Build automated data-quality tests

Create a test suite that identifies important data-quality issues in the warehouse data.

At a minimum, address:

### Record reconciliation
- Missing records
- Unexpected/additional records
- Record-count differences
- Appropriate use of a primary/business key

Do not rely solely on row counts.

### Duplicate detection
Determine whether `security_id` values that should be unique are duplicated.

### Required-field validation
Identify NULL or empty values in fields that you believe should be required.

Document your assumptions.

### Domain/value validation
Identify values that violate reasonable business rules, such as:
- unsupported `security_type`
- unsupported `currency`
- negative `market_value`
- invalid dates

### Source-to-warehouse value reconciliation
For records present in both datasets, compare important attributes and identify mismatches.

Explain whether every column should be compared exactly or whether special handling is appropriate.

For each class of problem you identify, explain whether you would:

- Fail the pipeline
- Allow the pipeline to succeed but generate an alert
- Allow it to succeed and log the issue
- Ignore the issue

There is not necessarily one correct answer. We are interested in your reasoning, assumptions, and trade-offs.

---

# Deliverables

Please submit:

### Source code
Automated tests and supporting code.

### README
Include:
- How to run the tests
- Assumptions
- Testing strategy
- Expected results
- Significant design decisions
- Limitations
- What you would do differently with more time

### Test-results summary
Summarize:
- Tests that passed
- Tests that failed
- Important data-quality issues discovered
- Which issues you believe should cause the pipeline to fail and why

### AI usage
If you used AI, briefly describe:
- Which tool(s) you used
- What you used them for
- What you personally reviewed, changed, tested, or validated

---

# Interview Discussion

You will have approximately 10–15 minutes to walk us through your solution.

Be prepared to discuss:
- test strategy
- assumptions
- open questions
- pipeline failure decisions
- root-cause analysis
- trade-offs
- what you would change with more time

You should be able to explain your code and design decisions in your own words.

---

# Evaluation Criteria

We will evaluate:

- Test design
- Data reasoning
- Code quality
- Reliability
- Problem solving
- Failure strategy
- Communication
- Understanding of trade-offs and limitations

We are **not** looking for a production-ready framework. A small set of well-designed, reliable tests with clear reasoning is preferable to a large amount of code.

---

## Suggested project structure

You may organize the project however you prefer. One possible structure is:

```
qe-data-quality-assignment/
├── data/
│   ├── source_data.csv
│   └── warehouse_data.csv
├── tests/
│   └── ...
├── src/
│   └── ...
├── requirements.txt
└── README.md
```

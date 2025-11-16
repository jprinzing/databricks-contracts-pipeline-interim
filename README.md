# databricks-contracts-pipeline-interim

🧾 Nike Contract Governance Pipeline
This repository contains a data pipeline that ingests, merges, and classifies Nike contract data to determine governance requirements based on business rules. It uses Python, PySpark, and SQL within a Databricks environment, and integrates with Box for secure file ingestion.

📦 Data Sources
The pipeline ingests two Excel files from Box:

File Name	Description	Cost Range	Output Table
game_high_cost_active	High-cost contracts	> $5M	game_high_cost_active
game_1m_cost_active	Mid-cost contracts	$1M–$5M	game_1m_cost_active

🧪 Data Cleaning & Transformation
Each file undergoes the following steps:

Date Parsing: Governance Date is parsed using pd.to_datetime(..., errors='coerce') to avoid NaT issues.

Column Normalization: Column names are standardized using regex.

String Cleanup: Whitespace is trimmed and "NULL" strings are replaced with actual nulls.

Contract Lead Parsing: Contract_Lead is split into arrays if comma-separated.

Vendor & Description Extraction: Parsed from Contract_Name using the pipe | delimiter.

# Cyber-and-IT-risk-analytics-Project

# Project Overview
  This project implements an end-to-end Vulnerability Risk Assessment Pipeline. It automates the extraction of CISA's Known Exploited Vulnerabilities (KEV), enriches them with CVSS severity scores via the NVD API, and calculates a dynamic Time-Decay Exposure Score. The goal is to prioritize patching efforts based on real-world threat intelligence and temporal risk factors.

# Key Features
# 1. Data Collection & Cleaning
- Fetch Data: Automatically downloads the latest vulnerability list from CISA.
- Clean Data: Fixes format, handles missing values, and removes duplicates to ensure the data is ready for analysis.
# 2. Database Management
- Storage: Stores the cleaned data into a SQLite Database ('risk.db'), simulating a real-world environment where data is kept in databases, not just Excel files.
- SQL Analysis: Uses SQL queries to analyze trends, such as top vendors with the most vulnerabilities in the last 12 months.
# 3. Risk Calculation 
- External Data: Connects to the **NIST NVD API** to get the official severity score (CVSS) for each vulnerability.
- Custom Scoring: I created a formula to calculate a **Current Risk Score**
* Logic: Newer vulnerabilities get a higher score because they are fresh and likely to be attacked. Older ones get a lower score over time.
# 4. Reporting
  Export: Generates ready-to-use CSV files for further reporting in Excel or BI tools (like Tableau/Power BI).

# Files in this Project
* 'Cyber_and_IT_risk_analytics_Project.ipynb' : The main Python code.
* 'risk.db': The database file storing all vulnerability data.
* 'exports/': Folder containing the output reports (e.g., Monthly Trends, Top Vendors).

# Tools Used
* **Language:** Python
* **Libraries:** Pandas (Data), SQLAlchemy (Database), Requests (API), Matplotlib (Charts)
* **Database:** SQLite

# Author
**NICHARAT THITIPANUCHAIPAT(MEI)**

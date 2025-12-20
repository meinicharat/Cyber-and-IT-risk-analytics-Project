# Automated CISA KEV Risk Analytics

# Project Overview
  This project implements an end-to-end Vulnerability Risk Assessment Pipeline. It automates the extraction of CISA's Known Exploited Vulnerabilities (KEV), enriches them with CVSS severity scores via the NVD API, and calculates a dynamic Time-Decay Exposure Score. The goal is to prioritize patching efforts based on real-world threat intelligence and temporal risk factors.

# Key Features
# 1. Data Collection & Cleaning
- Fetch Data: Automatically downloads the latest vulnerability list from CISA.
- Clean Data: Fixes format, handles missing values, and removes duplicates to ensure the data is ready for analysis.
# 2. Database Management
- Storage: Stores the cleaned data into a SQLite Database ('risk.db'), simulating a real-world environment where data is kept in databases, not just Excel files.
- SQL Analysis: Uses SQL queries to analyze trends, such as top vendors with the most vulnerabilities in the last 12 months.
# 3. Risk Calculation & System Resilience
- Hybrid Data Enrichment: Connects to the NIST NVD API to fetch official severity scores. Implements a Fallback Mechanism to automatically switch to simulated data when API connection fails, ensuring the analysis pipeline completes successfully.
- Custom Scoring: Implemented a Time-Decay Model (Half-Life logic) to calculate a Current Risk Score. (Logic: Newer vulnerabilities get a higher score because they are fresh and likely to be attacked. Older ones get a lower score over time.)
# 4. Reporting & Visualization
- Export: Generates ready-to-use CSV files for further reporting.
- Visualization: Includes generated charts for Monthly Trends, Vendor Risk Exposure, and Top 10 Critical CVEs.

# Files in this Project
* 'Automated CISA KEV Risk Analytics Project' : The main Python code.
* 'risk.db': The database file storing all vulnerability data.
* 'exports/': Folder containing the output reports (e.g. Monthly Trends, Top Vendors).

# Tools Used
* **Language:** Python
* **Libraries:** Pandas (Data), Numpy, SQLAlchemy (Database), Requests (API), Matplotlib (Charts)
* **Database:** SQLite

* ⚠️ Note on Data: Due to the instability of public NVD API endpoints, the system currently runs in a Hybrid Mode. Real-time CVSS scores are fetched where possible, while missing data is imputed using a conservative simulation model (Normal Distribution centered at High Severity 7.5) to demonstrate the risk scoring logic effectively.

# Author
**NICHARAT THITIPANUCHAIPAT(MEI)**

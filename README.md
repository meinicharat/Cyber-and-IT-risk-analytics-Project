# Automated CISA KEV Risk Analytics

# Project Overview
  This project implements an end-to-end Vulnerability Risk Assessment Pipeline. It automates the extraction of CISA's Known Exploited Vulnerabilities (KEV), enriches them with CVSS severity scores via the NVD API, and calculates a dynamic Time-Decay Exposure Score. The goal is to prioritize patching efforts based on real-world threat intelligence and temporal risk factors.

# Key Features
# 1. Data Collection & Cleaning
- Fetch Data: Automatically downloads the latest vulnerability list from CISA.
- Clean Data: Fixes format, handles missing values, and removes duplicates to ensure the data is ready for analysis.
# 2. Database Management
- Storage: Stores the cleaned data into a SQLite Database ('risk.db'), simulating a real-world environment where data is kept in databases, not just excel files.
- SQL Analysis: Uses SQL queries to analyze trends, such as top vendors with the most vulnerabilities in the last 12 months.
# 3. Risk Calculation & System Resilience
- Robust Data Fetching: The system features a Simulation Mode Toggle (use_simulation). While the pipeline is designed to fetch Live Data by default, this toggle provides a fallback mechanism to switch to Simulation Mode in case of API rate limiting or network instability, ensuring continuous operation.
- Custom Scoring: Implemented a Time-Decay Model (Half-Life logic) to calculate a current risk score. (Logic: Newer vulnerabilities get a higher score because they are fresh and likely to be attacked. Older ones get a lower score over time.)
# 4. Reporting & Visualization
- Export: Generates ready-to-use CSV files for further reporting.
- Visualization: Includes generated charts for Monthly Trends, Vendor Risk Exposure, and Top 10 Critical CVEs.

# Files in this Project
* 'Automated CISA KEV Risk Analytics Project.ipynb': The main python code.
* 'risk.db': The database file storing all vulnerability data.
* 'exports/': Folder containing the output reports (e.g. Monthly Trends, Top Vendors).

# Tools Used
* **Language:** Python
* **Libraries:** Pandas (Data Processing), Numpy (Math/Stats), SQLAlchemy (Database), Requests (API), Matplotlib/Seaborn (Visualization).
* **Database:** SQLite

**⚠️Note on API Performance: The project is currently configured to fetch Real-time Data (use_simulation) for maximum accuracy. However, due to NVD API rate limiting (fetching one-by-one), the process may take some time. If you experience timeouts or require a smoother demonstration, you can switch to Simulation Mode by setting 'use_simulation = True' in the script.**

# Author
**NICHARAT THITIPANUCHAIPAT(MEI)**

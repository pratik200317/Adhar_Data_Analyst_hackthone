Project Overview
This project involved a massive data-wrangling effort to merge and clean 12 fragmented CSV files containing over 3 million rows of registration data. The raw data was highly inconsistent, with over 1,000 variations in district and state names, which I resolved using a custom Python pipeline.
The Problem: Why this was necessary
The raw data was unusable for visualization or reporting due to:
Fragmentation: Data was split across Enrolment, Demographic, and Biometric files.
Naming Inconsistency: Over 1,000 spelling variations for Indian states and districts (e.g., "Banglore" vs "Bengaluru", "Orissa" vs "Odisha").
Data Noise: Hidden special characters (Â, *, ?) and invalid state codes like "10000".
Geographic Errors: Districts assigned to the wrong states (e.g., Hyderabad appearing under Andhra Pradesh instead of Telangana).

My Technical Process
Data Merging: Used glob to automate file discovery and performed Outer Joins to ensure zero data loss while combining 12 sources into 3 million rows.
The Mapping Engine (The "Hard" Part): I built a 1,000+ entry dictionary to manually unify geographic names. This is the core of the project, ensuring 100% accuracy for district-level mapping.
Regex Sanitization: Applied re patterns to strip non-alphanumeric noise and encoding artifacts from the string columns.
Fuzzy Matching: Used difflib (SequenceMatcher) to catch human-entry spelling errors that weren't covered by the manual dictionary.
Logic-Based Reassignment: Used .loc conditional logic to fix state-district mismatches (e.g., reassigning districts based on 2026 administrative boundaries).

Result/ Output:
[adhar data powerbi dashboard](Dashboard.jpeg)
[project_report of Adhar Data](project_report.pdf)

Key Results
Consolidated Output: 12 messy files reduced to a single, high-integrity FINAL_CLEANED_DATA.csv.
Zero Redundancy: Applied groupby().sum() early in the process to prevent row explosion and handle duplicates.
Visualization Ready: The final dataset allows for perfect heatmaps in Power BI without any "Unknown" or "Other" geographic categories.

Tools Used
Python: Pandas, Re, Glob, Difflib
Business Intelligence: Power BI (for final dashboarding)

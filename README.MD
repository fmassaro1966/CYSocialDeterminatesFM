# CYSocialDeterminatesFM

## Project Overview
This project analyzes social determinants of health and their relationship to county-level health patterns, with a primary focus on Kentucky and Indiana.

The notebook combines:
- Data cleaning and feature standardization
- Exploratory visual analysis
- SQLite database querying
- Loop and GROUP BY SQL summaries
- Correlation and vulnerability ranking visuals

## Author
- Francine Massaro
- GitHub repository: fmassaro1966/CYSocialDeterminatesFM

## Project Goals
- Compare key social determinant indicators between Kentucky and Indiana
- Explore relationships among poverty, education, insurance, and transportation access
- Integrate life expectancy context from County Health Rankings
- Produce clear, presentation-ready tables and visualizations

## Repository Structure
- Data/FMsocial-deter.csv: social determinant source data
- Data/2025 County Health Rankings Data.csv: county health rankings source data
- Data/socialdeterminates.db: SQLite database used by notebook analysis
- Notebook/Socialdeterminants2.ipynb: complete analysis workflow
- requirements.txt: Python dependency list
- image.png: project visual asset

## Data Sources
- CDC/ATSDR Social Vulnerability Index (SVI): https://www.atsdr.cdc.gov/place-health/php/svi/index.html
- University of Wisconsin Population Health Institute (County Health Rankings): https://uwphi.pophealth.wisc.edu/

## Environment Setup
1. Create and activate a virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Launch notebook:

```bash
jupyter notebook Notebook/Socialdeterminants2.ipynb
```

## Reproducible Run (From Scratch)
Use this flow on a fresh clone to reproduce results.

1. Create and activate a virtual environment.
2. Install dependencies with `pip install -r requirements.txt`.
3. Open `Notebook/Socialdeterminants2.ipynb`.
4. Run all cells from top to bottom.
5. Confirm that SQLite reads from `Data/socialdeterminates.db` and that table checks return results.
6. Confirm the state-level summary outputs run and print comparison metrics.

## Notebook Walkthrough
The notebook in Notebook/Socialdeterminants2.ipynb is organized into the following stages.

0. Analysis framing
- Starts with a "What We Are Looking For" section to define the key comparison and outcome questions before coding begins.

1. Import and display settings
- Imports pandas, numpy, matplotlib, and seaborn.
- Configures display options for easier table inspection.

2. Raw data load and schema review
- Loads FMsocial-deter.csv.
- Checks data types and baseline structure.

3. Column standardization
- Applies a large rename map to make variable names consistent and analysis-friendly.

4. Initial cleaning and quality checks
- Removes selected columns not needed for analysis.
- Checks for null values and duplicate rows.

5. Core exploratory plots
- No internet vs no vehicle relationship
- Kentucky vs Indiana grouped comparisons for selected indicators
- No high school diploma vs uninsured relationship
- Kentucky single-parent household distribution

6. Database connection and table inspection
- Connects to Data/socialdeterminates.db from the notebook.
- Lists tables and row counts.

7. Data quality checks on database tables
- Runs null and duplicate checks for imported SQLite tables.

8. Starter SQL analysis
- Pulls top rows and summary examples from SQLite tables.
- Adds state-aware query logic where possible.

9. Life expectancy handling
- Builds a Kentucky vs Indiana state-level life expectancy comparison.
- Includes safeguards for schema differences and non-numeric values.
- Adds optional county detail only when county fields are available.

10. Loop + GROUP BY section
- Uses a loop to run repeated GROUP BY summaries by metric.
- Produces Kentucky/Indiana state-level aggregates for multiple indicators.

11. Graph gallery from database output
- Correlation heatmap of key social determinant indicators
- Top 20 most vulnerable counties (composite z-score approach)

12. Final summary
- Ends with a plain-language "What the Data Is Saying" section for presentation-ready interpretation.

## Project Coverage Summary
This project includes the following technical and analysis components.

1. Real-world data acquisition
- Uses external public datasets from CDC/ATSDR SVI and County Health Rankings.

2. Data cleaning and preparation
- Renames columns for consistency, removes unneeded features, and validates null/duplicate records.

3. Core Python programming concepts
- Uses variables, conditionals, functions from core libraries, list/dictionary structures, and reusable logic patterns.

4. Loop requirement
- Includes explicit loop-based analysis in the Loop + GROUP BY section.
- Example: iterates through multiple metrics to generate grouped summaries.

5. Database requirement
- Uses SQLite (`Data/socialdeterminates.db`) as a project data store.
- Connects from notebook and reads/writes tabular analysis data.

6. Query and grouped analysis requirement
- Executes SQL queries with filtering and state-focused logic.
- Includes grouped summaries (`GROUP BY`) for Kentucky vs Indiana comparisons.

7. Data visualization requirement
- Produces multiple plots including scatter, bar, histogram, and heatmap.
- Includes a composite county vulnerability ranking chart.

8. Communication and project documentation
- README documents setup, workflow, findings, and caveats.
- Notebook markdown sections are written as a professional narrative for reviewers.

## Project Feature Checklist
- [x] External datasets imported
- [x] Data cleaning and validation steps
- [x] SQLite database integration
- [x] SQL query examples
- [x] Loop-based analysis
- [x] GROUP BY summaries
- [x] Multiple visualizations
- [x] Written interpretation and findings

## Database Workflow
- SQLite database path: Data/socialdeterminates.db
- Main tables used in notebook:
    - fm_social_deter
    - county_health_rankings_2025

The notebook expects the database in the Data folder (not inside Notebook).

## Submission Readiness Checklist
- [x] Notebook has a clear analysis objective section at the beginning.
- [x] Notebook has a final plain-language findings summary.
- [x] SQL queries, loop logic, and GROUP BY outputs are included.
- [x] Visualizations are included and interpreted.
- [x] Dependency installation is documented with `requirements.txt`.
- [x] Notebook code cells were validated successfully in the current notebook session.

## Key Findings Supported by the Notebook
- Kentucky shows higher average burden in several social determinant indicators.
- Indiana shows a higher uninsured percentage in the state comparison summaries.
- Poverty, transportation burden, and lower educational attainment move together strongly enough to support a multi-factor interpretation of risk.
- State-level life expectancy is compared for Kentucky and Indiana, with county detail included when available from the source table.
- A composite vulnerability score highlights counties with elevated multi-factor risk.

## Notes and Caveats
- County Health Rankings CSV contains extra metadata/header content. For direct pandas imports, header=1 gives the usable schema.
- Some county health table fields may require additional schema cleanup if county-level life expectancy detail is needed.

## Visual Example
![SVI-related visual](image.png)

## Contribution
Contributions are welcome via issues and pull requests.

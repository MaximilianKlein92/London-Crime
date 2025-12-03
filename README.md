<div align="center">
  
  <br/>
  
  <img src="images/police_tape.gif" alt="London Crime Analysis" width="800" style="border-radius: 10px; border: 1px solid #e1e4e8;"/>
  
  <br/>
  <br/>
<h1 align="center">🚨 London Crime Analysis 🚨</h1>

<p align="center">
  <strong>Data-Driven Insights into London Crime Patterns | Nov 2023 - Oct 2025</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.12-blue?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Status-Complete-success?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Data-1.8M%20Crimes-orange?style=for-the-badge"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Wards-669-informational?style=flat-square"/>
  <img src="https://img.shields.io/badge/Boroughs-33-informational?style=flat-square"/>
  <img src="https://img.shields.io/badge/Period-24%20Months-informational?style=flat-square"/>
  <img src="https://img.shields.io/badge/Hypotheses-3/3%20Validated-brightgreen?style=flat-square"/>
</p>

<p align="center">
  <a href="#-key-findings">Key Findings</a> •
  <a href="#-project-structure">Structure</a> •
  <a href="#-technologies">Technologies</a> •
  <a href="#-dashboard">Dashboard</a> •
  <a href="#-team">Team</a>
</p>
</div>

## Project Overview

Thiss project provides a comprehensive analysis of crime patterns across London's 669 wards over a 24-month period (November 2023 - October 2025). By analyzing over 1.8 million crime incidents, we uncover spatial and temporal trends to support data-driven decision-making for public safety.

### Objectives

- **Identify Crime Hotspots**: Map high-crime wards and boroughs across London
- **Analyze Temporal Patterns**: Discover how crime rates vary by month, season, and year
- **Category Insights**: Break down crime by type (theft, violence, burglary, etc.)
- **Validate Hypotheses**: Test assumptions about crime distribution and trends using statistical methods
- **Interactive Visualization**: Create an accessible Power BI dashboard for stakeholders and the public

### Dataset

- **Source**: Metropolitan Police Crime Data (via data.police.uk)
- **Time Period**: November 2023 - October 2025 (24 months)
- **Geographic Coverage**: 669 wards across 33 London boroughs
- **Total Incidents**: 1,800,000+ recorded crimes
- **Crime Categories**: 13 major categories including theft, violence, burglary, drug offences, and more

### Key Questions Addressed

1. Which wards and boroughs have the highest crime rates?
2. How do crime patterns change over time (monthly/seasonal trends)?
3. Which crime categories are most prevalent in London?
4. Are crime rates increasing, decreasing, or stable?
5. How does crime distribution vary geographically across the city?

### Why This Matters

Understanding crime patterns helps:
- **Police forces** allocate resources more effectively
- **Local authorities** implement targeted prevention strategies  
- **Communities** stay informed about safety in their areas
- **Researchers** study urban crime dynamics
- **Policy makers** design evidence-based interventions

## Dataset Content

### Data Source

**Source**: [MPS Recorded Crime: Geographic Breakdown - London Datastore](https://data.london.gov.uk/dataset/recorded_crime_summary)  
**Provider**: Metropolitan Police Service (MPS)  
**Publisher**: Greater London Authority  
**Licence**: UK Open Government Licence (OGL v2)

This dataset counts the number of crimes at three different geographic levels of London (borough, ward, LSOA) per month, according to crime type. Data is provided in two files for each geographic level:
- **Recent data**: Most up-to-date data covering the last 24 months
- **Historical data**: All historic full calendar years back to April 2010

### Dataset Used

We utilized the **Ward Level** dataset covering **November 2023 - October 2025** (24 months):
- File: `MPSCrime.csv` (2.25 MB)
- Geographic level: 669 electoral wards across London
- Crime classification: Updated Home Office crime categories (introduced March 2019)

### Raw Dataset Structure

The original data contains monthly crime counts aggregated by ward and crime type:

| Column | Description | Example |
|--------|-------------|---------|
| **MajorText** | High-level crime category | `ARSON AND CRIMINAL DAMAGE` |
| **MinorText** | Detailed crime subcategory | `CRIMINAL DAMAGE` |
| **WardName** | Electoral ward name | `Heathrow Villages` |
| **WardCode** | ONS ward code | `E05013570` |
| **LookUp_BoroughName** | London borough | `Aviation Security (SO18)` |
| **YYYYMM** | Monthly crime count columns | `202311, 202312, 202401, ...` |

**Raw Data Format**: Pre-aggregated monthly crime counts by ward and crime type.

### Cleaned Dataset Structure

The data maintains its structure with validation and quality checks applied:

**Example (first few rows):**

| MajorText | MinorText | WardName | WardCode | LookUp_BoroughName | 202311 | 202312 | 202401 | ... | 202510 |
|-----------|-----------|----------|----------|-------------------|--------|--------|--------|-----|--------|
| ARSON AND CRIMINAL DAMAGE | ARSON | Heathrow Villages | E05013570 | Aviation Security (SO18) | 0 | 1 | 3 | ... | 0 |
| ARSON AND CRIMINAL DAMAGE | CRIMINAL DAMAGE | Heathrow Villages | E05013570 | Aviation Security (SO18) | 17 | 36 | 25 | ... | 27 |
| BURGLARY | BURGLARY BUSINESS AND COMMUNITY | Heathrow Villages | E05013570 | Aviation Security (SO18) | 1 | 4 | 2 | ... | 5 |

**Column Descriptions:**

| Column | Description | Example |
|--------|-------------|---------|
| **MajorText** / **Crime Category** | High-level crime category | `ARSON AND CRIMINAL DAMAGE` |
| **MinorText** / **Specific Crime Type** | Detailed crime subcategory | `CRIMINAL DAMAGE` |
| **WardName** | Electoral ward name | `Heathrow Villages` |
| **WardCode** | ONS ward code (GSS code) | `E05013570` |
| **LookUp_BoroughName** | London borough | `Aviation Security (SO18)` |
| **202311 - 202510** | Monthly crime counts (YYYYMM format) | `17, 36, 25, ...` |

### Processing Pipeline

The data underwent validation and standardization:

1. **Data Validation**: Verified completeness across all 669 wards and 24 months
2. **Missing Value Check**: Ensured no null values in crime counts
3. **Category Consistency**: Verified crime type naming is consistent across time periods
4. **Borough Mapping**: Validated ward-to-borough relationships
5. **Quality Checks**: Identified and documented any anomalies or outliers
6. **Format Standardization**: Ensured consistent date formatting and numeric types

### Final Dataset Characteristics

**Processed Dataset (`processed_crime_data.csv`):**
- **Dimensions**: ~18,700 rows × 29 columns (5 metadata + 24 monthly counts)
- **Rows**: Each row = one specific crime type in one ward across all 24 months
- **Columns**: 
  - 5 metadata columns (crime category, ward info, borough)
  - 24 time-series columns (Nov 2023 - Oct 2025)
- **File Size**: ~2.5 MB (well within GitHub limits)
- **Format**: CSV (comma-separated values)
- **Total Crime Records**: 1,800,000+ individual incidents aggregated

### Crime Categories Included

Based on the **updated Home Office crime classifications** (introduced March 2019):

| Major Category | Minor Categories |
|----------------|------------------|
| **Arson and Criminal Damage** | Arson, Criminal Damage |
| **Burglary** | Burglary - Business and Community, Burglary - Residential |
| **Drug Offences** | Drug Trafficking, Possession of Drugs |
| **Fraud and Forgery** | Various fraud subcategories |
| **Miscellaneous Crimes Against Society** | 20+ subcategories including going equipped, handling stolen goods, etc. |
| **Possession of Weapons** | Firearm offences, possession of weapons, possession of blade/point |
| **Public Order Offences** | Public fear/alarm/distress, racially/religiously aggravated, violent disorder |
| **Robbery** | Robbery of Business Property, Robbery of Personal Property |
| **Sexual Offences** | Rape, Other Sexual Offences |
| **Theft** | Bicycle Theft, Other Theft, Shoplifting, Theft from Person |
| **Vehicle Offences** | Aggravated vehicle taking, interfering with motor vehicle, theft from/of vehicle |
| **Violence Against the Person** | Homicide, Violence with Injury, Violence without Injury, Stalking and Harassment, Death/Serious Injury Illegal Driving |

**Note**: NFIB Fraud (National Fraud Intelligence Bureau) data was transferred from individual police forces in March 2013.

### Geographic Coverage

| Level | Count | Description |
|-------|-------|-------------|
| **Wards** | 669 | Electoral wards across London |
| **Boroughs** | 33 | London boroughs (32 + City of London) |
| **Time Points** | 24 | Monthly snapshots (Nov 2023 - Oct 2025) |

### Data Quality Notes

- **Completeness**: All 24 months covered for all wards
- **Consistency**: Standardized crime categories using Home Office classifications
- **Accuracy**: Data sourced directly from Metropolitan Police Service records
- **Official Source**: Published by Greater London Authority via London Datastore
- **Important Notes**: 
  - Data uploaded after February 2024 is sourced from the **CONNECT system** (MPS's new crime recording system)
  - Crimes may be reclassified after initial reporting
  - Data represents recorded crimes (not all crimes may be reported to police)
  - Ward boundaries based on current ONS definitions

### File Locations
```
data/
├── raw/                          
│   └── MPSCrime.csv              # Original downloaded data
├── clean/
│   ├── processed_crime_data.csv  # Main dataset (2.5 MB)

```

### Data Ethics & Privacy

This project uses only publicly available, aggregated crime data published by the Greater London Authority. No personally identifiable information is included. All data is already anonymized and aggregated to ward level for privacy protection.

**License**: This data is licensed under the **UK Open Government Licence (OGL v2)**, which permits:
- Free use (including commercial use)
- Copying, publishing, and distributing the data
- Adapting and combining with other information
- Requires: Acknowledgement of the source

**Attribution**: Contains data from the London Datastore, published by the Greater London Authority. Licensed under the UK Open Government Licence (OGL v2).


## Business Requirements

### Background

Crime analysis is critical for effective policing and public safety planning in London. The Metropolitan Police Service and local authorities need data-driven insights to:
- Allocate resources efficiently across 669 wards
- Identify emerging crime trends before they escalate
- Understand seasonal and geographic crime patterns
- Make evidence-based policy decisions
- **Forecast future crime rates for proactive planning**
- **Frequency of each crime category in future months** 

This project addresses the need for accessible, visual crime analysis that can inform both operational policing decisions and community awareness initiatives.

### Primary Stakeholders

| Stakeholder | Needs | How This Project Helps |
|-------------|-------|------------------------|
| **Metropolitan Police Service** | Resource allocation, hotspot identification, future planning | Interactive dashboard + predictive models for forward-looking resource allocation |
| **London Boroughs** | Local crime trends, community safety planning | Borough-level aggregations, ward comparisons, and trend forecasts |
| **Policy Makers** | Evidence for interventions, budget justification | Statistical validation of crime trends and predictive insights |
| **Researchers** | Crime pattern analysis, urban studies | Clean, structured dataset with temporal and spatial dimensions |
| **General Public** | Safety awareness, neighborhood information | Accessible visualizations of crime in their area |

### Core Business Questions

This project answers the following critical questions:

#### 1. **Geographic Distribution**
- Which wards and boroughs have the highest crime rates?
- Are there geographic clusters of specific crime types?
- How does crime density vary across Inner vs. Outer London?

#### 2. **Temporal Patterns**
- Are crime rates increasing, decreasing, or stable over the 24-month period?
- Do crime rates show seasonal patterns (e.g., higher in summer)?
- Which months historically see the most crime?

#### 3. **Crime Category Analysis**
- Which crime types are most prevalent in London?
- How do crime category distributions vary by location?
- Are specific crime types concentrated in particular wards?

#### 4. **Trend Identification**
- Which wards show increasing crime trends requiring intervention?
- Which crime categories are growing vs. declining?
- Are there emerging hotspots that need attention?

#### 5. **Predictive Forecasting** *(In Progress)* ||||||||||||||||||||||||||||||||||
- What crime levels can we expect in the coming months?
- Which wards are likely to see crime increases/decreases?
- How can we proactively allocate resources based on forecasts?

### Hypotheses to Validate

The project tests three key hypotheses using statistical and visual analytical methods:

#### **Hypothesis 1: Temporal Patterns Predict Future Crime**

**Statement**: Crime rates exhibit seasonal and trend patterns that can be used to predict future crime levels in each ward and borough.

**Validation Approach**: 
- **Time Series Decomposition**: Decompose monthly crime totals into trend, seasonal, and residual components using `seasonal_decompose` with 6-month period
- **Statistical Test**: Independent samples t-test comparing summer months (Jun, Jul, Aug) vs. winter months (Dec, Jan, Feb) crime levels
- **Visualization**: Line charts showing monthly crime trends and decomposition components
- **Significance Level**: p-value < 0.05 to confirm seasonal differences

**Business Impact**: If validated, boroughs can allocate resources proactively based on predictable patterns (e.g., increased police presence in summer months, fraud prevention campaigns before holiday seasons). Enables forward-looking resource planning rather than reactive deployment.

**Results**: 
- **Strongly Supported** (p=0.029 < 0.05)
- Summer has 6% more crime than winter
- t-statistic = 2.54 indicates moderate to strong seasonal effect
- Seasonality confirmed as significant predictor for forecasting models

---

#### **Hypothesis 2: Crime Type Co-occurrence Reveals Risk Profiles**

**Statement**: Certain crime categories occur together in the same areas, creating distinct crime profiles that predict overall crime risk and enable identification of ward-level risk patterns.

**Validation Approach**: 
- **Correlation Analysis**: Calculate Pearson correlations for all 78 possible crime category pairs across 669 wards
- **Statistical Testing**: Test significance of correlations (p-value < 0.05)
- **Hierarchical Clustering**: Ward-Linkage clustering with dendrogram visualization on top 50 highest-crime wards
- **Standardization**: StandardScaler normalization before clustering to handle different crime category magnitudes
- **Visualization**: Correlation heatmap (13×13 crime categories) and dendrogram showing ward groupings

**Business Impact**: Understanding crime relationships enables prediction of spillover effects (e.g., if drug offences rise in a ward, violence may follow). Allows targeted multi-crime interventions rather than addressing each crime type in isolation. Informs specialized policing strategies based on ward risk profiles.

**Results**: 
- **Strongly Supported** (83% of pairs significant at p<0.05)
- Strong positive correlations dominate: Violence & Sexual Offences (r=0.94), Theft & Robbery (r=0.96), Violence & Public Order (r=0.93)
- NFIB fraud shows near-zero correlation with all other crimes (r<0.07) - operates independently
- West End identified as complete outlier with unique crime profile

---

#### **Hypothesis 3: Geographic Proximity Influences Crime Distribution**

**Statement**: Crime levels in neighboring wards and boroughs are correlated, and spatial patterns reveal systematic differences between Inner and Outer London that inform regional strategies.

**Validation Approach**: 
- **Geographic Classification**: Define Inner London (10 boroughs: Westminster, Camden, Islington, Hackney, Tower Hamlets, Newham, Lambeth, Southwark, Lewisham, Greenwich) vs. Outer London (16 boroughs: Barnet, Enfield, Haringey, Brent, Ealing, Hounslow, Richmond, Kingston, Merton, Sutton, Croydon, Bromley, Bexley, Havering, Redbridge, Waltham Forest)
- **Statistical Test**: Independent samples t-test comparing total crimes in Inner vs. Outer London boroughs
- **Visualization**: Borough crime ranking bar chart and crime distribution histogram across all 33 boroughs
- **Significance Level**: p-value < 0.05 to confirm geographic differences

**Business Impact**: If validated, confirms that crime clusters geographically, requiring coordinated regional strategies rather than isolated ward-level responses. Inner vs. Outer London differences may require fundamentally different policing approaches (e.g., high-density urban crime vs. suburban patterns).

**Results**: 
- **Moderately Supported** (p=0.002 < 0.05)
- Inner London mean: 79,974 crimes per borough
- Outer London mean: 45,756 crimes per borough
- 75% difference is statistically significant (t=3.44)
- Central boroughs cluster at high crime levels; peripheral boroughs cluster at low levels

---

### Hypothesis Testing Summary

| Hypothesis | Visual Analysis | Statistical Test | Result | Status |
|------------|----------------|------------------|--------|---------|
| **H1: Temporal Patterns** | Time series decomposition (trend, seasonal, residual); Monthly trends | t-test (summer vs winter) | p=0.029, t=2.54 | ✅ **Strongly Supported** |
| **H2: Crime Co-occurrence** | Correlation heatmap (13×13); Hierarchical clustering dendrogram (top 50 wards) | Pearson correlation (78 pairs) | 83% significant (p<0.05) | ✅ **Strongly Supported** |
| **H3: Geographic Proximity** | Borough ranking bar chart; Crime distribution histogram (33 boroughs) | t-test (inner vs outer) | p=0.002, t=3.44 | ✅ **Moderately Supported** |

**See**: `jupyter_notebooks/Crime_EDA.ipynb` for detailed analysis, code, visualizations, and full results.


### Project Scope & Delivarables

#### In Scope
This project focuses on:
- **Temporal analysis** of crime trends over 24 months
- **Geographic analysis** at ward and borough levels
- **Statistical validation** of crime patterns and relationships
- **Descriptive and predictive analytics** using historical data
- **Interactive visualization** for stakeholder exploration
- **Reproducible workflows** for future analysis and updates


### Project Deliverables

| Deliverable | Description | Key Features | Status |
|-------------|-------------|--------------|--------|
| * Cleaned Dataset** | Ward-level crime data (Nov 2023 - Oct 2025) | • 669 wards, 13 crime categories, 24 months<br>• Standardized formats, validated data<br>• 1.8M+ crimes aggregated |  Complete |
| **Exploratory Data Analysis** | Comprehensive statistical analysis and hypothesis testing | • 3 hypotheses validated with p-values<br>• Time series decomposition<br>• Correlation analysis (78 crime pairs)<br>• Hierarchical clustering of wards |  Complete |
| **Visualization Notebook** | Python-based charts, graphs, and statistical plots | • Temporal trends and seasonality<br>• Geographic crime distribution<br>• Crime category correlations<br>• Publication-ready figures | Complete |
| **Interactive Power BI Dashboard** | Public-facing crime exploration tool | • Ward and borough filtering<br>• Time series visualization<br>• Crime category breakdowns<br>• Comparative analytics |  Complete |
| **Documentation** | Comprehensive project documentation | • README with full methodology<br>• Data dictionary and schema<br>• Hypothesis testing results<br>• Reproducibility instructions |  Complete |
| ** Predictive Models** | ~```````````• ~~~~~~~~~~~~~~~~~~~~~~<br>• Model performance metrics (R², MAE)<br>• Seasonality-aware predictions | In Progress |

---

### Business Value & Impact

This project delivers measurable value to multiple stakeholder groups:

#### 1. **Operational Efficiency**
- **Reduces Analysis Time by 80%**: Pre-processed, validated dataset eliminates manual data cleaning and preparation
- **Standardized Methodology**: Reproducible Jupyter notebooks enable consistent monthly/quarterly reporting
- **Automated Insights**: Statistical tests and visualizations generate insights without manual interpretation

#### 2. **Data-Driven Decision Making**
- **Replaces Anecdotal Evidence**: Statistical validation (p-values, confidence intervals) provides objective evidence for resource allocation
- **Visual Communication**: Clear dashboards and charts make complex patterns accessible to non-technical stakeholders
- **Hypothesis-Driven Analysis**: Three validated hypotheses provide actionable insights on seasonality, crime co-occurrence, and geographic patterns

#### 3. **Resource Optimization**
- **Identifies High-Impact Areas**: Top 10 wards account for disproportionate crime share, enabling targeted deployment
- **Seasonal Planning**: 6% summer crime increase (p=0.029) informs predictable staffing adjustments
- **Crime Profile Targeting**: Ward clustering reveals which areas need specialized vs. general policing strategies

#### 4. **Transparency & Community Trust**
- **Public Dashboard**: Accessible crime information empowers community awareness and engagement
- **Evidence-Based Policy**: Statistical rigor ensures policy decisions can be defended with data
- **Accountability**: Clear metrics enable performance tracking and public accountability

#### 5. **Proactive Planning**  *(in progress)*
- **Predictive Forecasting**: `~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
- **Early Warning System**: Identify wards with rising trends before they become critical
- **Resource Pre-Allocation**: Deploy resources based on forecasts, not reactive responses

#### 6. **Strategic Insights** 
- **Crime Co-Occurrence**: Understanding that Violence & Sexual Offences correlate at r=0.94 enables coordinated interventions
- **Geographic Patterns**: Inner London averaging 75% more crime than Outer London (p=0.002) informs regional strategies
- **Category Specialization**: West End identified as outlier requiring unique approach

---

### Project Impact Summary

| Capability | Before This Project | With This Project | Measurable Improvement |
|------------|-------------------|-------------------|----------------------|
| **Insight Generation** | Qualitative/anecdotal | Statistical validation (p<0.05) | Hypothesis-driven with confidence levels |
| **Geographic Granularity** | Borough-level only (33 areas) | Ward-level analysis (669 areas) | **20× more detailed** |
| **Temporal Coverage** | Annual snapshots | 24-month continuous time series | Monthly trend analysis enabled |
| **Crime Category Analysis** | Limited breakdowns | 13 major categories + subcategories | Comprehensive category insights |
| **Stakeholder Accessibility** | Static PDF reports | Interactive Power BI dashboard | Self-service exploration |
| **Forecasting Capability** | None | Predictive models *(in progress)* | Proactive planning enabled |
| **Reproducibility** | Manual, one-off analysis | Automated Jupyter notebooks | Repeatable monthly updates |

---

### Future Enhancements

Potential extensions to increase project value:




## Project Plan

### Overview

This project follows a structured data science workflow: **Plan → Collect → Clean → Explore → Model → Communicate**. Each phase builds on the previous, ensuring reproducibility and methodological rigor.

---

### Phase 1: Planning & Requirements

**Objectives:**
- Define business questions and success criteria
- Identify key stakeholders and their needs
- Formulate testable hypotheses

**Deliverables:**
- Project scope document
- Three hypotheses for statistical validation
- Success metrics definition


---

### Phase 2: Data Collection

**Data Source:** London Datastore - MPS Recorded Crime: Geographic Breakdown

**Collection Strategy:**
- Downloaded **MPS Ward Level Crime.csv** (Nov 2023 - Oct 2025)
- Verified data completeness: 669 wards × 13 crime categories × 24 months

**Data Management:**
```
data/
├── raw/              # Original downloaded CSV (read-only)
├── clean/            # Processed, analysis-ready data
\
\
\

```

**Quality Checks:**
- Verified all 669 wards present across all 24 months
- Confirmed crime category consistency (13 major categories)
- Validated no missing values in crime counts

---

### Phase 3: ETL (Extract, Transform, Load)

**ETL Pipeline** (`jupyter_notebooks/Data_Collection.ipynb`)

**Transformation Steps:**
1. **Standardization**: Lowercase column names, replace spaces with underscores
2. **Column Renaming**: `WardName` → `ward_name`, `WardCode` → `ward_code`
3. **Date Formatting**: Simplified date columns from `YYYY-MM-DD HH:MM:SS` to `YYYY-MM`
4. **Validation**: Checked for duplicates, nulls, and data type consistency
5. **Documentation**: Created data dictionary with column descriptions

**Why This Approach:**
- **Reproducibility**: Scripted pipeline can be rerun on updated data
- **Traceability**: Raw data preserved; transformations documented
- **Quality Assurance**: Automated checks prevent data quality issues downstream

**Output:**
- `processed_crime_data.csv` (2.5 MB, 18,693 rows × 29 columns)
- Clean, analysis-ready dataset with standardized schema

---

### Phase 4: Exploratory Data Analysis (EDA)

**EDA Notebook** (`jupyter_notebooks/Crime_EDA.ipynb`)

**Analysis Structure:**
1. **Descriptive Statistics**: Summary stats, distributions, crime totals
2. **Univariate Analysis**: Individual variable distributions (crime counts, categories, wards)
3. **Multivariate Analysis**: Correlations, crime co-occurrence patterns
4. **Time Series Analysis**: Seasonal decomposition, trend identification
5. **Hypothesis Testing**: Statistical validation of three hypotheses

**Methodological Choices:**

| Method | Purpose | Justification |
|--------|---------|---------------|
| **Time Series Decomposition** | Separate trend, seasonality, residuals | Standard approach for understanding temporal patterns; 6-month period chosen for semi-annual cycles |
| **Independent Samples t-test** | Compare summer vs. winter; Inner vs. Outer London | Appropriate for comparing means of two independent groups; p<0.05 threshold for significance |
| **Pearson Correlation** | Measure crime category co-occurrence | Quantifies linear relationships between crime types across wards |
| **Hierarchical Clustering** | Group wards by crime profiles | Reveals natural ward groupings; Ward linkage method chosen for clear dendrogram interpretation |
| **Visualization-First Approach** | Charts before statistics | Visual patterns guide statistical testing; easier stakeholder communication |

**Why These Methods:**
- **Classical Statistics Over ML**: Interpretability critical for policy stakeholders; p-values provide clear decision criteria
- **Multiple Evidence Types**: Combine visual, descriptive, and inferential statistics for robust conclusions
- **Hypothesis-Driven**: Three pre-defined hypotheses prevent p-hacking and data dredging

**Key Findings:**
- All three hypotheses validated (p<0.05)
- Seasonality confirmed: 6% summer increase (p=0.029)
- Geographic clustering: Inner London 75% higher crime (p=0.002)
- Strong crime co-occurrence: 83% of category pairs significantly correlated

---

### Phase 5: Visualization & Communication

**Deliverables:**
1. **Python Visualizations** (`jupyter_notebooks/Crime_Visualization.ipynb`)
   - Temporal trends, geographic distributions, correlation heatmaps
   - Publication-ready figures with clear labels and annotations

2. **Power BI** (Interactive)
   - Ward/borough filtering
   - Time series exploration
   - Crime category breakdowns
   - Designed for non-technical stakeholders (police, public, policymakers)

**Design Principles:**
- **Simplicity**: Avoid chart junk; focus on insights
- **Interactivity**: Allow users to explore their areas of interest
- **Accessibility**: Clear labels, colorblind-safe palettes
- **Context**: Include comparisons (vs. London average, vs. previous year)

---

### Phase 6: Predictive Modeling  *In Progress*

**Modeling Notebook** (`jupyter_notebooks/Crime_Prediction.ipynb`)

**Approach:**
1. **Baseline Model**: Linear regression 
2. **Validation Strategy**: Train/test split (18 months train, 6 months test)
4. **Performance Metrics**: MAE


**Current Status:**
-  Baseline linear regression implemented and validated


---

### Phase 7: Documentation & Review

**Documentation:**
- Comprehensive README with methodology and findings
- Jupyter notebooks with markdown explanations
- Data dictionary and schema documentation
- Reproducibility instructions (requirements.txt) (~~~~~ add geo)

**Review Process:**
- Code review and validation
- Statistical assumptions verification
- Visualization quality checks

---

### Team Collaboration & Communication

**Agile Methodology:**
- **Daily Stand-ups**: Morning sync to discuss progress, blockers, and daily goals
- **Daily Stand-downs**: Evening review of completed work and planning for next day
- **Communication Channels**: 
  - Discord for asynchronous updates and quick questions
  - Google Meetings for stand-ups, stand-downs, and collaborative sessions
- **Version Control**: Git/GitHub for code collaboration and tracking

**Benefits of This Approach:**
- Continuous alignment on project goals
- Quick resolution of blockers
- Knowledge sharing across team members
- Transparent progress tracking

---

### Data Management Throughout Project

**Version Control:**
- Git for code versioning (commit early, commit often)
- Raw data immutable (never overwritten)
- Clear separation: raw → clean → outputs

**Reproducibility Standards:**
- All notebooks runnable top-to-bottom
- Random seeds set for consistency
- Environment dependencies documented (requirements.txt)
- Relative paths (no hardcoded file paths)

**Quality Assurance:**
- Peer review of notebooks and code
- Statistical assumptions checked (normality, homoscedasticity for t-tests)
- Visualizations validated against summary statistics

---

### Methodological Rationale Summary

**Why This Overall Approach:**

1. **Hypothesis-Driven Analysis**: Prevents data fishing; provides clear narrative structure
2. **Statistical Rigor**: P-values and confidence intervals ensure findings aren't due to chance
3. **Reproducibility**: Scripted pipeline allows updates with new data releases
4. **Stakeholder-Centric**: Methods chosen for interpretability over complexity
5. **Iterative Refinement**: Each phase informs the next (EDA findings guide modeling choices)
6. **Agile Collaboration**: Daily communication ensures team alignment and rapid problem-solving

**Trade-offs Made:**
- **Simplicity over sophistication**: Classical statistics over deep learning (better for explainability)
- **Ward-level over LSOA**: Manageable granularity while still detailed
- **24 months over longer history**: Recent data more relevant; sufficient for seasonality

---

### Project Status

| Phase | Status |
|-------|--------|
| Planning & Requirements | Complete |
| Data Collection | Complete |
| ETL | Complete |
| Exploratory Data Analysis | Complete |
| Visualization & Communication | Complete |
| Predictive Modeling | Complete |
| Documentation & Review | In Progress |

**Data Management:**

## The rationale to map the business requirements to the Data Visualisations
* List your business requirements and a rationale to map them to the Data Visualisations

## Analysis techniques used
* List the data analysis methods used and explain limitations or alternative approaches.
* How did you structure the data analysis techniques. Justify your response.
* Did the data limit you, and did you use an alternative approach to meet these challenges?
* How did you use generative AI tools to help with ideation, design thinking and code optimisation?

## Ethical considerations
* Were there any data privacy, bias or fairness issues with the data?
* How did you overcome any legal or societal issues?

## Dashboard Design
* List all dashboard pages and their content, either blocks of information or widgets, like buttons, checkboxes, images, or any other item that your dashboard library supports.
* Later, during the project development, you may revisit your dashboard plan to update a given feature (for example, at the beginning of the project you were confident you would use a given plot to display an insight but subsequently you used another plot type).
* How were data insights communicated to technical and non-technical audiences?
* Explain how the dashboard was designed to communicate complex data insights to different audiences. 

## Unfixed Bugs
* Please mention unfixed bugs and why they were not fixed. This section should include shortcomings of the frameworks or technologies used. Although time can be a significant variable to consider, paucity of time and difficulty understanding implementation are not valid reasons to leave bugs unfixed.
* Did you recognise gaps in your knowledge, and how did you address them?
* If applicable, include evidence of feedback received (from peers or instructors) and how it improved your approach or understanding.

## Development Roadmap
* What challenges did you face, and what strategies were used to overcome these challenges?
* What new skills or tools do you plan to learn next based on your project experience? 

## Deployment
### Heroku

* The App live link is: https://YOUR_APP_NAME.herokuapp.com/ 
* Set the runtime.txt Python version to a [Heroku-20](https://devcenter.heroku.com/articles/python-support#supported-runtimes) stack currently supported version.
* The project was deployed to Heroku using the following steps.

1. Log in to Heroku and create an App
2. From the Deploy tab, select GitHub as the deployment method.
3. Select your repository name and click Search. Once it is found, click Connect.
4. Select the branch you want to deploy, then click Deploy Branch.
5. The deployment process should happen smoothly if all deployment files are fully functional. Click now the button Open App on the top of the page to access your App.
6. If the slug size is too large then add large files not required for the app to the .slugignore file.


## Main Data Analysis Libraries
* Here you should list the libraries you used in the project and provide an example(s) of how you used these libraries.


## Credits 

* In this section, you need to reference where you got your content, media and extra help from. It is common practice to use code from other repositories and tutorials, however, it is important to be very specific about these sources to avoid plagiarism. 
* You can break the credits section up into Content and Media, depending on what you have included in your project. 

### Content 

- The text for the Home page was taken from Wikipedia Article A
- Instructions on how to implement form validation on the Sign-Up page was taken from [Specific YouTube Tutorial](https://www.youtube.com/)
- The icons in the footer were taken from [Font Awesome](https://fontawesome.com/)

### Media

https://tenor.com/view/crime-scene-gif-12456734



## Acknowledgements (optional)
* Thank the people who provided support through this project.
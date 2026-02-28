# Dublin Fire Brigade: Ambulance Response Analysis

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)](https://docs.microsoft.com/en-us/dax/)
[![Open Data](https://img.shields.io/badge/Open%20Data-Dublin-green?style=for-the-badge)](https://data.gov.ie/)

> **A comprehensive analysis of Dublin Fire Brigade ambulance response data to identify operational performance gaps and investment opportunities.**

**Presenter:** Binay Tiwari  
**Student ID:** 20070646  
**Institution:** Master's in Business Analytics, Dublin

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Key Questions & Impact](#-key-questions--impact)
- [Dataset Overview](#-dataset-overview)
- [Dashboard Features](#-dashboard-features)
- [Key Performance Indicators](#-key-performance-indicators)
- [Critical Findings](#-critical-findings)
- [Performance Analysis](#-performance-analysis)
- [Data Quality Challenges](#-data-quality-challenges)
- [Key Learnings](#-key-learnings)
- [Challenges & Lessons Learned](#-challenges--lessons-learned)
- [Technology Stack](#-technology-stack)
- [Future Improvements](#-future-improvements)
- [How to Use This Dashboard](#-how-to-use-this-dashboard)
- [Connect With Me](#-connect-with-me)

---

## 🎯 Project Overview

This project analyzes Dublin Fire Brigade's ambulance response data to uncover operational inefficiencies and identify strategic investment opportunities. The analysis focuses on response times, regulatory compliance, and bottleneck identification across 16 fire stations serving Dublin.

**Why This Matters:** Response time directly impacts survival rates in medical emergencies. Understanding performance gaps can save lives.

---

## 🔍 Key Questions & Impact

This analysis addresses four critical operational questions:

| Question | Objective | Impact |
|----------|-----------|--------|
| **Slowest Stations?** | Identify stations with the longest response times | Target underperforming locations for resource allocation |
| **Target Met?** | Assess high-criticality calls against the 8-minute regulatory target | Ensure regulatory compliance and quality of service |
| **Time Loss?** | Pinpoint where delays occur: dispatch, travel, or on-scene | Focus improvement efforts on actual bottlenecks |
| **Demand Variation?** | Understand how demand changes by call criticality level | Optimize resource distribution based on urgency patterns |

---

## 📊 Dataset Overview

**Source:** Open Data Dublin - Dublin Fire Brigade Ambulance Calls (2023)

### Dataset Specifications
- **Total Records:** 41,000+ ambulance calls
- **Time Period:** Full year 2023
- **Geographic Coverage:** 16 fire stations across Dublin
- **Data Quality:** ~0.2% invalid records removed after validation

### Key Timestamp Fields
- **TOC (Time of Call):** When emergency call was received
- **ORD (Order Dispatched):** When ambulance was dispatched
- **IA (Incident Arrival):** When ambulance arrived at scene
- **CD (Call Completed):** When patient was handed over/call completed

### Criticality Levels
The dataset includes six criticality classifications:
- **A, B:** High-criticality (Urgent) - 8-minute target
- **C, D:** Medium criticality
- **O, E:** Emergency and other classifications

### Call Distribution by Criticality
- **A Calls:** 19,730 (47.68%) - Highest volume
- **B Calls:** 6,930 (16.74%)
- **C Calls:** 7,550 (18.25%)
- **D Calls:** 5,470 (13.21%)
- **O/E Calls:** Remainder

---

## 🎨 Dashboard Features

The Power BI dashboard provides interactive, multi-dimensional analysis through four key visualization categories:

### 1. **Operational Efficiency View**
- **Station Performance Matrix:** Scatter plot showing call volume vs. on-time performance (% Target Met)
- **Average Response Time by Station:** Horizontal bar chart comparing response times (10.4 - 23.8 minutes)
- **Interactive Slicers:** Filter by Month, Hour, Station Name, and Criticality level

### 2. **Regulatory Compliance View**
- **% Target Met Visualization:** Shows current performance at 28.53% (vs. industry benchmark of 90%+)
- **Scope of Improvement Metric:** Displays 14.56% potential improvement
- **Best Performing Station Highlight:** Tara Street Fire Station identified as top performer

### 3. **Time Breakdown Analysis**
- **Stacked Area Chart:** "Where time is spent" - shows three stages (Call→Mobilization, Mobilization→Arrival, Arrival→Closure) across all 16 stations
- **Stage-Specific Metrics:**
  - Call → Mobilization (Avg: 32.6 min)
  - Mobilization → Arrival (Avg: 13.55 min) 
  - Arrival → Closure (Avg: 74.96 min) ⚠️ **Major Bottleneck**

### 4. **Demand Pattern Analysis**
- **Calls by Criticality:** Column chart showing distribution across all call types
- **Response Time vs. Call Volume:** Dual-axis visualization correlating demand with performance

### Interactive Features
✅ **Dynamic Filtering:** All visuals respond to slicer selections  
✅ **Drill-Through Capability:** Click stations for detailed breakdowns  
✅ **Cross-Filtering:** Selecting one visual filters all others automatically  
✅ **Tooltips:** Hover over data points for detailed metrics  

---

## 📈 Key Performance Indicators

### Primary KPIs

#### 1. **Average Response Time**
- **Overall Average:** 13.55 minutes (Mobilization → Arrival)
- **Best Station:** Tara Street (10.4 min)
- **Worst Stations:** Balbriggan & Skerries (23.8 min each)
- **Target:** 8 minutes for high-criticality calls (A/B)

#### 2. **% Target Met**
- **Current Performance:** 28.53%
- **Industry Benchmark:** 90%+
- **Gap:** 61.47 percentage points below benchmark
- **Compliance Status:** ⚠️ Non-compliant (regulatory concern)

#### 3. **Scope of Improvement**
- **Potential Improvement:** 14.56%
- **Estimated Impact:** ~2 minutes fleet-wide reduction
- **Calculation Method:** Gap between current performance and top-3 station average

### Response Time Breakdown (Three-Stage Analysis)

| Stage | Average Time | % of Total | Status |
|-------|--------------|------------|--------|
| **Call → Mobilization** | 32.6 min | ~27% | Dispatcher efficiency & crew readiness |
| **Mobilization → Arrival** | 13.55 min | ~11% | Core response to scene (Target: 8 min) |
| **Arrival → Closure** | 74.96 min | **62%** | ⚠️ **Major Bottleneck** - On-scene + hospital handoff |

**Critical Insight:** 62% of total response time occurs AFTER ambulance arrival, indicating that the bottleneck is not dispatch or travel but on-scene treatment and hospital handoff processes.

---

## 🚨 Critical Findings

### 1. **Post-Arrival Bottleneck**
> **62% of total response time occurs after ambulance arrival (Arrival → Closure stage)**

- **Problem:** Hospital handoff and on-scene treatment time dominate total response duration
- **Root Cause:** Current data combines on-scene treatment time with hospital transfer/handoff time
- **Impact:** Cannot isolate ambulance-specific vs. hospital-specific delays
- **Recommendation:** Request separated data fields for on-scene vs. hospital time

### 2. **Severe Regulatory Non-Compliance**
> **Only 28.53% of high-criticality calls meet the 8-minute target**

- **Gap:** 61.47 percentage points below 90% industry benchmark
- **Affected Calls:** High-criticality A and B classifications (26,660 calls total)
- **Risk:** Regulatory penalties and increased mortality risk
- **Urgency:** Immediate action required

### 3. **Extreme Station Performance Variation**
> **Response times range from 10.4 to 23.8 minutes - a 129% difference**

**Top Performers:**
- Tara Street: 10.4 min
- Phibsborough: 11.3 min
- North Strand: 11.5 min

**Underperformers:**
- Balbriggan: 23.8 min (+129% vs. best)
- Skerries: 23.8 min (+129% vs. best)
- Tallaght: 16.0 min (+54% vs. best)

**Geographic Factor:** Outer stations (Balbriggan, Skerries) cover larger geographic areas, partially explaining longer response times. Future analysis should normalize for service area size.

### 4. **Dispatch Delay Issue**
> **Average Call → Mobilization time: 32.6 minutes**

- **Problem:** Significant delay between call receipt and ambulance dispatch
- **Contributing Factors:** Dispatcher workload, crew availability, triage processes
- **Improvement Potential:** Reduce by even 5 minutes = ~15% improvement in total response time

---

## 🎯 Performance Analysis

### Station-by-Station Breakdown

| Station Name | Avg Response Time (min) | % Target Met | Call Volume | Performance Tier |
|--------------|------------------------|--------------|-------------|------------------|
| Tara Street | 10.4 | 50%+ | 3,500+ | ⭐ Excellent |
| Phibsborough | 11.3 | 40-50% | 4,000+ | ⭐ Excellent |
| North Strand | 11.5 | 40-50% | 3,800+ | ⭐ Excellent |
| Dolphins Barn | 12.1 | 30-40% | 5,000+ | ✅ Good |
| Donnybrook | 12.5 | 30-40% | 3,200+ | ✅ Good |
| Finglas | 13.5 | 20-30% | 4,500+ | ⚠️ Needs Improvement |
| Kilbarrack | 13.9 | 20-30% | 2,800+ | ⚠️ Needs Improvement |
| Blanchardstown | 14.3 | 20-30% | 6,000+ | ⚠️ Needs Improvement |
| Rathfarnham | 14.4 | 20-30% | 3,600+ | ⚠️ Needs Improvement |
| Dun Laoghaire | 14.5 | 20-30% | 4,200+ | ⚠️ Needs Improvement |
| Swords | 14.5 | 10-20% | 3,900+ | 🔴 Critical |
| Tallaght | 15.5 | 10-20% | 5,500+ | 🔴 Critical |
| Finglas | 16.0 | 10-20% | 4,500+ | 🔴 Critical |
| Skerries | 23.8 | <10% | 1,200+ | 🔴 Critical |
| Balbriggan | 23.8 | <10% | 1,500+ | 🔴 Critical |

### Call Volume vs. Performance Insight
**High-volume stations (Blanchardstown: 6,000+ calls, Tallaght: 5,500+ calls) are underperforming**, indicating resource constraints under demand pressure.

---

## 🛠️ Data Quality Challenges

### Issues Encountered & Solutions Implemented

#### 1. **Midnight Crossovers**
- **Problem:** Calls spanning 23:00-01:00 caused negative time calculation errors
- **Impact:** Affected ~5% of records, distorting daily averages
- **Solution:** Implemented Power BI DAX time arithmetic formulas to handle date transitions
- **DAX Formula Used:**
```dax
Duration = 
VAR StartDate = [TOC_Date]
VAR EndDate = [IA_Date]
VAR TimeDiff = DATEDIFF([TOC_Time], [IA_Time], MINUTE)
RETURN
IF(EndDate > StartDate, 
   TimeDiff + 1440,  // Add 24 hours if next day
   TimeDiff
)
```

#### 2. **Invalid Time Sequences**
- **Problem:** ~0.2% of records had impossible timestamp sequences (e.g., arrival before dispatch)
- **Examples:** IA < ORD, CD < IA, ORD < TOC
- **Solution:** Implemented data validation filter to exclude records with:
  - Negative duration values
  - Out-of-sequence timestamps
  - Missing critical timestamp fields
- **Impact:** Removed 82 invalid records from 41,000+ dataset

#### 3. **Hospital Data Contamination**
- **Problem:** Arrival → Closure time includes both on-scene treatment AND hospital handoff time
- **Impact:** Cannot isolate ambulance delays from hospital delays
- **Current Workaround:** Noted in analysis that 74.96-minute average includes hospital time
- **Recommended Solution:** Request data source to separate:
  - On-scene treatment completion time
  - Hospital arrival time
  - Hospital handoff completion time

#### 4. **Station Geographic Variation**
- **Problem:** Outer stations (Balbriggan, Skerries) cover significantly larger geographic areas
- **Impact:** "Apples-to-oranges" comparison - longer response times may be unavoidable
- **Current Approach:** Added contextual notes in analysis
- **Future Enhancement:** Normalize by:
  - Service area square kilometers
  - Average distance to incidents
  - Population density

---

## 💡 Key Learnings

### 1. **Time Breakdown Reveals True Bottleneck**
**Insight:** 62% of total response time occurs AFTER ambulance arrival (Arrival → Closure stage)

**Implication:** The real bottleneck is NOT:
- ❌ Dispatcher speed
- ❌ Ambulance travel time
- ❌ Road congestion

**The real bottleneck IS:**
- ✅ On-scene treatment duration
- ✅ Hospital handoff processes
- ✅ Emergency department capacity

**Action Required:** Operational improvements must target hospital coordination and on-scene efficiency, not just dispatch/travel optimization.

---

### 2. **Data Quality is Mission-Critical**
**Challenges Overcome:**
- Midnight timestamp crossovers requiring complex DAX formulas
- Invalid time sequences needing validation rules
- Mixed hospital data contaminating ambulance metrics

**Lesson Learned:** Always validate timestamp data with:
- Sequence checks (ORD > TOC, IA > ORD, CD > IA)
- Reasonable range checks (response time < 120 minutes)
- Date transition handling for 24-hour operations

---

### 3. **Visualization Choice Drives Insight Clarity**
**Critical Decision:** Used stacked area chart for time breakdown analysis

**Why It Worked:**
- Immediately visible that "Arrival → Closure" dominates (62% of area)
- Cross-station comparison shows consistent pattern
- Management could see bottleneck in 5 seconds

**Alternative Approaches That Failed:**
- ❌ Pie chart: Couldn't compare across stations
- ❌ Table: Too many numbers, pattern lost
- ❌ Line chart: Misleading temporal interpretation

**Key Principle:** Chart type directly affects whether insights are discovered or buried.

---

### 4. **Context is Essential for Fair Comparison**
**Problem Discovered:** Outer stations (Balbriggan, Skerries) have 2x response times

**Initial Interpretation:** Poor performance  
**Contextual Reality:** Stations cover 3-4x larger geographic areas

**Lesson:** Always seek contextual data:
- Geographic service areas
- Population density
- Road network quality
- Equipment/staffing levels

**Recommendation for Future Work:** Normalize performance by service area characteristics before ranking stations.

---

## 🚧 Challenges & Lessons Learned

### What Went Wrong → What We Learned

| Challenge | Impact | Lesson Learned | Future Action |
|-----------|--------|----------------|---------------|
| **Hospital data contamination** | Cannot isolate ambulance-specific delays | Upstream data collection needs to separate concerns | Request granular timestamps from data source |
| **Geographic variation** | Station comparisons not "apples-to-apples" | Contextual data is vital for fair comparisons | Add service area size and population density to model |
| **Dashboard density** | Initial version too cluttered, insights buried | Simplify: one clear message per page is more effective | Redesign with separate pages for each key question |
| **Forgot to save!** | Lost work during development | Always enable auto-save and version control | Implement Git for Power BI files (.pbix) |
| **Timestamp complexity** | Midnight crossovers broke calculations | Edge cases matter in 24/7 operations | Build comprehensive validation rules upfront |

---

## 🔧 Technology Stack

### Why Power BI? A Strategic Choice

This project leveraged **Power BI** as the primary analytics platform for four strategic reasons:

#### 1. **Slicer Interactivity** 🎚️
- Built-in, self-serve filtering across all visuals
- Users can explore data by Month, Hour, Station, and Criticality
- No coding required for end-user exploration

#### 2. **DAX Formulas** 🧮
- Powerful time arithmetic for complex timestamp logic
- Handled midnight crossovers and multi-stage duration calculations
- Custom measures for KPIs (% Target Met, Scope of Improvement)

**Example DAX Measure:**
```dax
% Target Met = 
DIVIDE(
    CALCULATE(
        COUNTROWS('Ambulance Calls'),
        'Ambulance Calls'[Response Time] <= 8,
        'Ambulance Calls'[Criticality] IN {"A", "B"}
    ),
    CALCULATE(
        COUNTROWS('Ambulance Calls'),
        'Ambulance Calls'[Criticality] IN {"A", "B"}
    ),
    0
)
```

#### 3. **Excel/CSV Integration** 📁
- Easy data loading from Open Data Dublin CSV files
- Familiar interface for business users
- No complex ETL pipelines required

#### 4. **Learning Value** 📚
- Industry-standard tool (used by 97% of Fortune 500)
- Resume-building skill for business analytics roles
- Strong community support and documentation

### Tools & Technologies Used

| Category | Technology | Purpose |
|----------|-----------|---------|
| **Data Source** | Open Data Dublin (CSV) | 41K+ ambulance call records |
| **Data Preparation** | Power Query | Data cleaning, transformation, validation |
| **Analytics Engine** | Power BI Desktop | Dashboard development |
| **Calculation Language** | DAX (Data Analysis Expressions) | KPI calculations, time arithmetic |
| **Visualization** | Power BI Visuals | Charts, slicers, KPI cards |
| **Deployment** | Power BI Service (optional) | Dashboard sharing and collaboration |

---

## 🚀 Future Improvements

### Planned Enhancements

#### 1. **Data Merging & Temporal Expansion** 📅
**Current State:** Single year (2023) analysis  
**Future Goal:** Multi-year trend analysis

**Implementation:**
- Merge 2021-2024 data for longitudinal insights
- Identify seasonal patterns (winter vs. summer demand)
- Track year-over-year performance improvements

**Expected Benefit:** Understand if performance is improving/declining over time

---

#### 2. **Simplified Dashboard Layout** 🎨
**Current Issue:** Too much information on single pages  
**Future Design:** One key message per dashboard page

**Planned Structure:**
- **Page 1:** Executive Summary (top 3 KPIs)
- **Page 2:** Station Performance Deep-Dive
- **Page 3:** Time Breakdown Analysis
- **Page 4:** Regulatory Compliance Focus
- **Page 5:** Improvement Opportunities

**Expected Benefit:** Faster insight discovery, better stakeholder presentations

---

#### 3. **Temporal Pattern Analysis** ⏰
**Gap Identified:** No hour-of-day or day-of-week analysis in current version  
**Future Analysis:**

**Questions to Answer:**
- Which hours have longest response times? (Rush hour impact?)
- Are weekends slower than weekdays?
- Do night shifts perform differently?
- Are there monthly patterns (holidays, events)?

**Implementation:** Add time-series visuals by hour/day/month

---

#### 4. **Geographic Context Integration** 🗺️
**Current Limitation:** No map visualization or service area data  
**Future Enhancement:**

**Data to Add:**
- Station latitude/longitude
- Service area boundaries (GeoJSON)
- Road network quality scores
- Population density by area

**New Visuals:**
- **Heat map:** Response time by geographic region
- **Service area map:** Visualize coverage gaps
- **Normalized performance:** Response time per square kilometer

**Expected Benefit:** Fair station comparisons and resource allocation optimization

---

#### 5. **Better Source Data** 📊
**Recommendations to Dublin Fire Brigade:**

**Timestamp Separation:**
- Add "On-Scene Treatment Complete" timestamp
- Add "Hospital Arrival" timestamp  
- Add "Hospital Handoff Complete" timestamp

**Additional Fields:**
- Distance traveled to incident (km)
- Number of units dispatched
- Crew size per call
- Weather conditions
- Traffic density score

**Expected Benefit:** Isolate controllable delays from external factors

---

#### 6. **Predictive Analytics** 🤖
**Future Direction:** Machine learning models

**Models to Build:**
- **Demand Forecasting:** Predict call volume by hour/location
- **Response Time Prediction:** Estimate response time based on factors
- **Resource Optimization:** Recommend optimal ambulance positioning

**Technology Stack:** Python (scikit-learn, prophet) + Power BI integration

---

#### 7. **Real-Time Monitoring** ⚡
**Vision:** Live operational dashboard

**Features:**
- Real-time call tracking
- Alert system for long response times
- Dynamic resource allocation suggestions
- Live KPI updates

**Requirements:** API integration with Dublin Fire Brigade systems

---

## 📖 How to Use This Dashboard

### For Analysts & Researchers
1. **Clone/Download** the Power BI file (.pbix)
2. **Data Source:** Obtain latest data from [Open Data Dublin](https://data.gov.ie/)
3. **Refresh Data:** Power Query will automatically clean and transform new data
4. **Explore:** Use slicers to filter by Month, Hour, Station, Criticality
5. **Export:** Generate reports for stakeholders

### For Stakeholders
1. **Executive View:** Start with KPI cards (% Target Met, Avg Response Time)
2. **Drill Down:** Click on stations or criticality levels for detailed breakdowns
3. **Compare:** Use scatter plots to identify outlier stations
4. **Action:** Focus on stations with <30% Target Met rate

### For Technical Users
1. **DAX Measures:** Open "Modeling" tab to view custom calculations
2. **Data Model:** Review relationships in "Model" view
3. **Power Query:** Check "Transform Data" for cleaning steps
4. **Validation Rules:** See data quality filters in Query Editor

---

## 🎓 Academic Context

**Course:** Business Analytics  
**Institution:** Dublin (Master's Program)  
**Presenter:** Binay Tiwari  
**Student ID:** 20070646  

**Skills Demonstrated:**
- Data cleaning and validation
- KPI development and tracking
- Dashboard design and storytelling
- DAX formula creation
- Regulatory compliance analysis
- Operational performance analysis
- Critical thinking and problem-solving

---

## 📧 Connect With Me

**Binay Tiwari**  
Master's in Business Analytics | Dublin

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yourprofile)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/yourprofile)
[![Portfolio](https://img.shields.io/badge/Portfolio-FF5722?style=for-the-badge&logo=google-chrome&logoColor=white)](https://yourportfolio.com)

**Open to:**
- Business Analytics roles
- Data Analytics positions  
- Power BI consulting opportunities
- Collaboration on public data projects

---

## 📄 License

This project uses public data from Open Data Dublin. The analysis and visualizations are original work by Binay Tiwari.

**Data Source License:** [Open Data Commons Open Database License (ODbL)](https://opendatacommons.org/licenses/odbl/)

---

## 🙏 Acknowledgments

- **Open Data Dublin** for providing high-quality public datasets
- **Dublin Fire Brigade** for transparency in sharing operational data
- **Master's Program Instructors** for guidance on analytical methodologies
- **Power BI Community** for DAX formula support and best practices

---

## 📊 Project Statistics

![Dashboard Views](https://img.shields.io/badge/Dashboard%20Views-4-blue)
![Data Points](https://img.shields.io/badge/Data%20Points-41K+-green)
![Stations Analyzed](https://img.shields.io/badge/Stations-16-orange)
![KPIs Tracked](https://img.shields.io/badge/KPIs-5+-red)

---

## 🔖 Tags

`#PowerBI` `#DataAnalytics` `#BusinessIntelligence` `#EmergencyServices` `#PublicData` `#DAX` `#PerformanceAnalysis` `#Healthcare` `#Dublin` `#DataVisualization` `#KPIs` `#OperationalEfficiency`

---

**⭐ If you found this analysis insightful, please consider starring this repository!**

**📣 Share this project to help improve emergency response services through data-driven insights.**

---

*Last Updated: February 2026*  
*Project Status: ✅ Complete | 🚀 Ready for Enhancements*
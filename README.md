# ➕Pixel Mobile Case Study: Variance Analysis  

# For the comprehensive overview of the project, please consider accessing [file](https://docs.google.com/spreadsheets/d/1LfNkXNxQdUbBkY8S2Umj_gvQxxmVdfgPPMLsIdCUhxw/edit?gid=186228482#gid=186228482)

## 📋 Introduction  
Pixel Mobile is a mobile manufacturing company. In 2023, the management team set production targets for their new Pixel Moon mobile models: Mini, Max, and Pro. To achieve these targets, they allocated specific production budgets for each region, factory, model, and month, determining the number of units to be produced.

This project focuses on conducting a **variance analysis** to evaluate the performance of production against these targets. Insights will help pinpoint areas of success and opportunities for improvement.  

## 🎯 Objective  
The goal is to analyze production performance using variance analysis by focusing on two key aspects:  
1. **Region-wise Variance Analysis:**  
   - Determine actual vs. budgeted production for each region and identify gaps.  
2. **Model-wise Variance Analysis:**  
   - Evaluate which Pixel Moon models (Mini, Max, Pro) met or exceeded their targets and which fell short.  

This analysis will offer actionable insights for improving future production planning and allocation strategies.  

## 📊 Data Overview  
### Datasets Used:  
| Dataset             | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **Budget Sheet**    | Budgeted production targets by region, model, month, and factory.          |
| **Actual Sheet**    | Actual production details for all batches, including quantities produced.  |
| **Abbreviation Sheet** | Abbreviations and codes used in the dataset with their full explanations. |

### Data Structure:  
| **Column Name**     | **Description**                                                             |
|---------------------|-----------------------------------------------------------------------------|
| Region              | Geographic area of production (e.g., North, South).                        |
| Factory             | Factory code where production occurred.                                    |
| Model               | Pixel Moon mobile model (Mini, Max, Pro).                                  |
| Month               | Month of production (Jan-Dec).                                             |
| Units Budgeted      | Expected production numbers for the given time period.                     |
| Units Produced      | Actual production numbers from the Actual Sheet.                           |
| Variance            | Difference between actual and budgeted production.                         |

## 🧹Data Cleaning 
The encoded batch details follow a specific structure, and this decoder helps extract meaningful information, such as production ID, date, region, factory code, and product model.
Here’s how the batch ID is structured and decoded:

| **Batch Details Example**      | **PRD1002012723SF003SMAX**         |
|--------------------------------|------------------------------------|
| **Field**                      | **Extraction Rule**                | **Example Value** |
| Cleaned Batch ID               | Remove spaces and `/`              | `PRD1002012723SF003SMAX` |
| Production ID                  | First 7 letters                    | `PRD1002`          |
| Month                          | 8th & 9th letters                  | `01`              |
| Day                            | 10th & 11th letters                | `27`              |
| Year                           | 12th & 13th letters                | `23`              |
| Region                         | 14th letter                        | `S`               |
| Factory Code                   | 15th to 19th letters               | `F003S`           |
| Product Model                  | Letters after the 20th position    | `MAX`             |

We used the rules listed above or utilize the provided script to extract and clean the fields.
#### Input:
`//PRD1002012723SF003SMAX///`

#### Cleaned Batch ID:
`PRD1002012723SF003SMAX`

#### Extracted Details:
- **Production ID**: `PRD1002`
- **Month**: `01`
- **Day**: `27`
- **Year**: `23`
- **Region**: `S`
- **Factory Code**: `F003S`
- **Product Model**: `MAX`

## 📊Exploratory Data Analysis

### Month-wise Variance Report
This table presents the month-wise comparison of budgeted quantities against actual quantities, along with the variance.

| **Month**     | **Budgeted Quantity** | **Actual Quantity** | **Variance** |
|---------------|------------------------|---------------------|--------------|
| January       | 14,069                | 12,124              | -1,945       |
| February      | 16,296                | 14,044              | -2,252       |
| March         | 14,962                | 12,827              | -2,135       |
| April         | 15,894                | 13,734              | -2,160       |
| May           | 16,556                | 14,483              | -2,073       |
| June          | 16,164                | 13,984              | -2,180       |
| July          | 15,259                | 13,342              | -1,917       |
| August        | 15,484                | 14,154              | -1,330       |
| September     | 15,108                | 13,361              | -1,747       |
| October       | 13,357                | 13,704              | **+347**     |
| November      | 12,447                | 13,322              | **+875**     |
| December      | 10,433                | 12,294              | **+1,861**   |

- **Variance**: Calculated as
`Actual Quantity - Budgeted Quantity`.
- Negative variances indicate a shortfall in the actual quantity compared to the budgeted quantity.
- Positive variances indicate the actual quantity exceeded the budgeted quantity.
- 
- **Months with Positive Variance**:
  - October: +347
  - November: +875
  - December: +1,861
- **Largest Negative Variance**: February (-2,252)
- **Smallest Negative Variance**: August (-1,330)

### Model-wise Variance Report

This table presents the model-wise comparison of budgeted quantities against actual quantities, along with the variance.

| **Model**     | **Budgeted Quantity** | **Actual Quantity** | **Variance** |
|---------------|------------------------|---------------------|--------------|
| MINI          | 59,124                | 54,291              | -4,833       |
| MAX           | 58,533                | 53,328              | -5,205       |
| PRO           | 58,372                | 53,754              | -4,618       |

- **Largest Negative Variance**: MAX (-5,205)
- **Smallest Negative Variance**: PRO (-4,618)
- **Overall Trend**: All models show a negative variance, indicating that actual quantities are below budgeted expectations.

### Quarter-wise Variance Report

This table presents the quarter-wise comparison of budgeted quantities against actual quantities, along with the variance.

| **Quarter**   | **Budgeted Quantity** | **Actual Quantity** | **Variance** |
|---------------|------------------------|---------------------|--------------|
| Q1            | 45,327                | 38,995              | -6,332       |
| Q2            | 48,614                | 42,201              | -6,413       |
| Q3            | 45,851                | 40,857              | -4,994       |
| Q4            | 36,237                | 39,320              | **+3,083**   |

- **Highest Negative Variance**: Q2 (-6,413)  
- **Positive Variance**: Q4 (+3,083)  
- **Trend**:  
  - The first three quarters show negative variance, indicating lower-than-expected performance.  
  - Q4 exceeds budgeted expectations, possibly due to seasonal demand or improved operational efficiency.

### Quarter-wise Variance Analysis
This table details the quarter-wise variance for each model, breaking down performance by MINI, MAX, and PRO models.

| **Quarter**   | **MINI**   | **MAX**   | **PRO**   |
|---------------|------------|-----------|-----------|
| Q1            | -2,230     | -2,106    | -1,996    |
| Q2            | -2,142     | -2,001    | -2,270    |
| Q3            | -1,744     | -1,992    | -1,258    |
| Q4            | +1,283     | +894      | +906      |

- **Worst Performing Quarter**:  
  - Q2 has the highest negative variance for the PRO model (-2,270).  
  - All models experienced a decline in Q2.  

- **Best Performing Quarter**:  
  - Q4 shows positive variance across all models:
    - MINI: +1,283  
    - MAX: +894  
    - PRO: +906  

- **Overall Trend**:  
  - Negative variance dominates Q1 through Q3, indicating underperformance.  
  - Q4 saw a rebound with all models exceeding budgeted quantities.
 
 ### Quarter-wise Variance Analysis (%)
This table presents the quarter-wise percentage variance for each model, highlighting the performance trends.

| **Quarter**   | **MINI**     | **MAX**     | **PRO**     |
|---------------|--------------|-------------|-------------|
| Q1            | -14.25%      | -13.29%     | -14.43%     |
| Q2            | -12.65%      | -13.82%     | -13.20%     |
| Q3            | -12.14%      | -12.89%     | -7.85%      |
| Q4            | +10.53%      | +7.01%      | +8.01%      |

- **Largest Negative Variance (%)**:  
  - Q1: The PRO model had the largest negative percentage variance at **-14.43%**.
  - All models show significant underperformance in Q1 and Q2.

- **Positive Variance in Q4 (%)**:  
  - MINI: **+10.53%** (strongest positive growth).  
  - MAX: **+7.01%**.  
  - PRO: **+8.01%**.  

- **Overall Trend**:
  - Performance dips in Q1 through Q3 with recovery in Q4.  
  - MINI consistently shows the largest percentage shifts, indicating higher sensitivity to demand or operational changes.

### Region-wise Variance Report
This table provides a region-wise comparison of budgeted quantities against actual quantities, along with the variance.

| **Region**   | **Budgeted Quantity** | **Actual Quantity** | **Variance** |
|--------------|------------------------|---------------------|--------------|
| North        | 60,572                | 54,607              | -5,965       |
| South        | 57,395                | 54,602              | -2,793       |
| West         | 58,062                | 52,164              | -5,898       |

- **Highest Negative Variance**:  
  - **North Region**: -5,965, indicating a significant shortfall compared to the budgeted quantity.
  
- **Lowest Negative Variance**:  
  - **South Region**: -2,793, which is relatively closer to meeting expectations.

- **Overall Trend**:  
  - All regions experienced negative variance, with actual quantities falling short of the budgeted targets.
  - The **North and West regions** show similar levels of underperformance, suggesting operational or demand challenges in these areas.

### Region-wise Variance Analysis
This table provides a breakdown of the variance for each model in different regions.

| **Region**   | **MINI**   | **MAX**   | **PRO**   |
|--------------|------------|-----------|-----------|
| North        | -955       | -648      | -4,362    |
| South        | -3,302     | -200      | -200      |
| West         | -576       | -4,357    | -965      |

- **North Region**:  
  - The PRO model experienced the largest negative variance (-4,362), highlighting significant shortfalls in demand or production.  
  - MINI and MAX had relatively minor variances (-955 and -648, respectively).  

- **South Region**:  
  - MINI showed the largest variance (-3,302).  
  - MAX and PRO performed similarly with minor shortfalls (-200 each).  

- **West Region**:  
  - The MAX model had the highest negative variance (-4,357).  
  - MINI and PRO had lower variances (-576 and -965, respectively).  

- **Overall Trends**:  
  - The PRO model underperformed significantly in the **North** region, while the MAX model struggled in the **West**.  
  - The **South** region displayed a more balanced variance across all models, with the MINI model being the most affected.

### Region-wise Variance Analysis (%)
This table outlines the percentage variance for each model in different regions.

| **Region**   | **MINI**     | **MAX**     | **PRO**     |
|--------------|--------------|-------------|-------------|
| North        | -6.64%       | -5.63%      | -12.58%     |
| South        | -9.56%       | -1.77%      | -1.73%      |
| West         | -5.64%       | -12.20%     | -7.96%      |

- **North Region**:  
  - The PRO model had the highest negative variance (-12.58 %), showing a significant performance gap.  
  - MINI (-6.64%) and MAX (-5.63%) had moderate declines.  

- **South Region**:  
  - MINI exhibited the largest percentage variance (-9.56%), while MAX (-1.77%) and PRO (-1.73%) showed relatively minor underperformance.  

- **West Region**:  
  - MAX had the largest variance (-12.20%), followed by PRO (-7.96%) and MINI (-5.64%).  

- **Overall Trends**:  
  - The **North** and **West** regions faced significant challenges with the PRO and MAX models, respectively.  
  - The **South** region's variance is comparatively lower, except for the MINI model, which showed a notable gap.  


## Dashboard
![image](https://github.com/user-attachments/assets/c4296d77-724d-4031-b27f-e9059e24818d)

## Summary of Insights
**Model:** The best performing model for us in terms of production variance is "PRO". It has lesser quantity production variance as compare to other two models.

**Region:** The best-performing region for us in terms of production variance is "South". Though all the region had lower production than their budgeted production quantities.

**Quarter:** In "Q4", the company has positive production variance and in all other three quarters the variance is negative.


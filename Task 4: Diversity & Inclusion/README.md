# Diversity & Inclusion | PWC Virtual Case Experience

![Cover](https://github.com/calmk/Diversity-and-Inclusion-PWC-Virtual-Case-Experience/assets/100661121/28f2beff-1a39-43a9-afe4-a729035b70ad)


## Table of contents
- [Problem Statement](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%204:%20Diversity%20&%20Inclusion#Problem-Statement)
- [Data Sourcing](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%204:%20Diversity%20&%20Inclusion#Data-Sourcing)
- [Data Preparation](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%204:%20Diversity%20&%20Inclusion#Data-Preparation)
- [Data Modeling](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%204:%20Diversity%20&%20Inclusion#Data-Modeling)
- [Data Visualization](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%204:%20Diversity%20&%20Inclusion#Data-Visualization)
- [Analysis and Insights](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%204:%20Diversity%20&%20Inclusion#Analysis-and-Insights)
- [Shareable Link](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%204:%20Diversity%20&%20Inclusion#Shareable-Link)

# Problem Statement

- **Problem:** Human Resources at our telecom client is highly into diversity and inclusion. They’ve been working hard to improve gender balance at the executive management level, but they’re not seeing any progress.
- **Objective**:
    - Define proper KPIs in hiring, promotion, performance and turnover
    - Create a visualization for the HR manager that reflects all relevant Key Performance indicators(KPIs) and metrics in the dataset.
    - Define some root causes of their slow progress in improving gender balance at the executive management level might be
    - Allows for minimal interaction.
   
# Data Sourcing

The dataset used for this analysis was provided by [Pwc Switzerland](https://www.pwc.ch/en/careers-with-pwc/students/virtual-case-experience.html) and available here: [Diversity & Inclusion](https://github.com/calmk/PWC-Virtual-Case-Experience/blob/main/Task%204%3A%20Diversity%20%26%20Inclusion/03%20Diversity-Inclusion-Dataset.xlsx)

# Data Preparation

The dataset was loaded into Microsoft Power BI Desktop for modeling after transformation in Power Query.

### **Metadata**

The tabulation below shows the metadata of `Diversity & Inclusion` dataset:
| File name | 03 Diversity-Inclusion-Dataset |
| --- | --- |
| Format | .xlsx |
| Size | 176 KB |
| Fields | 32 |
| Entities | 500 |

The tabulation below shows the Diversity & Inclusion table with its field's names and their description:
| Column Name | Description |
| --- | --- |
| Employee ID | Represents the unique number of the employee in the dataset |
| Gender | Describes the gender of the employee |
| Job Level after FY20 promotions | Describes the job level of the employee after being promoted in FY20 |
| New hire FY20? | Describes if the employee is a new hire in FY20 |
| FY20 Performance Rating | Represents the performance rating of the employee in FY20 |
| Promotion in FY21? | Describes if the employee is being promoted in FY21 |
| In base group for Promotion FY21 | Describes if the employee is being selected for promotion in FY21 |
| Target hire balance | Describes the target hire balance of the employee |
| FY20 leaver? | Describes if the employee is a leaver in FY20 |
| In base group for turnover FY20 | Describes if the employee is in a group for turnover in FY20 |
| Department @01.07.2020 | Describes the department each employee belongs to as of January 7, 2020 |
| Leaver FY | Describes if the employee is a leaver in an FY |
| Job Level after FY21 promotions | Describes the job level of the employee after being promoted in FY21 |
| Last Department in FY20 | Describes the last department each employee belongs in FY20 |
| FTE group | Describes if the employee belongs to an FTE group |
| Time type | Describes the contract type employee |
| Department & JL group PRA status | Describes the department and JL group PRA status of the employee |
| Department & JL group for PRA | Describes the department and JL group PRA of the employee |
| Job Level group PRA status | Describes the job level group PRA status of the employee |
| Job Level group for PRA | Describes the job level group PRA of the employee |
| Time in Job Level @01.07.2020 | Describes the time in job level of the employee |
| Job Level before FY20 promotions | Describes the job level of the employee before being promoted in FY20 |
| Promotion in FY20? | Describes if the employee is being promoted in FY20 |
| FY19 Performance Rating | Describes the performance rating of the employee in FY19 |
| Age group | Describes the age group of the employee |
| Age @01.07.2020 | Represents the age of the employee as of January 07, 2020 |
| Nationality 1 | Describes the nationality of the employee at the state level |
| Region group: nationality 1 | Describes the nationality of the employee at the country level |
| Broad region group: nationality 1 | Describes the nationality of the employee at the regional level |
| Last hire date | Describes the last hire date of the employee |
| Years since the last hire | Represents the number of years since the last hire of the employee |
| Rand | generates a random number for each entry in the dataset |

### Data Cleaning

Data Cleaning for the dataset was done in Power Query as follows:

- Unnecessary columns were removed
- Unnecessary rows were filtered
- Each of the columns in the table was validated to have the correct data type

### Data Transformation

- For easy observing and analyzing, the extracted text had been applied for those columns: `Job Level after FY21 promotions`, `Job Level after FY20 promotions`
    - Extracted Text After Delimiter = `Table.TransformColumns(#"Extracted Text After Delimiter1", {{"Job Level before FY20 promotions", each Text.AfterDelimiter(_, "-"), type text}})`

# Data Modeling

After the dataset was cleaned and transformed, it was ready to be modeled. Because the dataset is just included one table, the Data Modeling is nothing much to modify
- `Measure` was created to store all DAX measures for ensuring the organization


![data modeling](https://github.com/calmk/Diversity-and-Inclusion-PWC-Virtual-Case-Experience/assets/100661121/6fc48c03-f76c-4e32-9cc6-7f7768bbdae1)



# Data Visualization

Data visualization for the dataset was done in Microsoft Power BI Desktop, the dashboard includes three main dashboards and three tooltip pages:

- HR Overview
- Performance
- Hiring & Promotion

![detail](https://github.com/calmk/Diversity-and-Inclusion-PWC-Virtual-Case-Experience/assets/100661121/7d865f96-024a-4e87-8d06-e4b7dabe76b6)




### Dashboard Type

Dashboard by the level of detail: **Operational dashboard**

Dashboard by use-case: **Exploratory**

Target audience: **Human Resource Manager, Analyst**

### Key Performance Indicators and Metrics:

**About HR Overview:**

- Number of employees, leavers
- Number of promotions and hiring in FY20
- Average Performance
- Age distribution
- Nationality distribution
- Job-level distribution
- Time type distribution

**About Performance:**

- Average Performance of gender, leavers
- Performance Rate distribution
- Average Performance Rate by Positions, Age, Region
- Comparison performance between leaver and non-leaver by department

**About Hiring & Promotion:**

- Indicators of the gender balance of new hire FY20, Promotion FY21, Turnover rate
- Executive gender balance
- Average Time at the Job level
- Hiring trend and hiring distribution by nationality
- Promotion and Turnover rate FY 21

### Measures

- **Calculated measures:**
    - Turnover Rate = `Divide(Calculate(distinctcount('HR dataset'[Employee ID]),Filter('HR dataset','HR dataset'[FY20 leaver?]="Yes")),Divide(Calculate(distinctcount('HR dataset'[Employee ID]),Filter('HR dataset','HR dataset'[In base group for turnover FY20]="Y"))+Calculate(distinctcount('HR dataset'[Employee ID]),Filter('HR dataset',NOT('HR dataset'[Department @01.07.2020]=BLANK()))),2))`
    - #newhire = `CALCULATE(COUNT('HR dataset'[New hire FY20?]),KEEPFILTERS('HR dataset'[New hire FY20?] = "Yes"))`
    - #PromoteFY20 =
    
    `VAR promote = CALCULATE(COUNT('HR dataset'[Promotion in FY20?]),'HR dataset'[Promotion in FY20?] = "Y")
    Return` 
    
    `IF(ISBLANK(promote),0,promote)`
    
- **Format measures**
    - Welcome text = 
    `VAR Hour = HOUR(NOW())
    VAR Greeting = 
    SWITCH(
        TRUE(),
        Hour >= 0 && Hour < 5, "Good Night",
        Hour >= 5 && Hour < 12, "Good Morning",
        Hour >= 12 && Hour < 18, "Good Afternoon",
        Hour >= 18 && Hour < 24, "Good Evening"
    )
    RETURN
    Greeting & " " & "Manager!"`
    - Performance Rating % =
        
        `VAR __BASELINE_VALUE = SUM('HR dataset'[FY20 Performance Rating])
        VAR __VALUE_TO_COMPARE = SUM('HR dataset'[FY19 Performance Rating])
        VAR change = DIVIDE(__VALUE_TO_COMPARE - __BASELINE_VALUE, __BASELINE_VALUE)
        RETURN
        		IF(NOT ISBLANK(__VALUE_TO_COMPARE), 
        		SWITCH(TRUE(),
                change <= 0,"▼"  & " " & FORMAT(change*-1,"percent"),
                change > 0, "▲" & " " & FORMAT(change,"percent")))`
        

### Format using

**Font:** SF Pro Display

**Color:** Datacamp palette

# Analysis and Insights

The purpose of this dashboard is to serve as self-exploratory for managers, but I still note some highlighted points that I recognize that some root causes of their slow progress in improving gender balance at the executive management level might be below:

- Employees who were promoted twice within two years had very low-performance ratings, while those who left had higher ratings.
- According to the data, it appears that a significant portion of employees has been stagnating in their current job level for more than two years, despite working diligently. Promotions have not been forthcoming, female directors, in particular, require more time to be nominated as executives compared to their male counterparts.
- There is a significant gender imbalance in the distribution of new hires and promotions for executive positions, despite the fact that these female directors perform better.
- A potential factor contributing to the slow progress in achieving gender balance at the executive management level is that the performance evaluations for promotion at management levels may not be entirely objective and honest. This could result in qualified female candidates being overlooked for executive positions, despite their superior performance compared to their male counterparts.


# Shareable Link

You can interact and have fun with the dashboard here:

[Microsoft PowerBI](https://app.powerbi.com/view?r=eyJrIjoiM2Y2YzE3ZGQtZTliNi00NzVhLTkxNTktMDQ2YTAzNTY3OWMwIiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9&embedImagePlaceholder=true) | [novyPro](https://www.novypro.com/project/diversity--inclusion-|-pwc-virtual-case-experience)


### Huge thanks to you for joining this creation journey with me.  Hope you all are doing great! :pray::pray::pray::relaxed:


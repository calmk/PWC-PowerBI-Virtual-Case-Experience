<H1> Call Center Analysis | Pwc Switzerland Power BI Virtual Case Experience 
  
![Cover for github](https://user-images.githubusercontent.com/100661121/233259968-0c733411-1ce8-467b-ad94-a66a09e58bd8.png)




## Table of contents
- [Problem Statement](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%202:%20Call%20Center%20Dashboard#Problem-Statement)
- [Data Preparation](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%202:%20Call%20Center%20Dashboard#Data-Preparation)
- [Data Modeling](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%202:%20Call%20Center%20Dashboard#Data-Modeling)
- [Data Visualization](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%202:%20Call%20Center%20Dashboard#Data-Visualization)
- [Analysis and Insights](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%202:%20Call%20Center%20Dashboard#Analysis-and-Insights)
- [Shareable Link](https://github.com/calmk/PWC-Virtual-Case-Experience/tree/main/Task%202:%20Call%20Center%20Dashboard#Shareable-Link)


# Problem Statement

- **Problem:** The manager at PhoneNow (a big telecom company) is seeking transparency and insight into the Call Center dataset to gain an accurate overview of long-term customer and agent behavior trends.
- **Objective:** The purpose of this analysis is to create a dashboard in Power BI for Call Center Manager that reflects all relevant Key Performance Indicators (KPIs) and metrics to:
    - Self-exploratory call trends
    - Overview of the agent’s performance and behaviors
    - Overview the customer satisfaction
    - Contain many metrics and plots related to a single area of business for discussing with higher managers and generating further analysis.
    - Allows for minimal interaction
- **Possible KPIs** include (but are not limited to):
    - Overall customer satisfaction
    - Overall calls answered/abandoned
    - Calls by time
    - Average speed of answer
    - Agents performance quadrant -> average handle time(talk duration) vs calls answered

# Data Sourcing

The Dataset used for this analysis was provided by [Pwc Switzerland](https://www.pwc.ch/en/careers-with-pwc/students/virtual-case-experience.html) and available here: [Call Center Dataset](https://github.com/calmk/PWC-Virtual-Case-Experience/blob/main/Task%202%3A%20Call%20Center%20Dashboard/01%20Call-Center-Dataset.xlsx)
# Data Preparation

The dataset was loaded into Microsoft Power BI Desktop for transformation in Power Query and modeling.

### Metadata

The tabulation below shows the metadata of `Call Center` dataset:

| File name |01 Call-Center-Dataset  |
| --- | --- |
| Format | .xlsx |
| Size | 249KB |
| Fields | 10 |
| Entities | 5000 |
| Time | January 1, 2021 - March 31, 2021 |

The tabulation below shows the `Call Center` table with its fields names and their description:

| Field Name | Description | Data Type |
| --- | --- | --- |
| Call Id | Represents every unique observation in the dataset | Text  |
| Agent | Describes the name of the agent | Text |
| Date | Describes the date of the call | Date |
| Time | Represents the time of the call | Date/Time |
| Topic | Describes the topic of the caller | Text |
| Answered (Y/N) | Describes if the call was answered or not | Text |
| Resolved | Describes if the problem was Resolved or not | Text |
| Speed of answer in seconds | Represents the speed of answer in seconds | Decimal number |
| AvgTalkDuration | Represents the average talk duration of a call | Time |
| Satisfaction rating | Represents the satisfaction rating of the agent during the call | Decimal number |

### Data Cleaning

Data Cleaning for the dataset was done in Power Query as follows:

- Unnecessary columns were removed
- Each of the columns in the table was validated to have the correct data type
- Unnecessary rows were removed

### Data Transformation

To ensure the comprehensive satisfaction of customers, an additional column named `Satisfaction Likert` was created for referencing using the M-formula: 

`Table.AddColumn(#"Added Custom", "Satisfaction Likert", each if [Satisfaction rating] = 1 then "Very poor" else if [Satisfaction rating] = 2 then "Poor" else if [Satisfaction rating] = 3 then "Average" else if [Satisfaction rating] = 4 then "Good" else "Very good")`

Here is a breakdown of what the formula does:

For the dataset, we want to transform the satisfaction rating from number to text based on the Likert scale with the condition if `Satisfaction rating = 1`, it will display the rating as `“Very poor”`, respectively for each value of `Satisfaction rating` .

# Data Modeling

After the dataset was cleaned and transformed, it was ready to be modeled, but the dataset just included one table, so the Data Modeling is nothing much to modify

# Data Visualization
![dashboard github](https://user-images.githubusercontent.com/100661121/233076182-dedd0efc-5704-4886-b4d0-b80a841e9773.png)


Data visualization for the datasets was done in Microsoft Power BI Desktop and designed in PowerPoint, the dashboard includes:

- One main dashboard
- Six tooltip pages

### Dashboard type
Dashboard by the level of detail: **Tactical dashboard**

Dashboard by use-case: **Exploratory**

Target audience: **Team lead & Manager** (non-technical users)

### Key Performance Indicators and Metrics:

**About Calls and Agents:** 

- Overall calls answered/abandoned
- Calls received by time, day 
- Average speed of answer, handle duration
- Resolved rate by Agents, Topics
- Agent’s performance quadrant -> average handle time (talk duration) vs calls answered

**About Customer satisfaction:**

- Overall customer satisfaction
- Customer satisfaction distribution by Agents, Topics
### Measures

The measure used in visualization are:

- **Calculated measures:**

  - Number of answered = `Calculate(distinctcount('Call Center'[Call Id]),Filter('Call Center','Call Center'[Answered (Y/N)]="Y"))`
  - Abandoned Rate = `DIVIDE(COUNT('Call Center'[Call Id]) - [Number of Answer], COUNT('Call Center'[Call Id]))`
  - Number of resolved = `Calculate(distinctcount('Call Center'[Call Id]),Filter('Call Center','Call Center'[Resolved]="Y"))`
  - Average satisfaction rating = `Average('Call Center'[Satisfaction rating])`
  - Average Speed of answer = `Average('Call Center'[Average Speed of answer in seconds])`
  - Operation hour DAX = `FORMAT('Call Center'[Time], "hh:mm")`
  - duration = `MINUTE('Call Center'[AvgTalkDuration])*60 + SECOND('Call Center'[AvgTalkDuration])`
- **Format measures:**

  - Welcome text = `VAR Hour = HOUR(NOW())
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
  - Show filter =

      `-- Agents
      IF(
          ISFILTERED('Call Center'[Agent]),
          VAR Agents = VALUES('Call Center'[Agent])
          VAR Agentscombined = CONCATENATEX(Agents, 'Call Center'[Agent], UNICHAR(10))
          RETURN Agentscombined & UNICHAR(10)
      )&
      --Topics
      IF(
          ISFILTERED('Call Center'[Topic]),
          VAR Topics = VALUES('Call Center'[Topic])
          VAR Topicscombined = CONCATENATEX(Topics, 'Call Center'[Topic], UNICHAR(10))
          RETURN Topicscombined & UNICHAR(10)
      )`

  - Show header filter =

      `-- Header of agent
      IF( 
          ISFILTERED('Call Center'[Agent]),
          "Agent: " & REPT(UNICHAR(10), COUNTROWS(VALUES('Call Center'[Agent])))
      ) &
      -- Header of agent
      IF( 
          ISFILTERED('Call Center'[Topic]),
          "Topic: " & REPT(UNICHAR(10), COUNTROWS(VALUES('Call Center'[Topic])))
      )`

### Format using

**Font:** SF Pro Display

**Color:** Datacamp palette


# Analysis and Insights
The purpose of this dashboard is to serve as self-exploratory for managers, but I still note some highlighted points that I recognize below:

********************About Call trends:********************

- Customers tend to call more between 5:00 pm - 5:30 pm at 250 calls received with an abandoned rate is 18.40% (approximately to the average abandoned rate) and distributed mainly in the middle of the month
- The highest abandoned rate is 28.03% between 1:00 pm - 1:30 pm
- Customers have more problems with Streaming service
- The resolved rate is at a high rate (89,94%)

********************About performance of agents:********************

- The agent who satisfies customers most is Becky with a 12.02% of “Very good” rating
- The agent who has the highest resolved rate is Jim and he is effective with solving problems related to “Contract related” and “Admin Support”

********************About customer satisfaction:********************

- The average customer satisfaction is at an acceptable rate with 3.40, mainly comes from “Average” (30.04%) and “Good” (29.11%) rating
- The correlation between call answered and call resolved is strongly positive which resulted in a increase in the customer satisfaction rate

# Shareable Link
You can interact and have fun with the dashboard here:

[Microsoft PowerBI](https://app.powerbi.com/view?r=eyJrIjoiZmNiNWNiZGMtZTM4MS00ZDI3LTlhNTUtODMwOTZmZDExOGI5IiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9) | [novyPro](https://www.novypro.com/project/baokhanhdinhtr)

### Huge thanks to you for joining this creative journey with me.  Hope you all are doing great! :pray::pray::pray::relaxed:


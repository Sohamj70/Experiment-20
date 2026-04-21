# **Experiment No. 20 — Project Analysis: COVID-19 Data Analysis**

## **Introduction**
The COVID-19 pandemic resulted in millions of confirmed cases and deaths globally, making data analysis critical for tracking spread and informing policy. This project applies a complete data science pipeline — ingestion, preprocessing, feature engineering, aggregation, and geospatial visualization — to analyze global case distribution, country-wise impact, time-series trends, and India's state-level statistics.

## **Theory**
Data analysis of real-world datasets involves multiple stages to extract meaningful insights. The first step is data loading and preprocessing, where the dataset is cleaned by removing unnecessary columns and converting data types for proper analysis. Feature engineering is then applied to derive new useful attributes such as active cases, which represent the current number of infected individuals.
After preprocessing, data aggregation techniques like grouping and filtering are used to analyze information at different levels such as country-wise and state-wise statistics. Time-series analysis helps in understanding trends over time by grouping data based on dates. Visualization techniques like choropleth maps are used to represent geographical distribution of cases, making it easier to compare regions visually.
Overall, these steps form a complete data analysis pipeline that transforms raw data into structured insights, helping in better understanding and decision-making.
###### 1. Data Loading and Preprocessing
- Dataset loaded using pd.read_csv()
- Unnecessary columns removed using data.drop()
- Date column converted using astype('datetime64[ns]')
- Numerical columns converted using astype('int64')
###### 2. Feature Engineering — Active Cases
- Active cases calculated using:
- data['Active'] = data['Confirmed'] - data['Recovered'] - data['Deaths']
- Represents real-time infected cases
###### 3. Latest Date Snapshot
- Latest date extracted using data['ObservationDate'].max()
- Data filtered using boolean indexing:
- data[data['ObservationDate'] == data['ObservationDate'].max()]
###### 4. Country-Level Aggregation
- Data grouped using groupby('Country/Region').sum()
- Index reset using .reset_index()
- Specific country filtered using:
- data[data['Country/Region'] == "India"]
###### 5. Choropleth Map — Global Visualization
- Map created using px.choropleth()
- Locations mapped using country names
- Color scale adjusted using parameters like range_color
###### 6. Time-Series Aggregation
- Data grouped by date using:
- data.groupby('ObservationDate').sum().reset_index()
- Provides trend over time
###### 7. Top 20 Most Affected Countries
- Data sorted using:
- data.sort_values(by='Confirmed', ascending=False)
- Top records selected using .head(20)
###### 8. India State-Level Analysis
- India data filtered using:
- data[data['Country/Region'] == "India"]
- Missing values handled using .fillna("Unknown")
- State-wise grouping using groupby('Province/State').sum()
## **Conclusion**
- A complete data analysis pipeline was applied to real-world COVID-19 data
- Data preprocessing and feature engineering improved analysis quality
- Aggregation helped identify trends and comparisons
- Visualization highlighted global and regional patterns
- Multi-level analysis enabled insights from global to state level

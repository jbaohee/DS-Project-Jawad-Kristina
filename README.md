# Anomalies in Paris From Dans-Ma Rue Dataset

## Introduction of Dataset
Dans-Ma Rue is a free to use applcation for reporting urban anomalies in Paris. By anomalies, it is meant that various type of irregularities that does not comply with the urban and municipal rules. This dataset is collected from kaggle. We have collected data from the year of 2012 until 2022. We have omitted the data for 2023 because they year has not ended yet and the dataset for this particular year is not fully created yet. This dataset has 17 features and most of them are categorical. To answer our research question, we also used to other complimentary dataset that gave use the data on touristic sites in Paris and also the social housing in Paris. We collected both of those dataset from opendata.paris.fr <br>

Issues with the dataset:

- The dataset is very big and they are divided year-wise
- Even after cleaning, the CSV file was too big to show on kepler.gl website as each time we tried, the website crashed
- Data is overall clean but there are discrepencies across the datasets (i.e. Non-uniform feature name, data-type and ordering)
- A CSV file had different encoding 
- Some decimal values were comma-seperated. But for visualization, they needed to be dot seperated

## Research Questions
After looking at the data, we came up with questions:

1. Is there a particular time window during the year where most of the anomalies are reported?
2. Which areas of Paris are most affected by anomalies/ vandalisms? What type are they?
3. Do tourists and social housing influence the accurance of anomalies? How?
4. Can we make a predictive algorithm which may answer which areas might be more susceptible to a particular anomaly? 

## Data Cleaning
- First we dropped the features that were redundant (The features which could be extracted from other features)
- Then we renamed the column names and rearranged ordering to remove discrepency 
- We concatenated all the dataframes into a single one after confirming they had same column name and order
- Converted the 'CODE_POSTAL', 'ARR' and 'NUMERO' column to string so that we can replace the commas with dots using a user defined function
- Then converteed the 'CODE_POSTAL', 'ARR', 'NUMERO', 'X' and 'Y' column to float as an intermediate step to avoid parsing error
- Finally converting the 'CODE_POSTAL', 'ARR' and 'NUMERO' column back to int 'X' and 'Y' columns are kept as float because they are coordinates 
- Renamed the 'X' and 'Y' columns to 'LONGITUDE' and 'LATITUDE' for kepler.gl website for spatial visualization


## Data Visualization
Since this dataset mostly provides us with spatial data, we tried to visualize the data on kepler.gl. Unfortunately, because of the huge size of the dataset, we were unable to do so. So then we mostly focused on statistics of the data to reach a conclusion. We have done the following data visualizations:
1. A bar plot to visualize what type of anomalies are most common ones. 
2. A 3D bar plot to visalize which type of anomalies are prevalent in which districts of Paris but that turned out to be a bad visualization
3. A stacked bar plot of number of Anomalies vs Year to see the growth/reduction in reported anomalies
4. A violin plot to see what type of Anomalies are most common in each district, it provided us a better visualization than the 3D bar plot
5. Year-wise bar plots of total reported anomalies vs month to uncover any trend between the number of reports and time of the year

Apart from these visualization, in the notebook, we have also done some intermediate visualization for better understanding the data. <br>

After visualizing the data, we applied some statistical analysis for answering our research question

## Statistics
We have done the following statistical analysis to support/refute our research questions
- A correlation heat-map across various features
- Boxplot of anomalies reported month-wise for any particular year
- Correlation heat-map between Dans-Ma Rue, Touristics Area and Social Housing 

Then we have reached some conclusions about our project after the visualizations and statistics.

## Conclusions
1. From the month-wise boxplot, we concluded that most of the anomalies occur during summer which is the peak tourism time in Paris
2. Reports have grown exponentially each year with a dip in the year 2020. We speculate the dip happened because of the Covid-19 lockdown
3. The 10th, 11th, 12th, 15th, 17th and 20th Arrondissements are more prone to anomalies than all other districts combined
4. Most common type of anomalies are graffitis, abandoned objects, abandoned properties and public space violation 
5. Touristic attraction areas and social housing has an effect on reported anomalies 

## Faced problems in this project

- We could not use geopandas library due to lack of experience
- The kepler.gl website crashed when we tried to visualize the spatial data
- Due to the nature of the dataset (mostly categorical data) it was hard to find insight
- We had to resort to two other datasets for supporting our research questions
- For some visualizations, we had to learn the theories from scratch

## Future work
We want to build a predictive model that will take two inputs, the Code Postal and Time of the year (Month). Then the model will give a breakdown of probabilies of each type of anomalie occuring in that particular district. But building the model is proving to be very tough. 

## Presentation
Please refer to the report to see the brief presentation

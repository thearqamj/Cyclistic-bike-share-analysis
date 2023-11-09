![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/897f3bda-9001-4f94-8dd7-a39ee93c0ad2)![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/9080f5d0-5a59-4930-8202-e020561a0819)## Cyclistic-bike-share-analysis
This project delves into the operational data of Cyclistic, a bike-share company, to uncover valuable insights and drive strategic decision-making. By applying the data analysis process, the project identifies user patterns, optimizes station utilization, and enhances overall efficiency.


## Background

A bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to work each day.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno (the director of marketing and my manager) believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.


## Scenerio

As a junior data analyst at Cyclistic, I am tasked with understanding the usage patterns of casual riders and annual members to develop a marketing strategy that converts more casual riders into annual members. I will analyze Cyclistic's historical bike trip data to identify trends, patterns, and insights that will inform my recommendations. I will also create compelling data visualizations to present my findings to Cyclistic executives.


## This Data Analysis Project will be completed in 06 phases of data analysis:
1. ASK
2. PREPARE
3. PROCESS
4. ANALYZE
5. SHARE
6. ACT

## STEP: 01 ASK

Three main question that needs to be answered are:
1. How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclistic use digital media to influence casual riders to become members?


### Business Task:
Devise marketing strategies to convert casual riders to annual members.

Here the key stakeholders are director of marketing and the consumers.



## STEP 02: PREPARE

Now that the task is clear its time to prepare the data for analysis.

### Data Source:
I will use Cyclistic’s historical trip data to analyze and identify trends from Jan 2022 to Dec 2022. This is public data that can be used to explore how different customer types are using Cyclistic bikes. But note that data-privacy issues prohibit from using riders’ personally identifiable information. This means that we won’t be able to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes.

### Data Organization
There are 12 files with naming convention of YYYYMM-divvy-tripdata and each file includes information for one month, such as the ride id, bike type, start time, end time, start station, end station, start location, end location, and whether the rider is a member or not. The corresponding column names are ride_id, rideable_type, started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng and member_casual.


## STEP 03: PROCESS

This is the most crucial step of data analysis. Here I combined the data using MYSQL because the amount of data is huge and excel cannot handle such data.


### Merging Data Sets

SQL Query: [Data Processing](https://github.com/thearqamj/Cyclistic-bike-share-analysis/blob/main/Data%20Processing)
12 csv files are uploaded as tables in the dataset '2022_tripdata'. Another table named "combined_data" is created, containing 5,667,717 rows of data for the entire year.


### Data Explorations

Before proceeding to the Data Cleaning step, it is necessary to explore the data, become familiar with its content, and identify any inconsistencies.

#### Observations:

1. The table below shows the all column names and their data types. The ride_id column is our primary key.

![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/102df164-b3b8-415a-9064-096b4d1aaac0)

2. The following table shows number of null values in each column.
   
![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/722d2646-4a22-4253-b544-8b5befcfb5a6)

3. As ride_id has no null values, let's use it to check for duplicates.

![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/36c66089-df36-468e-97c3-98a202ce77e8)

4. All ride_id values have length of 16 so no need to clean it.

5. There are 3 unique types of bikes(rideable_type) in our data.

![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/d4005095-77ff-4675-8ee2-c7cdef121150)

6. The started_at and ended_at shows start and end time of the trip in YYYY-MM-DD hh:mm:ss UTC format. New column ride_length can be created to find the total trip duration. There are 5360 trips which has duration longer than a day and 122283 trips having less than a minute duration or having end time earlier than start time so need to remove them. Other columns day_of_week and month can also be helpful in analysis of trips at different times in a year.

7. Total of 833064 rows have both start_station_name and start_station_id missing which needs to be removed.

8. Total of 892742 rows have both end_station_name and end_station_id missing which needs to be removed.

9. Total of 5858 rows have both end_lat and end_lng missing which needs to be removed.

10. Member_casual column has 2 uniqued values as member or casual rider.

![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/0ce57a9d-2ad7-43c8-b945-1cfdefa74bbc)

11. Columns that need to be removed are start_station_id and end_station_id as they do not add value to analysis of our current problem. Longitude and latitude location columns may not be used in analysis but can be used to visualise a map.

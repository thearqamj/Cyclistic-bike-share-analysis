## Cyclistic-bike-share-analysis
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

Three questions will guide the future marketing program:

How do annual members and casual riders use Cyclistic bikes differently?
Why would casual riders buy Cyclistic annual memberships?
How can Cyclistic use digital media to influence casual riders to become members?
Moreno has assigned me the first question to answer: How do annual members and casual riders use Cyclistic bikes differently?

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

## Data Cleaning

SQL Query: [Data Cleaning](https://github.com/thearqamj/Cyclistic-bike-share-analysis/blob/main/Data%20Cleaning)

1. All the rows having missing values are deleted.
2. 3 more columns ride_length for duration of the trip, day_of_week and month are added.
3. Trips with duration less than a minute and longer than a day are excluded.
4. Total 1,375,912 rows are removed in this step.

## STEP 04: ANALYZE
SQL Query: [Data Analysis](https://github.com/thearqamj/Cyclistic-bike-share-analysis/new/main)


The data is stored appropriately and is now prepared for analysis. I queried multiple relevant tables for the analysis and visualized them in Tableau.
The analysis question is: How do annual members and casual riders use Cyclistic bikes differently?

First of all, member and casual riders are compared by the type of bikes they are using.


![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/9aa44fde-6d36-42c7-bccd-55dedf1a1ab9)

The members make 59.7% of the total while remaining 40.3% constitutes casual riders. Each bike type chart shows percentage from the total. Most used bike is classic bike followed by the electric bike. Docked bikes are used the least by only casual riders.

Next the number of trips distributed by the months, days of the week and hours of the day are examined.

![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/bfdd6135-20cb-49a8-827d-c1727616817c)

![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/8fb840f9-4632-470d-9ff4-06af79984b73)


Months: When it comes to monthly trips, both casual and members exhibit comparable behavior, with more trips in the spring and summer and fewer in the winter. The gap between casuals and members is closest in the month of july in summmer.
Days of Week: When the days of the week are compared, it is discovered that casual riders make more journeys on the weekends while members show a decline over the weekend in contrast to the other days of the week.
Hours of the Day: The members shows 2 peaks throughout the day in terms of number of trips. One is early in the morning at around 6 am to 8 am and other is in the evening at around 4 pm to 8 pm while number of trips for casual riders increase consistently over the day till evening and then decrease afterwards.

We can infer from the previous observations that member may be using bikes for commuting to and from the work in the week days while casual riders are using bikes throughout the day, more frequently over the weekends for leisure purposes. Both are most active in summer and spring.

Ride duration of the trips are compared to find the differences in the behavior of casual and member riders.

![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/0c8a3a13-b0b8-4119-b5f3-97fdfa4a98e1)


![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/fdfd9dc9-124d-4261-aadd-48c02d70ab76)

Take note that casual riders tend to cycle longer than members do on average. The length of the average journey for members doesn't change throughout the year, week, or day. However, there are variations in how long casual riders cycle. In the spring and summer, on weekends, and from 10 am to 2 pm during the day, they travel greater distances. Between five and eight in the morning, they have brief trips.

These findings lead to the conclusion that casual commuters travel longer (approximately 2x more) but less frequently than members. They make longer journeys on weekends and during the day outside of commuting hours and in spring and summer season, so they might be doing so for recreation purposes.

To further understand the differences in casual and member riders, locations of starting and ending stations can be analysed. Stations with the most trips are considered using filters to draw out the following conclusions.

![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/97d8d224-261b-4f12-9977-beba6c81e32f)

Casual riders have frequently started their trips from the stations in vicinity of museums, parks, beach, harbor points and aquarium while members have begun their journeys from stations close to universities, residential areas, restaurants, hospitals, grocery stores, theatre, schools, banks, factories, train stations, parks and plazas.

![image](https://github.com/thearqamj/Cyclistic-bike-share-analysis/assets/135017364/3a2dc69f-2c40-4955-8532-57ba17d36037)

Similar trend can be observed in ending station locations. Casual riders end their journay near parks, museums and other recreational sites whereas members end their trips close to universities, residential and commmercial areas. So this proves that casual riders use bikes for leisure activities while members extensively rely on them for daily commute.

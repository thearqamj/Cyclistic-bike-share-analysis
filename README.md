# Cyclistic-bike-share-analysis
This project delves into the operational data of Cyclistic, a bike-share company, to uncover valuable insights and drive strategic decision-making. By applying the data analysis process, the project identifies user patterns, optimizes station utilization, and enhances overall efficiency.


# Background

A bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to work each day.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno (the director of marketing and my manager) believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.


# Scenerio

As a junior data analyst at Cyclistic, I am tasked with understanding the usage patterns of casual riders and annual members to develop a marketing strategy that converts more casual riders into annual members. I will analyze Cyclistic's historical bike trip data to identify trends, patterns, and insights that will inform my recommendations. I will also create compelling data visualizations to present my findings to Cyclistic executives.


# This Data Analysis Project will be completed in 06 phases of data analysis:
1. ASK
2. PREPARE
3. PROCESS
4. ANALYZE
5. SHARE
6. ACT

# STEP: 01 ASK

Three main question that needs to be answered are:
1. How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclistic use digital media to influence casual riders to become members?


## Business Task:
Devise marketing strategies to convert casual riders to annual members.

Here the key stakeholders are director of marketing and the consumers.



# STEP 02: PREPARE

Now that the task is clear its time to prepare the data for analysis.

## Data Source:
I will use Cyclistic’s historical trip data to analyze and identify trends from Jan 2022 to Dec 2022. This is public data that can be used to explore how different customer types are using Cyclistic bikes. But note that data-privacy issues prohibit from using riders’ personally identifiable information. This means that we won’t be able to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes.

## Data Organization
There are 12 files with naming convention of YYYYMM-divvy-tripdata and each file includes information for one month, such as the ride id, bike type, start time, end time, start station, end station, start location, end location, and whether the rider is a member or not. The corresponding column names are ride_id, rideable_type, started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng and member_casual.

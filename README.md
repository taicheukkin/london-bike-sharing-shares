# london-bike-sharing-shares
The operational dashboard help business make sense of the relationship between weather and sport, in order to allocate resource in specified weather condition or time to optimize the revenue effectively. In detail, how the time and weather in determining the bike sharing shares between 2015 and 2017 was analyzed by Powerbi

# About data source
the data was downloaded from kaggle
https://www.kaggle.com/datasets/hmavrodiev/london-bike-sharing-dataset

# data cleaning 

Step 1 :Load data from csv file into Power BI Desktop, and Open power query editor & in view tab under Data preview section

- check "column distribution", "column quality" & "column profile" options.
- It was observed that in none of the columns errors & empty values were present

step 2: change the column name 
- from T1 and T2 to actual temperature and perceived temperature respectively.

step 3：Check the data type of each column

# Data Transformation 
Step 1: replace integer as text in column   
- replace 0 and 1 in column（is holiday , is _weekend) as 'no' and 'Yes' respectively
- replace 1,2,3,4 in season as "spring","summer","autumn" and“winter" respectively

step2 :Create new column called weather to indicate meaning of weather code column.

- Dax function was written to create new column

![image](https://github.com/user-attachments/assets/ee7376d8-e857-49d6-920b-1f05cef45e55)

step 3:
Create new column to categorize "cloudy","few clouds","clear","Broken Clouds" as Good weather as well as "Light rain,snowball,rain with thunderstorm as bad weather


step 4:
- create new column called Time to present time as 24 hours clock, and time number was created for ranking the time column 

- Dax function was written to create new column

![image](https://github.com/user-attachments/assets/bf83c88c-7445-4878-bb5a-52dfda157fd6)

Step 5:
- Create group for actual temperature(10 bins),perceived temperature（10 bins） wind speed(10 bins) 

step 6:
Create table "calendar" for representing Date in terms of year,month,quarter,_weekday/_weekend and day.

- Dax function is written to create new  column

![image](https://github.com/user-attachments/assets/40663ab2-644b-459e-b1d8-388be04afa26)

- On the model view, create many and one Relationship between timestamp column (date/time format)in london_bike_sharing table and date column in calandar table. 



step 7:Create table "measure"   
- create measure for calculating average,total,sum,standard deviation and range of london_bike_sharing_shares

- create measure for calculating average,total,sum of column(wind_speed,actual_temperature and percieved temperature）

-Create measure for showing the difference between actual_temperature and percieved temperature

![image](https://github.com/user-attachments/assets/c03bb01e-cc10-469e-b0ad-04ca7d0679e9)



Step 8：calculate the daily and monthly moving average in table for analyzing and forcasting trend of london_bike_sharing_shares.

- create month and selectedmonths for skateholders to select the number of monthly moving average 

Dax function creating  month and selectedmonths is written below

![image](https://github.com/user-attachments/assets/a277d6ba-5b39-4f32-beb1-9b81482421c2)

![image7](https://github.com/user-attachments/assets/07ff60f5-fe77-4f57-862d-ff0ab7622f05)


- Create two measure for calculating and checking monthly moving average of london_bike_sharing_shares

![image](https://github.com/user-attachments/assets/15488b85-64c5-4062-b17f-73e0f17a7181)

![image](https://github.com/user-attachments/assets/62bfa239-e98d-4a55-8ee7-e4bb9c205879)

- Repeating the same step as monthly moving average for creating daily moving average of london_bike_sharing_shares

Dax function for creating daily moving average is written below

 -![image](https://github.com/user-attachments/assets/fc678c02-9215-40e0-91f1-55a790a6df3e)

 -![image](https://github.com/user-attachments/assets/a4420431-0eb7-4fa8-b3b5-cdf38acb26e3)

 -![image](https://github.com/user-attachments/assets/3b66006a-a01b-42ba-b1d7-0fe79023c8c7)

 -![image](https://github.com/user-attachments/assets/7e3e651f-4e33-4d9c-8f09-64336f123577)


step 9 calculate correlation
- correlation between actual_temperature and monthly moving average london_bike_sharing_shares is calculated over 24 months in 2 years ,
the dax function is written below

![image](https://github.com/user-attachments/assets/64bb9272-6bcf-42e6-81cf-571d142edd23)

![image](https://github.com/user-attachments/assets/70a43b9f-949b-49b5-9533-e83f51a65ea9)


- correlation between wind_speed(10 bins) and average of london_bike_sharing_shares is calculated over daytime,
- the dax function is written below

![image](https://github.com/user-attachments/assets/1eabbd37-25b0-40b5-b167-90889fb592a8)

![image](https://github.com/user-attachments/assets/bdaf21a0-8ee1-4775-a724-4662c4ac4709)

- correlation between actual_temperature(10 bins) and average of london_bike_sharing_shares is calculated over daytime,
- the dax function is written below

![image](https://github.com/user-attachments/assets/cf7cab40-3cf9-47eb-ba42-d1bfa13362ad)

![image](https://github.com/user-attachments/assets/6866d6a8-290e-438a-9d39-a1f5c5a5b881)



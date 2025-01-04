# london-bike-sharing-shares
The operational dashboard help business make sense of the relationship between weather and sport, in order to allocate resource in specified weather condition or time to optimize the revenue effectively. In detail, how the time and weather in determining the bike sharing shares between 2015 and 2017 was analyzed by Powerbi

# About data source
the data was downloaded from kaggle
https://www.kaggle.com/datasets/hmavrodiev/london-bike-sharing-dataset

# Cleaning and Transformation step

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
- correlation between actual_temperature and monthly moving average london_bike_sharing_shares is calculated over 24 months in 2 years.
- correlation between wind_speed(10 bins) and average of london_bike_sharing_shares is calculated over daytime,
  
- correlation between actual_temperature(10 bins) and average of london_bike_sharing_shares is calculated over daytime,
- the example of dax function is written below

![image](https://github.com/user-attachments/assets/cf7cab40-3cf9-47eb-ba42-d1bfa13362ad)

![image](https://github.com/user-attachments/assets/6866d6a8-290e-438a-9d39-a1f5c5a5b881)

# Data visualization

# Dashboard1:seasonal trend of london_bike_sharing_shares

![image](https://github.com/user-attachments/assets/f58c6dc6-a8ae-4c2a-8650-7894a4d56f91)

Monthly moving average of london bike sharing shares has calculated for smoothing and analyzing the trend  

figure 1.1

![image](https://github.com/user-attachments/assets/94960591-27ec-47fc-b250-60d0c386eaee)

The Monthly moving average slicer allows users to choose number of monthly moving average to identify monthly,seasonal or half-year trend was existed in the london_bike_sharing_shares.The default value is 4 monthly moving average


The Season slicer allows user to identify which 3 months is corresponding to season

figure 1.2
![image](https://github.com/user-attachments/assets/1bbc85fc-fbf1-42a3-94c0-5688349d530e)

the table provide detailed date information(year/MonthNameShort) and monthly moving average,allow users check the monthly_moving_average. 

the 3 monthly_moving_average was choosen
,because the data is more smoothing as compared to 2 monthly_moving_average, and sensitive to the seasonal trend as compared to 4 monthly_moving_average.

Implication
The seasonal peak of monthly_moving_average in August is the average of June,July and August (the three months represent summer).It implied the more bike should be prepared for these three months.


# Dashboard2: weekend and holiday

![image](https://github.com/user-attachments/assets/e601a999-a7ff-45a7-bb69-e4f39b8f7940)


figure 2.1

![image](https://github.com/user-attachments/assets/96507ce8-f674-40cf-ba51-0938efd26dbc)

Month slicer aims to show daily moving average each month. day slicers adjust the
the number of daily moving average.the default is 2

figure 2.2

![image](https://github.com/user-attachments/assets/adab6411-41dc-459d-a28a-f39c87b18cd7)

figure 2.3

![image](https://github.com/user-attachments/assets/26f82967-2219-41a7-b7e6-bd3fb6b4f199)

figure 2.4

![image](https://github.com/user-attachments/assets/ad9d9afe-aeb9-49ac-b48b-70c59de69bda)

figure 2.5

![image](https://github.com/user-attachments/assets/44c67f7a-ff01-437f-bcd4-b080d3562fe0)

The bar chart showed the daytime trend of average bike sharing share.Overall,8am, 5am,6am are top 3 daytime in terms of  average bike sharing shares in figure3.2.The trend were similar when it was weekend in figure 3.3. In contrast,In figure 3.4 and 3.5, the rise and fall trend was observed between 7 am
and 11:00 pm, the average london_bike_sharing_shares increased gradual at 7am ,leveled off 12 pm,followed by gradual decrease from 2pm to 11pm.



figure 2.7

![image](https://github.com/user-attachments/assets/3dd0a0d3-ddf2-422c-8c47-e0d90aec6e36)

Overall,the x_axis and y_axis of bar chart is the date at the daily level and daily_moving_average respectively.The green and blue color bar represent the calculation of daily moving average involving weekend or non-weekend respectively.By adjusting day slicers, it is found that typically 5 blue bar chart with smaller daily_moving_average followed by green bar chart with higher daily_moving_average in 2_day moving average. It is implied There were association between seasonal trend between weekday and weekend.


Although the most month follow seasonal trend, Juanary and December were the exception.

figure 2.7

![image](https://github.com/user-attachments/assets/9cfbd192-0e67-4b1d-b5a7-efd7bc983deb)

figure 2.8

![image](https://github.com/user-attachments/assets/5da6e750-a2fc-45e0-bbdc-d38235e822eb)

figure 2.9

![image](https://github.com/user-attachments/assets/b6ce3b93-7b9f-4af1-97ee-60eb5467961d)

In figure 1,in 26th December,2016,the 2-day monthly_moving_average involving non_weekend was higher than weekend. The trend was not discovered in 2015 in figure 2. By adjusting is_holiday and is_weekend slicer to Yes and daily_moving_average to 1, it is discovered that 26th December,2016 is holiday in figure 3,but not weekend. It means holiday(26th December,2016) contributed the largest proportion to non_weekend when calculating daily_moving_average. 

figure 2.10

![image](https://github.com/user-attachments/assets/423f243b-e9cd-430d-a2b2-769df8a03aed)

figure 2.11

![image](https://github.com/user-attachments/assets/bed4d33d-b225-4bf6-8254-07a9550e8343)
same logic applied 1st and 2nd Juanary 2016 and 2017,the 2-day monthly_moving_average involving non_weekend was higher than weekend in 2016,By adjusting is_holiday and is_weekend slicer to Yes and daily_moving_average to 1 again,it is discovered that 1st and 2nd Juanary 2016 was holiday in figure 3,but not weekend.
Therefore the proportion of moving average of holiday was considered as non_weekend. In contrast,the 2-day monthly_moving_average involving non_weekend is drastically lower than weekend in 2016.The possible explanaiton was 1st and 2nd Juanary 2017 was holiday in essence,but since it was weekend as well is not applicable to the definition of holiday and non_weekend, but weekend. 

Implication

1.)In the daily level,more bike should be allocated to weekend and holiday,Specifically 1st Juanary (new_year_holiday) or the day near 26th December(Christmas).

2.)In daytime level,more bike should be allocated to 8pm,5/6pm when the day is weekday. The allocation of bike should be increased from 9pm to 1:00 pm, and decreased afterward when the day is weekend or holiday.


# dashboard 3: weather

![image](https://github.com/user-attachments/assets/b68dc90c-44c0-4495-bd53-9d3ba964d92c)

the dashboard aims to investiigate the relationship between weather and london_bike_sharing_shares.

figure  3.1

![image](https://github.com/user-attachments/assets/11882135-471b-43d3-8709-0b3594be2be6)
The donut chart measure the percentage of london_bike_sharing_shares shared in various weather condition
In the first layer of donut chart,the majority of weather was good weather(92%),rather than bad weather(8%). In the second layer,the good and bad weather was broken 4 and 2 weather respectively.The "clear"(36%),"few clouds"(30%) and "broken clouds"(21%)  were evenly distributed, except"cloudy"(5%). Regarding bad weather, majority of bike shares was accounted by "light rain"(9%).However,both percentage of "snowball" and rain with thunderstorm is less than 1%.

figure 3.2

![image](https://github.com/user-attachments/assets/da2269b5-813f-4611-b4b5-50f6cb65af67)

The bar chart showed average number of london_bike_sharing shares in various weather condition. Blue bar(good weather)show higher average number of london_bike_sharing shares as comapred to green bar(bad weather).


figure 3.3 overall monthly trend of good and bad weather

![image](https://github.com/user-attachments/assets/3cafd67d-23e5-4be1-b237-fad217ffe8e3)

 figure 3.4 monthly trend of clear weather 

![image](https://github.com/user-attachments/assets/27ab1481-8182-4ad6-88e0-8c0a0d8267f0)


The line graph in figure 4.3 depict the monthly seasonal trend of good weather (the gradual increase was observed in April and peaked at July, August and September) in terms of 3 monthly moving average,which was higher than bad weather thoughtout the 12 months. The bad weather did not show seasonal trend. Similarliy, In figure 4.4,the 3 monthly moving average of clear weather followed the same seasonal trend. It is noted that the monthly moving average of clear weather ranging from 1k to 8k occupied the majority of good weather ranging from 4k to 10k. Therefore, the rest of good weather only comprised the minority of good weather. 



Implication
more bike should be allocated in the good weather, Specifically clear weather in summer(June,July August). In contrast,less bike should be allocated in the bad weather,particular light rain.


# dashboard 4 temperature

![image](https://github.com/user-attachments/assets/3f5b850d-62f0-40c9-badc-09b4acc49621)

aims to investigate the association between temperature and london_bike_sharing_shares.

figure 4.1

![image](https://github.com/user-attachments/assets/6e4222c5-b9fe-46a7-952f-1bee054964e1)

The strongly positive correlation(0.73) is observed  between actual temperature with 1 monthly moving average of bike sharing shares over 24 months other than other monthly moving average. Specifically, seasonal trend of actual actual_temperature was almost overlapped with monthly moving average of bike sharing share in the line graph.


figure 4.2

The average,mean and frequency of actual_temperature (10 bins）

![image](https://github.com/user-attachments/assets/52b5581e-4169-48b0-b826-9585b3831c54)


It is found that the higher the average bike sharing, the larger the actual temperature group. However,actual temperature (bins)(8.80-12.39) contributed the highest frequency, but actual temperature (bins)(16.00-19.59) contributed the largest bike sharing shares among other groups thoughtout 2 years.


figure 4.3

![image](https://github.com/user-attachments/assets/0624dbb2-0d4c-4806-afd0-5b0696b70da7)

The pie chart show distribution of total bike sharing shares in percieved_temperature difference（actual temperature-percieved temperature). 0 temperature difference (green legend(71.45&))demonstrated it comprised majority of total bike sharing shares among others.

In view of this, the column "optimal temperature"(0 temperature difference) and measure "Count of optimal temperature was created for investigate the trend of optimal temperature. The dax function is written below.

figure 4.4

![image](https://github.com/user-attachments/assets/b6bf92d3-1a1d-4745-81e7-f7fde49cc6e3)

figure 4.5

![image](https://github.com/user-attachments/assets/54098b11-ff5d-46bf-87eb-618fd2bb5d44)

figure 4.6

![image](https://github.com/user-attachments/assets/cd7f9277-3617-4138-a0d0-8e6b745c43d7)

By adjusting optimal temperature to "yes", the correlation coefficient is increased from 0.73 to 0.99. The positive association between monthly_moving_average of london_bike_sharing_shares and actual_temperature is stronger.


figure 4.7

The average,mean and frequency of actual_temperature (10 bins）

![image](https://github.com/user-attachments/assets/52b5581e-4169-48b0-b826-9585b3831c54)

                 
figure 4.8         

average,mean and frequency of actual_temperature (10 bins） if adjusting optimal temperature slicers to "yes"

![image](https://github.com/user-attachments/assets/14346533-f88a-40f1-b233-949e0da999e5)

The largest contribution of bike sharing shares has shifted from actual temperature ctual temperature (bins)(16.00-19.59) in figure 4.7 to (12.40-15.99 and 16.00-19.59)
in figure 4.8



figure 4.9

percieved temperature difference by bike sharing shares in fall

![image](https://github.com/user-attachments/assets/312fb411-499f-4811-87ed-db71a6d32ba9)


figure 4.10

percieved temperature difference by bike sharing shares in spring

![image](https://github.com/user-attachments/assets/194a2e0a-9ee7-43b4-ad9f-55326df08cc6)


figure 4.11

percieved temperature difference by bike sharing shares in summer

![image](https://github.com/user-attachments/assets/f01d39d5-9851-433b-903d-a8be951842f1)

figure 4.12

percieved temperature difference by bike sharing shares in winter

![image](https://github.com/user-attachments/assets/a3b15095-5f6f-4272-a58e-427e8d3f4819)

By adjusting season slicers,it is found that the majority of percieved temperature difference is  0 (optimal temperature) in summer(91.89%),spring(62.6%),fall(81.53%),but not winter(32.26%)


Implication

optimal temperature may implied customers has watched weather forcasting in advance.It provide possible explanaiton for why there has been strong positive correlation between average_bike_sharing_shares and average temperature. The customers who have watched weather forcasting contribute the largest proportion of bike_sharing shares indicating large Customers base in spring,fall and particularly summer.Therefore, the strength of correlation between monthly average of bike_sharing_shares and average of actual_temperature  is stronger when the optimal temperature slicers is adjusted to "yes". Specifically, they prefered lending the bike when temperature range from 12.40-19.59. 

suggestion

1.Apart from the seasonal trend, The bike should be allocated according to trend of actual_temperature.

2.More bike should be allocated when actual temperature ranging from 12.40-19.59 
 
3. It is found lower total bike_sharing_shares, higher average_bike_sharing_shares. It implied  the presence of small group of customers lent the largest quantity of bike,showing strong customer loyalty. It is important to stay contact and allocate more bike for them.

# Dashboard 5： wind speed and actual temperature

![image](https://github.com/user-attachments/assets/028c2738-2bec-424e-bd61-825eb4129c06)

The Dashboard aims to discover the association between wind speed /actual temperature and bike_sharing_shares over the daytime

figure 5.1

![image](https://github.com/user-attachments/assets/d9152b31-5a1c-4c38-b658-1c1f7d39d432)
Both orange and blue color card showed very strong positve correlation between wind  speed/actual temperature and london_bike_sharing over daytime respectively when is_weekend slicers is applied.The combo chart demonstrated both wind  _speed and temperature follow the similar seasonal trend as london_bike_sharing. Specifically, moderate increase is observed from 8am ,and leveled off at 12pm, followed by moderate decrease at 4pm.It is noted that
top 5 average bike bike_sharing_shares was between 12pm to 5pm

figure 5.2

![image](https://github.com/user-attachments/assets/2e7f95da-4e05-4443-8d18-44c7f9db5571)

In figure 6.2, no slicers were applied. It was found that the top 3 largest average bike sharing shares was wind speed bin (5.65-11.29)(11.30-16.94)(16.95-22.59) as a result of the largest totla bike sharing shares.


figure 5.3

![image](https://github.com/user-attachments/assets/053eb4cc-fbc1-4336-9c8a-549475d29394)

figure 5.4

![image](https://github.com/user-attachments/assets/5917b6f1-2d08-42fc-b61b-2bc08ec086cc)

figure 5.5

![image](https://github.com/user-attachments/assets/ac336aa3-8ad6-469a-8f8d-a63fe502fed4)


By applied 12pm to 5pm in the time slicers in figure 6.3,the distribution of wind speed and actual_temperature between 12pm to 5pm was investigated. 

In figure 5.4,it was found that the average bike sharing are evenly distributed and in the first five wind_speed(bins), the rest of 4 groups show relatively low average bike sharing shares.The frquency of wind_speed(16.95-22.59) was the highest among 10 groups, the majority of total bikes sharing was  distributed to wind_speed(16.95-22.59)


In figure 5.5,it was found that the higher the average bike sharing, the larger the actual temperature group.
It is expected that frequency of temperature was the highest in actual_temperature(16.00-19.59). As a result,the majority of total bikes sharing was also distributed to temperature (16.00-19.59)


Implication

Customers prefer lending the bikes between 12:00 and 5:00 in the weekend. Wind_speed and temperature also play an crucial role in determining the bike sharing shares in this golden period.

1)In General,More bike should be allocated when Wind speed range from 5.65 to 16.95.

2)More bike should be allocated when Wind speed ranging from 0 to 28.24, in the golden period.

3)More bike should be allocated when temperature ranging from 8.80 to 23.19, in this golden period.

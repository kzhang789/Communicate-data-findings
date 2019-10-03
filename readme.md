# 2018 Bay Wheels Ride Data Exploration and Visualization
## by Kailai Zhang


## Dataset

[Bay Wheels](https://en.wikipedia.org/wiki/Bay_Wheels) (previously known as Ford GoBike) is a regional public bike sharing system in the San Francisco Bay Area, California. Bay Wheels is the first regional and large-scale bicycle sharing system deployed in California and on the West Coast of the United States with nearly 500,000 rides since the launch in 2017 and had about 10,000 annual subscribers as of January 2018. The dataset used for this exploratory analysis consists of [monthly individual trip data](https://www.lyft.com/bikes/bay-wheels/system-data) from January 2018 to December 2018 in CSV format covering the greater San Francisco Bay area, also available [here](https://s3.amazonaws.com/baywheels-data/index.html).

##### Data wrangling process:
- fix multiple fields that are not in the correct dtype, i.e. `start_time`, `end_time` should be datetime type, `user_type` and `member_gender` should be categorical data type, etc
- add new columns for trip duration in minute, trip start date in yyyy-mm-dd format, trip start hour of the day, day of week and month
- add a new column calculating riders' age from 'member_birth_year'
- filter out outlier ages from visual examination of the member age distribution and statistical percentile
- cast 'member_birth_year' and 'member_age' to integer instead of float type
- cast 'start_dayofweek' to category dtype
- cast 'start_month' to category dtype for easy plotting
- filter out outlier trip records where the duration was very long


## Summary of Findings

The number of trips peaked around 8-9am and 17-18pm during a day, there were more trips on work days (Mon-Fri) compared to weekends. Summar time was the most popular season of a year, likely due to the weather. The riding trips tend to be shorter on Monday through Friday compared to weekends. It indicates a pretty stable and efficient usage of the bike sharing system on normal work days, while more casual flexible use on weekends.

Most riders were male subscribers who did not use bike share for all trips. Most members were around 25 to 40 years old, as the age gets older, bike usage dropped significantly. Though not a huge difference, male riders tend to have shorter trips compared to female users, indicated by both a smaller median and shorter IQR. Riders who rented the bikes Monday through Friday are slightly older than those who ride on weekends, which supplements the work commute usage that was observed from some of the univariable exploration plots.

There are a lot more subscriber usage than customers overall. The riding habit/pattern varies a lot between subscribers and customers. Subscribers use the bike sharing system for work commnute thus most trips were on work days (Mon-Fri) and especially during rush hours (when going to work in the morning and getting off work in the afternoon), whereas customers tend to ride for fun in the afternoon or early evenings over weekends. Subscriber usage peaks out on typical rush hours when people go to work in the morning and getting off work in the afternoon, which strengthened their usage purpose and goal of riding. Similar pattern was not observed among customers who tend to ride most in the afternoon or early evening for a different purpose than the subscribers.


## Key Insights for Presentation

Different usage pattern/habit between the two type of riders are seen from the exploration. Subscribers use the system heavily on work days i.e. Monday through Friday whereas customers ride a lot on weekends, especially in the afternoon. Many trips concentrated around 8-9am and 17-18pm on work days for subscribers, yet customers tend to use more in the late afternoon around 17pm Monday to Friday. The efficient/short period of usage for subscribers corresponds to their high concentration on rush hours Monday through Friday, indicating the use is primarily for work commute. The more relaxing and flexible pattern of customer use shows that they're taking advantage of the bike sharing system quite differently from the subscribers, heavily over weekends and in the afternoon, for city tour or leisure purpose probably.
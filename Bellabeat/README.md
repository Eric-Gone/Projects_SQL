To determine and confirm any common columns across all tables. Id is common and will be useful for later JOINs
````sql
--Finding common columns across tables
select
  column_name
  ,count(table_name)
from
  `enduring-lane-416206.bellabeat.INFORMATION_SCHEMA.COLUMNS`
group by
  1;
````
````sql
select
  table_name,
  sum(case
    when column_name="Id" then 1
    else 0
    end
    ) as has_id_column
from
  `enduring-lane-416206.bellabeat.INFORMATION_SCHEMA.COLUMNS`
group by
  1
order by
  1 asc;
````
To determine the total number of unique Ids across all tables. Total number is 35 unique users.
````sql
select
  count(distinct A.id) as number_of_id
from
  (
    select 
      id
    from `enduring-lane-416206.bellabeat.dailyActivity`
    union all
    select 
      id
    from `enduring-lane-416206.bellabeat.hourlyCalories`
    union all
    select 
      id
    from `enduring-lane-416206.bellabeat.hourlyIntensities`
    union all
    select
      id
    from `enduring-lane-416206.bellabeat.hourlySteps`
    union all
    select
      id
    from `enduring-lane-416206.bellabeat.minuteSleep`
    union all
    select
      id
    from `enduring-lane-416206.bellabeat.weightLogInfo`
  ) A
````
To determine how many unique users are present in each table
````sql
select
  count(distinct id)
from
  `enduring-lane-416206.bellabeat.dailyActivity`
````
Daily Activity = 35 users
````sql
select
  count(distinct id)
from
  `enduring-lane-416206.bellabeat.hourlyCalories`
````
Hourly Calories = 35 users
````sql
select
  count(distinct id)
from
  `enduring-lane-416206.bellabeat.hourlyIntensities`
````
Hourly Intensities = 35 users
````sql
select
  count(distinct id)
from
  `enduring-lane-416206.bellabeat.hourlySteps`
````
Hourly Steps = 35 users
````sql
select
  count(distinct id)
from
  `enduring-lane-416206.bellabeat.minuteSleep`
````
Minute Sleep = 25 users
````sql
select
  count(distinct id)
from
  `enduring-lane-416206.bellabeat.weightLogInfo`
````
Weight Log Info = 13 users

We can see that not all tables has data on all participants. Therefore, it would be recommended that caution be put on any insights and recommendations based around sleep or weight log data. 



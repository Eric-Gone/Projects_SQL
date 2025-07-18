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
To determine and confirm any common columns across all tables. Id is common and will be useful for later JOINs
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
To determine the total number of unique Ids across all tables. Total number is 35 unique users.

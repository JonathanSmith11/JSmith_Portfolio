# Fitibit Daily Activity

https://www.kaggle.com/datasets/arashnic/fitbit?datasetId=1041311&sortBy=voteCount&language=Python


```python
import pandas as pd

#import the .csv data
activity = pd.read_csv('dailyActivity_merged.csv')

#view top 5 rows of data
activity.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>ActivityDate</th>
      <th>TotalSteps</th>
      <th>TotalDistance</th>
      <th>TrackerDistance</th>
      <th>LoggedActivitiesDistance</th>
      <th>VeryActiveDistance</th>
      <th>ModeratelyActiveDistance</th>
      <th>LightActiveDistance</th>
      <th>SedentaryActiveDistance</th>
      <th>VeryActiveMinutes</th>
      <th>FairlyActiveMinutes</th>
      <th>LightlyActiveMinutes</th>
      <th>SedentaryMinutes</th>
      <th>Calories</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1503960366</td>
      <td>04/12/2016</td>
      <td>13162</td>
      <td>8.50</td>
      <td>8.50</td>
      <td>0.0</td>
      <td>1.88</td>
      <td>0.55</td>
      <td>6.06</td>
      <td>0.0</td>
      <td>25</td>
      <td>13</td>
      <td>328</td>
      <td>728</td>
      <td>1985</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1503960366</td>
      <td>4/13/2016</td>
      <td>10735</td>
      <td>6.97</td>
      <td>6.97</td>
      <td>0.0</td>
      <td>1.57</td>
      <td>0.69</td>
      <td>4.71</td>
      <td>0.0</td>
      <td>21</td>
      <td>19</td>
      <td>217</td>
      <td>776</td>
      <td>1797</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1503960366</td>
      <td>4/14/2016</td>
      <td>10460</td>
      <td>6.74</td>
      <td>6.74</td>
      <td>0.0</td>
      <td>2.44</td>
      <td>0.40</td>
      <td>3.91</td>
      <td>0.0</td>
      <td>30</td>
      <td>11</td>
      <td>181</td>
      <td>1218</td>
      <td>1776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1503960366</td>
      <td>4/15/2016</td>
      <td>9762</td>
      <td>6.28</td>
      <td>6.28</td>
      <td>0.0</td>
      <td>2.14</td>
      <td>1.26</td>
      <td>2.83</td>
      <td>0.0</td>
      <td>29</td>
      <td>34</td>
      <td>209</td>
      <td>726</td>
      <td>1745</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1503960366</td>
      <td>4/16/2016</td>
      <td>12669</td>
      <td>8.16</td>
      <td>8.16</td>
      <td>0.0</td>
      <td>2.71</td>
      <td>0.41</td>
      <td>5.04</td>
      <td>0.0</td>
      <td>36</td>
      <td>10</td>
      <td>221</td>
      <td>773</td>
      <td>1863</td>
    </tr>
  </tbody>
</table>
</div>



## Cleaning/Preparing the data


```python
#1 Understand basic information about the data.
    # Such as the column names, missing values and Datatypes

activity.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 940 entries, 0 to 939
    Data columns (total 15 columns):
     #   Column                    Non-Null Count  Dtype  
    ---  ------                    --------------  -----  
     0   Id                        940 non-null    int64  
     1   ActivityDate              940 non-null    object 
     2   TotalSteps                940 non-null    int64  
     3   TotalDistance             940 non-null    float64
     4   TrackerDistance           940 non-null    float64
     5   LoggedActivitiesDistance  940 non-null    float64
     6   VeryActiveDistance        940 non-null    float64
     7   ModeratelyActiveDistance  940 non-null    float64
     8   LightActiveDistance       940 non-null    float64
     9   SedentaryActiveDistance   940 non-null    float64
     10  VeryActiveMinutes         940 non-null    int64  
     11  FairlyActiveMinutes       940 non-null    int64  
     12  LightlyActiveMinutes      940 non-null    int64  
     13  SedentaryMinutes          940 non-null    int64  
     14  Calories                  940 non-null    int64  
    dtypes: float64(7), int64(7), object(1)
    memory usage: 110.3+ KB
    

- 15 columns of data and 940 rows.

- ActivityDate column has a date type of object. This will need to be changed to a datetime for analysis.

- NO null values.


```python
#2 Change ActivityDate to a datetime data type

activity["ActivityDate"] = pd.to_datetime(activity["ActivityDate"], format="%m/%d/%Y")

# Check the change to the column
activity["ActivityDate"].dtype
```




    dtype('<M8[ns]')




```python
# Look at the data to see the change

activity.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>ActivityDate</th>
      <th>TotalSteps</th>
      <th>TotalDistance</th>
      <th>TrackerDistance</th>
      <th>LoggedActivitiesDistance</th>
      <th>VeryActiveDistance</th>
      <th>ModeratelyActiveDistance</th>
      <th>LightActiveDistance</th>
      <th>SedentaryActiveDistance</th>
      <th>VeryActiveMinutes</th>
      <th>FairlyActiveMinutes</th>
      <th>LightlyActiveMinutes</th>
      <th>SedentaryMinutes</th>
      <th>Calories</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1503960366</td>
      <td>2016-04-12</td>
      <td>13162</td>
      <td>8.50</td>
      <td>8.50</td>
      <td>0.0</td>
      <td>1.88</td>
      <td>0.55</td>
      <td>6.06</td>
      <td>0.0</td>
      <td>25</td>
      <td>13</td>
      <td>328</td>
      <td>728</td>
      <td>1985</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1503960366</td>
      <td>2016-04-13</td>
      <td>10735</td>
      <td>6.97</td>
      <td>6.97</td>
      <td>0.0</td>
      <td>1.57</td>
      <td>0.69</td>
      <td>4.71</td>
      <td>0.0</td>
      <td>21</td>
      <td>19</td>
      <td>217</td>
      <td>776</td>
      <td>1797</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1503960366</td>
      <td>2016-04-14</td>
      <td>10460</td>
      <td>6.74</td>
      <td>6.74</td>
      <td>0.0</td>
      <td>2.44</td>
      <td>0.40</td>
      <td>3.91</td>
      <td>0.0</td>
      <td>30</td>
      <td>11</td>
      <td>181</td>
      <td>1218</td>
      <td>1776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1503960366</td>
      <td>2016-04-15</td>
      <td>9762</td>
      <td>6.28</td>
      <td>6.28</td>
      <td>0.0</td>
      <td>2.14</td>
      <td>1.26</td>
      <td>2.83</td>
      <td>0.0</td>
      <td>29</td>
      <td>34</td>
      <td>209</td>
      <td>726</td>
      <td>1745</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1503960366</td>
      <td>2016-04-16</td>
      <td>12669</td>
      <td>8.16</td>
      <td>8.16</td>
      <td>0.0</td>
      <td>2.71</td>
      <td>0.41</td>
      <td>5.04</td>
      <td>0.0</td>
      <td>36</td>
      <td>10</td>
      <td>221</td>
      <td>773</td>
      <td>1863</td>
    </tr>
  </tbody>
</table>
</div>




```python
#3 For further analysis into specific routines of peoples activity, I also split the data to see the days of the week

# create new column "day_of_the_week" to represent day of the week 
activity["DayOfTheWeek"] = activity["ActivityDate"].dt.day_name()

# show 1st 5 rows to confirm
activity.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>ActivityDate</th>
      <th>TotalSteps</th>
      <th>TotalDistance</th>
      <th>TrackerDistance</th>
      <th>LoggedActivitiesDistance</th>
      <th>VeryActiveDistance</th>
      <th>ModeratelyActiveDistance</th>
      <th>LightActiveDistance</th>
      <th>SedentaryActiveDistance</th>
      <th>VeryActiveMinutes</th>
      <th>FairlyActiveMinutes</th>
      <th>LightlyActiveMinutes</th>
      <th>SedentaryMinutes</th>
      <th>Calories</th>
      <th>DayOfTheWeek</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1503960366</td>
      <td>2016-04-12</td>
      <td>13162</td>
      <td>8.50</td>
      <td>8.50</td>
      <td>0.0</td>
      <td>1.88</td>
      <td>0.55</td>
      <td>6.06</td>
      <td>0.0</td>
      <td>25</td>
      <td>13</td>
      <td>328</td>
      <td>728</td>
      <td>1985</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1503960366</td>
      <td>2016-04-13</td>
      <td>10735</td>
      <td>6.97</td>
      <td>6.97</td>
      <td>0.0</td>
      <td>1.57</td>
      <td>0.69</td>
      <td>4.71</td>
      <td>0.0</td>
      <td>21</td>
      <td>19</td>
      <td>217</td>
      <td>776</td>
      <td>1797</td>
      <td>Wednesday</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1503960366</td>
      <td>2016-04-14</td>
      <td>10460</td>
      <td>6.74</td>
      <td>6.74</td>
      <td>0.0</td>
      <td>2.44</td>
      <td>0.40</td>
      <td>3.91</td>
      <td>0.0</td>
      <td>30</td>
      <td>11</td>
      <td>181</td>
      <td>1218</td>
      <td>1776</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1503960366</td>
      <td>2016-04-15</td>
      <td>9762</td>
      <td>6.28</td>
      <td>6.28</td>
      <td>0.0</td>
      <td>2.14</td>
      <td>1.26</td>
      <td>2.83</td>
      <td>0.0</td>
      <td>29</td>
      <td>34</td>
      <td>209</td>
      <td>726</td>
      <td>1745</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1503960366</td>
      <td>2016-04-16</td>
      <td>12669</td>
      <td>8.16</td>
      <td>8.16</td>
      <td>0.0</td>
      <td>2.71</td>
      <td>0.41</td>
      <td>5.04</td>
      <td>0.0</td>
      <td>36</td>
      <td>10</td>
      <td>221</td>
      <td>773</td>
      <td>1863</td>
      <td>Saturday</td>
    </tr>
  </tbody>
</table>
</div>




```python
#4 From the data columns we can see that we have a TotalDistance, but not a TotalMinutes. I create this as a new column.

activity["TotalMinutes"] = activity["VeryActiveMinutes"]+activity["FairlyActiveMinutes"]+activity["LightlyActiveMinutes"]+activity["SedentaryMinutes"]

#show the 1st 5 rows
activity.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>ActivityDate</th>
      <th>TotalSteps</th>
      <th>TotalDistance</th>
      <th>TrackerDistance</th>
      <th>LoggedActivitiesDistance</th>
      <th>VeryActiveDistance</th>
      <th>ModeratelyActiveDistance</th>
      <th>LightActiveDistance</th>
      <th>SedentaryActiveDistance</th>
      <th>VeryActiveMinutes</th>
      <th>FairlyActiveMinutes</th>
      <th>LightlyActiveMinutes</th>
      <th>SedentaryMinutes</th>
      <th>Calories</th>
      <th>DayOfTheWeek</th>
      <th>TotalMinutes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1503960366</td>
      <td>2016-04-12</td>
      <td>13162</td>
      <td>8.50</td>
      <td>8.50</td>
      <td>0.0</td>
      <td>1.88</td>
      <td>0.55</td>
      <td>6.06</td>
      <td>0.0</td>
      <td>25</td>
      <td>13</td>
      <td>328</td>
      <td>728</td>
      <td>1985</td>
      <td>Tuesday</td>
      <td>1094</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1503960366</td>
      <td>2016-04-13</td>
      <td>10735</td>
      <td>6.97</td>
      <td>6.97</td>
      <td>0.0</td>
      <td>1.57</td>
      <td>0.69</td>
      <td>4.71</td>
      <td>0.0</td>
      <td>21</td>
      <td>19</td>
      <td>217</td>
      <td>776</td>
      <td>1797</td>
      <td>Wednesday</td>
      <td>1033</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1503960366</td>
      <td>2016-04-14</td>
      <td>10460</td>
      <td>6.74</td>
      <td>6.74</td>
      <td>0.0</td>
      <td>2.44</td>
      <td>0.40</td>
      <td>3.91</td>
      <td>0.0</td>
      <td>30</td>
      <td>11</td>
      <td>181</td>
      <td>1218</td>
      <td>1776</td>
      <td>Thursday</td>
      <td>1440</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1503960366</td>
      <td>2016-04-15</td>
      <td>9762</td>
      <td>6.28</td>
      <td>6.28</td>
      <td>0.0</td>
      <td>2.14</td>
      <td>1.26</td>
      <td>2.83</td>
      <td>0.0</td>
      <td>29</td>
      <td>34</td>
      <td>209</td>
      <td>726</td>
      <td>1745</td>
      <td>Friday</td>
      <td>998</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1503960366</td>
      <td>2016-04-16</td>
      <td>12669</td>
      <td>8.16</td>
      <td>8.16</td>
      <td>0.0</td>
      <td>2.71</td>
      <td>0.41</td>
      <td>5.04</td>
      <td>0.0</td>
      <td>36</td>
      <td>10</td>
      <td>221</td>
      <td>773</td>
      <td>1863</td>
      <td>Saturday</td>
      <td>1040</td>
    </tr>
  </tbody>
</table>
</div>




```python
#5 I can even go one step further and measure the total hours

activity['TotalHours'] = activity["TotalMinutes"]/60

activity.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>ActivityDate</th>
      <th>TotalSteps</th>
      <th>TotalDistance</th>
      <th>TrackerDistance</th>
      <th>LoggedActivitiesDistance</th>
      <th>VeryActiveDistance</th>
      <th>ModeratelyActiveDistance</th>
      <th>LightActiveDistance</th>
      <th>SedentaryActiveDistance</th>
      <th>VeryActiveMinutes</th>
      <th>FairlyActiveMinutes</th>
      <th>LightlyActiveMinutes</th>
      <th>SedentaryMinutes</th>
      <th>Calories</th>
      <th>DayOfTheWeek</th>
      <th>TotalMinutes</th>
      <th>TotalHours</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1503960366</td>
      <td>2016-04-12</td>
      <td>13162</td>
      <td>8.50</td>
      <td>8.50</td>
      <td>0.0</td>
      <td>1.88</td>
      <td>0.55</td>
      <td>6.06</td>
      <td>0.0</td>
      <td>25</td>
      <td>13</td>
      <td>328</td>
      <td>728</td>
      <td>1985</td>
      <td>Tuesday</td>
      <td>1094</td>
      <td>18.233333</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1503960366</td>
      <td>2016-04-13</td>
      <td>10735</td>
      <td>6.97</td>
      <td>6.97</td>
      <td>0.0</td>
      <td>1.57</td>
      <td>0.69</td>
      <td>4.71</td>
      <td>0.0</td>
      <td>21</td>
      <td>19</td>
      <td>217</td>
      <td>776</td>
      <td>1797</td>
      <td>Wednesday</td>
      <td>1033</td>
      <td>17.216667</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1503960366</td>
      <td>2016-04-14</td>
      <td>10460</td>
      <td>6.74</td>
      <td>6.74</td>
      <td>0.0</td>
      <td>2.44</td>
      <td>0.40</td>
      <td>3.91</td>
      <td>0.0</td>
      <td>30</td>
      <td>11</td>
      <td>181</td>
      <td>1218</td>
      <td>1776</td>
      <td>Thursday</td>
      <td>1440</td>
      <td>24.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1503960366</td>
      <td>2016-04-15</td>
      <td>9762</td>
      <td>6.28</td>
      <td>6.28</td>
      <td>0.0</td>
      <td>2.14</td>
      <td>1.26</td>
      <td>2.83</td>
      <td>0.0</td>
      <td>29</td>
      <td>34</td>
      <td>209</td>
      <td>726</td>
      <td>1745</td>
      <td>Friday</td>
      <td>998</td>
      <td>16.633333</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1503960366</td>
      <td>2016-04-16</td>
      <td>12669</td>
      <td>8.16</td>
      <td>8.16</td>
      <td>0.0</td>
      <td>2.71</td>
      <td>0.41</td>
      <td>5.04</td>
      <td>0.0</td>
      <td>36</td>
      <td>10</td>
      <td>221</td>
      <td>773</td>
      <td>1863</td>
      <td>Saturday</td>
      <td>1040</td>
      <td>17.333333</td>
    </tr>
  </tbody>
</table>
</div>



## Data Analysis


```python
# pull general statistics
activity.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>TotalSteps</th>
      <th>TotalDistance</th>
      <th>TrackerDistance</th>
      <th>LoggedActivitiesDistance</th>
      <th>VeryActiveDistance</th>
      <th>ModeratelyActiveDistance</th>
      <th>LightActiveDistance</th>
      <th>SedentaryActiveDistance</th>
      <th>VeryActiveMinutes</th>
      <th>FairlyActiveMinutes</th>
      <th>LightlyActiveMinutes</th>
      <th>SedentaryMinutes</th>
      <th>Calories</th>
      <th>TotalMinutes</th>
      <th>TotalHours</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>9.400000e+02</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
      <td>940.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>4.855407e+09</td>
      <td>7637.910638</td>
      <td>5.489702</td>
      <td>5.475351</td>
      <td>0.108171</td>
      <td>1.502681</td>
      <td>0.567543</td>
      <td>3.340819</td>
      <td>0.001606</td>
      <td>21.164894</td>
      <td>13.564894</td>
      <td>192.812766</td>
      <td>991.210638</td>
      <td>2303.609574</td>
      <td>1218.753191</td>
      <td>20.312553</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2.424805e+09</td>
      <td>5087.150742</td>
      <td>3.924606</td>
      <td>3.907276</td>
      <td>0.619897</td>
      <td>2.658941</td>
      <td>0.883580</td>
      <td>2.040655</td>
      <td>0.007346</td>
      <td>32.844803</td>
      <td>19.987404</td>
      <td>109.174700</td>
      <td>301.267437</td>
      <td>718.166862</td>
      <td>265.931767</td>
      <td>4.432196</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.503960e+09</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.000000</td>
      <td>0.033333</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.320127e+09</td>
      <td>3789.750000</td>
      <td>2.620000</td>
      <td>2.620000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.945000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>127.000000</td>
      <td>729.750000</td>
      <td>1828.500000</td>
      <td>989.750000</td>
      <td>16.495833</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>4.445115e+09</td>
      <td>7405.500000</td>
      <td>5.245000</td>
      <td>5.245000</td>
      <td>0.000000</td>
      <td>0.210000</td>
      <td>0.240000</td>
      <td>3.365000</td>
      <td>0.000000</td>
      <td>4.000000</td>
      <td>6.000000</td>
      <td>199.000000</td>
      <td>1057.500000</td>
      <td>2134.000000</td>
      <td>1440.000000</td>
      <td>24.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>6.962181e+09</td>
      <td>10727.000000</td>
      <td>7.712500</td>
      <td>7.710000</td>
      <td>0.000000</td>
      <td>2.052500</td>
      <td>0.800000</td>
      <td>4.782500</td>
      <td>0.000000</td>
      <td>32.000000</td>
      <td>19.000000</td>
      <td>264.000000</td>
      <td>1229.500000</td>
      <td>2793.250000</td>
      <td>1440.000000</td>
      <td>24.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>8.877689e+09</td>
      <td>36019.000000</td>
      <td>28.030001</td>
      <td>28.030001</td>
      <td>4.942142</td>
      <td>21.920000</td>
      <td>6.480000</td>
      <td>10.710000</td>
      <td>0.110000</td>
      <td>210.000000</td>
      <td>143.000000</td>
      <td>518.000000</td>
      <td>1440.000000</td>
      <td>4900.000000</td>
      <td>1440.000000</td>
      <td>24.000000</td>
    </tr>
  </tbody>
</table>
</div>



Some findings:

On average, users logged 7,637 steps or 5.4km which is not adequate.

Average calories burned is 2,303 calories.

## Which day is the most active?


```python
import matplotlib.pyplot as plt

#Plot a bar chart with 'DayOfTheWeek' on the x-axis and 'TotalMinutes' on the y-axis

day_grouped = activity.groupby('DayOfTheWeek')['TotalMinutes'].sum().reset_index()
day_grouped.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>DayOfTheWeek</th>
      <th>TotalMinutes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Friday</td>
      <td>155821</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Monday</td>
      <td>150853</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Saturday</td>
      <td>149860</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Sunday</td>
      <td>145048</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Thursday</td>
      <td>173281</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.bar(day_grouped['DayOfTheWeek'],day_grouped['TotalMinutes'])
plt.xlabel('DayOfTheWeek')
plt.ylabel('TotalMinutes')
plt.title('Bar Graph')
plt.show()
```



![Bar Chart 1](https://github.com/JonathanSmith11/JSmith_Portfolio/raw/main/images/DA - Bar chart 1.png)

![Bar Chart 1](https://raw.githubusercontent.com/JonathanSmith11/JSmith_Portfolio/main/path/to/DA - Bar chart 1.png)



## Insight:
    - Tuesday to Thursday is the most active period for the fitbit users
    - Either side of the weekend is the lowest activity levels. Winding down for the weekend and recovering from the weekend!?

## How many calories can you expect to burn per km?


```python
import numpy as np
from scipy import stats

plt.scatter(activity['TotalDistance'],activity['Calories'])
plt.xlabel('Distance in Km')
plt.ylabel('Calories')
plt.title('Scatter Plot')

# Calculate the line of best fit (regression line)
slope, intercept, r_value, p_value, std_err = stats.linregress(activity['TotalDistance'], activity['Calories'])
line_of_best_fit = slope * activity['TotalDistance'] + intercept

# Plot the regression line
plt.plot(activity['TotalDistance'], line_of_best_fit, color='red', label='Regression Line')

# Calculate the R^2 value (coefficient of determination)
r_squared = r_value**2

# Display the R^2 value on the plot in the bottom left corner
plt.text(0.1, 0.1, f'R^2 = {r_squared:.2f}', fontsize=12, transform=plt.gca().transAxes, bbox=dict(facecolor='white', alpha=0.5), ha='right')

plt.show()
```


    
![Scatter 1](https://github.com/JonathanSmith11/JSmith_Portfolio/raw/main/images/DA - Scatter Plot 1.png)

    


## Insight:

        - Positive correlation shows that as we walk more Km, we burn more calories
        - R^2 value of 0.42 suggests that 58% of the data is not explained using Distance alone. Other factors are also involved.
        - There are some obvious outliers here, possibly due to manual error. Such as the km = zero but calories burned being above zero. Or the person who moved over 25km but burned significantly less than expected (<3000).


```python
activity.columns
```




    Index(['Id', 'ActivityDate', 'TotalSteps', 'TotalDistance', 'TrackerDistance',
           'LoggedActivitiesDistance', 'VeryActiveDistance',
           'ModeratelyActiveDistance', 'LightActiveDistance',
           'SedentaryActiveDistance', 'VeryActiveMinutes', 'FairlyActiveMinutes',
           'LightlyActiveMinutes', 'SedentaryMinutes', 'Calories', 'DayOfTheWeek',
           'TotalMinutes', 'TotalHours'],
          dtype='object')



## What is the most common type of activity?


```python

# calculating total of individual minutes column
very_active_mins = activity['VeryActiveMinutes'].sum()
fairly_active_mins = activity['FairlyActiveMinutes'].sum()
lightly_active_mins = activity['LightlyActiveMinutes'].sum()
sedentary_mins = activity['SedentaryMinutes'].sum()

```


```python
# plotting pie chart
slices = [very_active_mins, fairly_active_mins, lightly_active_mins, sedentary_mins]
labels = ["Very active minutes", "Fairly active minutes", "Lightly active minutes", "Sedentary minutes"]
colours = ["lightcoral", "yellowgreen", "lightskyblue", "darkorange"]
explode = [0, 0, 0, 0.1]
plt.style.use("default")
plt.pie(slices, labels = labels, 
        colors = colours, wedgeprops = {"edgecolor": "black"}, 
        explode = explode, autopct = "%1.1f%%")
plt.title("Percentage of Activity in Minutes")
plt.tight_layout()
plt.show()
```


    
![Pie Chart 1](https://github.com/JonathanSmith11/JSmith_Portfolio/raw/main/images/DA - Pie Chart 1.png)
    


## Insight:

    - 81.3% of minutes spent tracking is from sedentary movement. This suggests that these minutes are form everyday commuting, daily mundane acitivity (walking to the printer etc..). 
    - A very small proportion of minutes are coming from Fairly to Very active minutes. This is dissapointing from ahealth perspective as the fitibit is supposed to encourage more active miniutes and exercise.

## Are those with high BMI most active?


```python
# Kaggle also provides data showing weight, BMI and other statistics per user.

user_info = pd.read_csv('weightLogInfo_merged (1).csv')
user_info.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>Date</th>
      <th>WeightKg</th>
      <th>WeightPounds</th>
      <th>Fat</th>
      <th>BMI</th>
      <th>IsManualReport</th>
      <th>LogId</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1503960366</td>
      <td>05/02/2016 23:59</td>
      <td>52.599998</td>
      <td>115.963146</td>
      <td>22.0</td>
      <td>22.650000</td>
      <td>True</td>
      <td>1.462230e+12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1503960366</td>
      <td>05/03/2016 23:59</td>
      <td>52.599998</td>
      <td>115.963146</td>
      <td>NaN</td>
      <td>22.650000</td>
      <td>True</td>
      <td>1.462320e+12</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1927972279</td>
      <td>4/13/2016 1:08:52 AM</td>
      <td>133.500000</td>
      <td>294.317120</td>
      <td>NaN</td>
      <td>47.540001</td>
      <td>False</td>
      <td>1.460510e+12</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2873212765</td>
      <td>4/21/2016 11:59:59 PM</td>
      <td>56.700001</td>
      <td>125.002104</td>
      <td>NaN</td>
      <td>21.450001</td>
      <td>True</td>
      <td>1.461280e+12</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2873212765</td>
      <td>05/12/2016 23:59</td>
      <td>57.299999</td>
      <td>126.324875</td>
      <td>NaN</td>
      <td>21.690001</td>
      <td>True</td>
      <td>1.463100e+12</td>
    </tr>
  </tbody>
</table>
</div>




```python
user_info = user_info[['Id','BMI']]
```


```python
user_info
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>BMI</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1503960366</td>
      <td>22.650000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1503960366</td>
      <td>22.650000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1927972279</td>
      <td>47.540001</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2873212765</td>
      <td>21.450001</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2873212765</td>
      <td>21.690001</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>62</th>
      <td>8877689391</td>
      <td>25.440001</td>
    </tr>
    <tr>
      <th>63</th>
      <td>8877689391</td>
      <td>25.559999</td>
    </tr>
    <tr>
      <th>64</th>
      <td>8877689391</td>
      <td>25.610001</td>
    </tr>
    <tr>
      <th>65</th>
      <td>8877689391</td>
      <td>25.559999</td>
    </tr>
    <tr>
      <th>66</th>
      <td>8877689391</td>
      <td>25.139999</td>
    </tr>
  </tbody>
</table>
<p>67 rows × 2 columns</p>
</div>



I would like to merge the user_info['BMI'] column onto the activity data. I can do this by peforming a join on the 'Id' column.

First, I will take the average BMI per Id


```python
user_info = user_info.groupby('Id')['BMI'].mean()
user_info
```




    Id
    1503960366    22.650000
    1927972279    47.540001
    2873212765    21.570001
    4319703577    27.415000
    4558609924    27.214000
    5577150313    28.000000
    6962181067    24.028000
    8877689391    25.487083
    Name: BMI, dtype: float64




```python
print('There are: ' + str(len(user_info)) + ' unique Ids')
```

    There are: 8 unique Ids
    


```python
# Merge BMI onto acitivty df using Id as the join column 
```


```python
merged_BMI = activity.merge(user_info, on='Id', how='inner')
merged_BMI.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>ActivityDate</th>
      <th>TotalSteps</th>
      <th>TotalDistance</th>
      <th>TrackerDistance</th>
      <th>LoggedActivitiesDistance</th>
      <th>VeryActiveDistance</th>
      <th>ModeratelyActiveDistance</th>
      <th>LightActiveDistance</th>
      <th>SedentaryActiveDistance</th>
      <th>VeryActiveMinutes</th>
      <th>FairlyActiveMinutes</th>
      <th>LightlyActiveMinutes</th>
      <th>SedentaryMinutes</th>
      <th>Calories</th>
      <th>DayOfTheWeek</th>
      <th>TotalMinutes</th>
      <th>TotalHours</th>
      <th>BMI</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1503960366</td>
      <td>2016-04-12</td>
      <td>13162</td>
      <td>8.50</td>
      <td>8.50</td>
      <td>0.0</td>
      <td>1.88</td>
      <td>0.55</td>
      <td>6.06</td>
      <td>0.0</td>
      <td>25</td>
      <td>13</td>
      <td>328</td>
      <td>728</td>
      <td>1985</td>
      <td>Tuesday</td>
      <td>1094</td>
      <td>18.233333</td>
      <td>22.65</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1503960366</td>
      <td>2016-04-13</td>
      <td>10735</td>
      <td>6.97</td>
      <td>6.97</td>
      <td>0.0</td>
      <td>1.57</td>
      <td>0.69</td>
      <td>4.71</td>
      <td>0.0</td>
      <td>21</td>
      <td>19</td>
      <td>217</td>
      <td>776</td>
      <td>1797</td>
      <td>Wednesday</td>
      <td>1033</td>
      <td>17.216667</td>
      <td>22.65</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1503960366</td>
      <td>2016-04-14</td>
      <td>10460</td>
      <td>6.74</td>
      <td>6.74</td>
      <td>0.0</td>
      <td>2.44</td>
      <td>0.40</td>
      <td>3.91</td>
      <td>0.0</td>
      <td>30</td>
      <td>11</td>
      <td>181</td>
      <td>1218</td>
      <td>1776</td>
      <td>Thursday</td>
      <td>1440</td>
      <td>24.000000</td>
      <td>22.65</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1503960366</td>
      <td>2016-04-15</td>
      <td>9762</td>
      <td>6.28</td>
      <td>6.28</td>
      <td>0.0</td>
      <td>2.14</td>
      <td>1.26</td>
      <td>2.83</td>
      <td>0.0</td>
      <td>29</td>
      <td>34</td>
      <td>209</td>
      <td>726</td>
      <td>1745</td>
      <td>Friday</td>
      <td>998</td>
      <td>16.633333</td>
      <td>22.65</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1503960366</td>
      <td>2016-04-16</td>
      <td>12669</td>
      <td>8.16</td>
      <td>8.16</td>
      <td>0.0</td>
      <td>2.71</td>
      <td>0.41</td>
      <td>5.04</td>
      <td>0.0</td>
      <td>36</td>
      <td>10</td>
      <td>221</td>
      <td>773</td>
      <td>1863</td>
      <td>Saturday</td>
      <td>1040</td>
      <td>17.333333</td>
      <td>22.65</td>
    </tr>
  </tbody>
</table>
</div>




```python
BMI_group = merged_BMI.groupby('BMI')['VeryActiveMinutes'].mean().reset_index()
```


```python
plt.bar(BMI_group['BMI'],BMI_group['VeryActiveMinutes'])
plt.xlabel('BMI')
plt.ylabel('VeryActiveMinutes')
plt.title('Bar Graph')
plt.show()
```


    
![Bar Chart 2](https://github.com/JonathanSmith11/JSmith_Portfolio/raw/main/images/DA - Bar chart 2.png)
    



```python
BMI_group = merged_BMI.groupby('BMI')['FairlyActiveMinutes'].mean().reset_index()
```


```python
plt.bar(BMI_group['BMI'],BMI_group['FairlyActiveMinutes'])
plt.xlabel('BMI')
plt.ylabel('VeryActiveMinutes')
plt.title('Bar Graph')
plt.show()
```


    
![Bar Chart 3](https://github.com/JonathanSmith11/JSmith_Portfolio/raw/main/images/DA - bar chart 3.png)
    



```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Assuming you have loaded your dataset into the 'data' DataFrame

# Create a pivot table to aggregate minutes for each BMI and activity level
pivot_table = merged_BMI.pivot_table(index='BMI', values=['VeryActiveMinutes', 'FairlyActiveMinutes', 'LightlyActiveMinutes', 'SedentaryMinutes'], aggfunc='sum')

# Reshape the pivot table to a long-format DataFrame
activity_minutes = pivot_table.reset_index().melt(id_vars='BMI', var_name='Activity', value_name='Minutes')

# Create the graph using seaborn
plt.figure(figsize=(10, 6))
sns.barplot(x='BMI', y='Minutes', hue='Activity', data=activity_minutes)
plt.xlabel('BMI')
plt.ylabel('Minutes')
plt.title('Minutes Spent in Different Activity Levels for Each BMI')
plt.legend(title='Activity', loc='upper right')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```


    
![Bar Chart 4](https://github.com/JonathanSmith11/JSmith_Portfolio/raw/main/images/DA - bar chart 4.png)
    


## What time of day is most active?


```python
# Kaggle also provides data showing steps each hour per user.

steps = pd.read_csv('hourlySteps_merged.csv')
steps['ActivityHour'].unique()
```




    array(['04/12/2016 00:00', '04/12/2016 01:00', '04/12/2016 02:00',
           '04/12/2016 03:00', '04/12/2016 04:00', '04/12/2016 05:00',
           '04/12/2016 06:00', '04/12/2016 07:00', '04/12/2016 08:00',
           '04/12/2016 09:00', '04/12/2016 10:00', '04/12/2016 11:00',
           '04/12/2016 12:00', '04/12/2016 13:00', '04/12/2016 14:00',
           '04/12/2016 15:00', '04/12/2016 16:00', '04/12/2016 17:00',
           '04/12/2016 18:00', '04/12/2016 19:00', '04/12/2016 20:00',
           '04/12/2016 21:00', '04/12/2016 22:00', '04/12/2016 23:00',
           '4/13/2016 12:00:00 AM', '4/13/2016 1:00:00 AM',
           '4/13/2016 2:00:00 AM', '4/13/2016 3:00:00 AM',
           '4/13/2016 4:00:00 AM', '4/13/2016 5:00:00 AM',
           '4/13/2016 6:00:00 AM', '4/13/2016 7:00:00 AM',
           '4/13/2016 8:00:00 AM', '4/13/2016 9:00:00 AM',
           '4/13/2016 10:00:00 AM', '4/13/2016 11:00:00 AM',
           '4/13/2016 12:00:00 PM', '4/13/2016 1:00:00 PM',
           '4/13/2016 2:00:00 PM', '4/13/2016 3:00:00 PM',
           '4/13/2016 4:00:00 PM', '4/13/2016 5:00:00 PM',
           '4/13/2016 6:00:00 PM', '4/13/2016 7:00:00 PM',
           '4/13/2016 8:00:00 PM', '4/13/2016 9:00:00 PM',
           '4/13/2016 10:00:00 PM', '4/13/2016 11:00:00 PM',
           '4/14/2016 12:00:00 AM', '4/14/2016 1:00:00 AM',
           '4/14/2016 2:00:00 AM', '4/14/2016 3:00:00 AM',
           '4/14/2016 4:00:00 AM', '4/14/2016 5:00:00 AM',
           '4/14/2016 6:00:00 AM', '4/14/2016 7:00:00 AM',
           '4/14/2016 8:00:00 AM', '4/14/2016 9:00:00 AM',
           '4/14/2016 10:00:00 AM', '4/14/2016 11:00:00 AM',
           '4/14/2016 12:00:00 PM', '4/14/2016 1:00:00 PM',
           '4/14/2016 2:00:00 PM', '4/14/2016 3:00:00 PM',
           '4/14/2016 4:00:00 PM', '4/14/2016 5:00:00 PM',
           '4/14/2016 6:00:00 PM', '4/14/2016 7:00:00 PM',
           '4/14/2016 8:00:00 PM', '4/14/2016 9:00:00 PM',
           '4/14/2016 10:00:00 PM', '4/14/2016 11:00:00 PM',
           '4/15/2016 12:00:00 AM', '4/15/2016 1:00:00 AM',
           '4/15/2016 2:00:00 AM', '4/15/2016 3:00:00 AM',
           '4/15/2016 4:00:00 AM', '4/15/2016 5:00:00 AM',
           '4/15/2016 6:00:00 AM', '4/15/2016 7:00:00 AM',
           '4/15/2016 8:00:00 AM', '4/15/2016 9:00:00 AM',
           '4/15/2016 10:00:00 AM', '4/15/2016 11:00:00 AM',
           '4/15/2016 12:00:00 PM', '4/15/2016 1:00:00 PM',
           '4/15/2016 2:00:00 PM', '4/15/2016 3:00:00 PM',
           '4/15/2016 4:00:00 PM', '4/15/2016 5:00:00 PM',
           '4/15/2016 6:00:00 PM', '4/15/2016 7:00:00 PM',
           '4/15/2016 8:00:00 PM', '4/15/2016 9:00:00 PM',
           '4/15/2016 10:00:00 PM', '4/15/2016 11:00:00 PM',
           '4/16/2016 12:00:00 AM', '4/16/2016 1:00:00 AM',
           '4/16/2016 2:00:00 AM', '4/16/2016 3:00:00 AM',
           '4/16/2016 4:00:00 AM', '4/16/2016 5:00:00 AM',
           '4/16/2016 6:00:00 AM', '4/16/2016 7:00:00 AM',
           '4/16/2016 8:00:00 AM', '4/16/2016 9:00:00 AM',
           '4/16/2016 10:00:00 AM', '4/16/2016 11:00:00 AM',
           '4/16/2016 12:00:00 PM', '4/16/2016 1:00:00 PM',
           '4/16/2016 2:00:00 PM', '4/16/2016 3:00:00 PM',
           '4/16/2016 4:00:00 PM', '4/16/2016 5:00:00 PM',
           '4/16/2016 6:00:00 PM', '4/16/2016 7:00:00 PM',
           '4/16/2016 8:00:00 PM', '4/16/2016 9:00:00 PM',
           '4/16/2016 10:00:00 PM', '4/16/2016 11:00:00 PM',
           '4/17/2016 12:00:00 AM', '4/17/2016 1:00:00 AM',
           '4/17/2016 2:00:00 AM', '4/17/2016 3:00:00 AM',
           '4/17/2016 4:00:00 AM', '4/17/2016 5:00:00 AM',
           '4/17/2016 6:00:00 AM', '4/17/2016 7:00:00 AM',
           '4/17/2016 8:00:00 AM', '4/17/2016 9:00:00 AM',
           '4/17/2016 10:00:00 AM', '4/17/2016 11:00:00 AM',
           '4/17/2016 12:00:00 PM', '4/17/2016 1:00:00 PM',
           '4/17/2016 2:00:00 PM', '4/17/2016 3:00:00 PM',
           '4/17/2016 4:00:00 PM', '4/17/2016 5:00:00 PM',
           '4/17/2016 6:00:00 PM', '4/17/2016 7:00:00 PM',
           '4/17/2016 8:00:00 PM', '4/17/2016 9:00:00 PM',
           '4/17/2016 10:00:00 PM', '4/17/2016 11:00:00 PM',
           '4/18/2016 12:00:00 AM', '4/18/2016 1:00:00 AM',
           '4/18/2016 2:00:00 AM', '4/18/2016 3:00:00 AM',
           '4/18/2016 4:00:00 AM', '4/18/2016 5:00:00 AM',
           '4/18/2016 6:00:00 AM', '4/18/2016 7:00:00 AM',
           '4/18/2016 8:00:00 AM', '4/18/2016 9:00:00 AM',
           '4/18/2016 10:00:00 AM', '4/18/2016 11:00:00 AM',
           '4/18/2016 12:00:00 PM', '4/18/2016 1:00:00 PM',
           '4/18/2016 2:00:00 PM', '4/18/2016 3:00:00 PM',
           '4/18/2016 4:00:00 PM', '4/18/2016 5:00:00 PM',
           '4/18/2016 6:00:00 PM', '4/18/2016 7:00:00 PM',
           '4/18/2016 8:00:00 PM', '4/18/2016 9:00:00 PM',
           '4/18/2016 10:00:00 PM', '4/18/2016 11:00:00 PM',
           '4/19/2016 12:00:00 AM', '4/19/2016 1:00:00 AM',
           '4/19/2016 2:00:00 AM', '4/19/2016 3:00:00 AM',
           '4/19/2016 4:00:00 AM', '4/19/2016 5:00:00 AM',
           '4/19/2016 6:00:00 AM', '4/19/2016 7:00:00 AM',
           '4/19/2016 8:00:00 AM', '4/19/2016 9:00:00 AM',
           '4/19/2016 10:00:00 AM', '4/19/2016 11:00:00 AM',
           '4/19/2016 12:00:00 PM', '4/19/2016 1:00:00 PM',
           '4/19/2016 2:00:00 PM', '4/19/2016 3:00:00 PM',
           '4/19/2016 4:00:00 PM', '4/19/2016 5:00:00 PM',
           '4/19/2016 6:00:00 PM', '4/19/2016 7:00:00 PM',
           '4/19/2016 8:00:00 PM', '4/19/2016 9:00:00 PM',
           '4/19/2016 10:00:00 PM', '4/19/2016 11:00:00 PM',
           '4/20/2016 12:00:00 AM', '4/20/2016 1:00:00 AM',
           '4/20/2016 2:00:00 AM', '4/20/2016 3:00:00 AM',
           '4/20/2016 4:00:00 AM', '4/20/2016 5:00:00 AM',
           '4/20/2016 6:00:00 AM', '4/20/2016 7:00:00 AM',
           '4/20/2016 8:00:00 AM', '4/20/2016 9:00:00 AM',
           '4/20/2016 10:00:00 AM', '4/20/2016 11:00:00 AM',
           '4/20/2016 12:00:00 PM', '4/20/2016 1:00:00 PM',
           '4/20/2016 2:00:00 PM', '4/20/2016 3:00:00 PM',
           '4/20/2016 4:00:00 PM', '4/20/2016 5:00:00 PM',
           '4/20/2016 6:00:00 PM', '4/20/2016 7:00:00 PM',
           '4/20/2016 8:00:00 PM', '4/20/2016 9:00:00 PM',
           '4/20/2016 10:00:00 PM', '4/20/2016 11:00:00 PM',
           '4/21/2016 12:00:00 AM', '4/21/2016 1:00:00 AM',
           '4/21/2016 2:00:00 AM', '4/21/2016 3:00:00 AM',
           '4/21/2016 4:00:00 AM', '4/21/2016 5:00:00 AM',
           '4/21/2016 6:00:00 AM', '4/21/2016 7:00:00 AM',
           '4/21/2016 8:00:00 AM', '4/21/2016 9:00:00 AM',
           '4/21/2016 10:00:00 AM', '4/21/2016 11:00:00 AM',
           '4/21/2016 12:00:00 PM', '4/21/2016 1:00:00 PM',
           '4/21/2016 2:00:00 PM', '4/21/2016 3:00:00 PM',
           '4/21/2016 4:00:00 PM', '4/21/2016 5:00:00 PM',
           '4/21/2016 6:00:00 PM', '4/21/2016 7:00:00 PM',
           '4/21/2016 8:00:00 PM', '4/21/2016 9:00:00 PM',
           '4/21/2016 10:00:00 PM', '4/21/2016 11:00:00 PM',
           '4/22/2016 12:00:00 AM', '4/22/2016 1:00:00 AM',
           '4/22/2016 2:00:00 AM', '4/22/2016 3:00:00 AM',
           '4/22/2016 4:00:00 AM', '4/22/2016 5:00:00 AM',
           '4/22/2016 6:00:00 AM', '4/22/2016 7:00:00 AM',
           '4/22/2016 8:00:00 AM', '4/22/2016 9:00:00 AM',
           '4/22/2016 10:00:00 AM', '4/22/2016 11:00:00 AM',
           '4/22/2016 12:00:00 PM', '4/22/2016 1:00:00 PM',
           '4/22/2016 2:00:00 PM', '4/22/2016 3:00:00 PM',
           '4/22/2016 4:00:00 PM', '4/22/2016 5:00:00 PM',
           '4/22/2016 6:00:00 PM', '4/22/2016 7:00:00 PM',
           '4/22/2016 8:00:00 PM', '4/22/2016 9:00:00 PM',
           '4/22/2016 10:00:00 PM', '4/22/2016 11:00:00 PM',
           '4/23/2016 12:00:00 AM', '4/23/2016 1:00:00 AM',
           '4/23/2016 2:00:00 AM', '4/23/2016 3:00:00 AM',
           '4/23/2016 4:00:00 AM', '4/23/2016 5:00:00 AM',
           '4/23/2016 6:00:00 AM', '4/23/2016 7:00:00 AM',
           '4/23/2016 8:00:00 AM', '4/23/2016 9:00:00 AM',
           '4/23/2016 10:00:00 AM', '4/23/2016 11:00:00 AM',
           '4/23/2016 12:00:00 PM', '4/23/2016 1:00:00 PM',
           '4/23/2016 2:00:00 PM', '4/23/2016 3:00:00 PM',
           '4/23/2016 4:00:00 PM', '4/23/2016 5:00:00 PM',
           '4/23/2016 6:00:00 PM', '4/23/2016 7:00:00 PM',
           '4/23/2016 8:00:00 PM', '4/23/2016 9:00:00 PM',
           '4/23/2016 10:00:00 PM', '4/23/2016 11:00:00 PM',
           '4/24/2016 12:00:00 AM', '4/24/2016 1:00:00 AM',
           '4/24/2016 2:00:00 AM', '4/24/2016 3:00:00 AM',
           '4/24/2016 4:00:00 AM', '4/24/2016 5:00:00 AM',
           '4/24/2016 6:00:00 AM', '4/24/2016 7:00:00 AM',
           '4/24/2016 8:00:00 AM', '4/24/2016 9:00:00 AM',
           '4/24/2016 10:00:00 AM', '4/24/2016 11:00:00 AM',
           '4/24/2016 12:00:00 PM', '4/24/2016 1:00:00 PM',
           '4/24/2016 2:00:00 PM', '4/24/2016 3:00:00 PM',
           '4/24/2016 4:00:00 PM', '4/24/2016 5:00:00 PM',
           '4/24/2016 6:00:00 PM', '4/24/2016 7:00:00 PM',
           '4/24/2016 8:00:00 PM', '4/24/2016 9:00:00 PM',
           '4/24/2016 10:00:00 PM', '4/24/2016 11:00:00 PM',
           '4/25/2016 12:00:00 AM', '4/25/2016 1:00:00 AM',
           '4/25/2016 2:00:00 AM', '4/25/2016 3:00:00 AM',
           '4/25/2016 4:00:00 AM', '4/25/2016 5:00:00 AM',
           '4/25/2016 6:00:00 AM', '4/25/2016 7:00:00 AM',
           '4/25/2016 8:00:00 AM', '4/25/2016 9:00:00 AM',
           '4/25/2016 10:00:00 AM', '4/25/2016 11:00:00 AM',
           '4/25/2016 12:00:00 PM', '4/25/2016 1:00:00 PM',
           '4/25/2016 2:00:00 PM', '4/25/2016 3:00:00 PM',
           '4/25/2016 4:00:00 PM', '4/25/2016 5:00:00 PM',
           '4/25/2016 6:00:00 PM', '4/25/2016 7:00:00 PM',
           '4/25/2016 8:00:00 PM', '4/25/2016 9:00:00 PM',
           '4/25/2016 10:00:00 PM', '4/25/2016 11:00:00 PM',
           '4/26/2016 12:00:00 AM', '4/26/2016 1:00:00 AM',
           '4/26/2016 2:00:00 AM', '4/26/2016 3:00:00 AM',
           '4/26/2016 4:00:00 AM', '4/26/2016 5:00:00 AM',
           '4/26/2016 6:00:00 AM', '4/26/2016 7:00:00 AM',
           '4/26/2016 8:00:00 AM', '4/26/2016 9:00:00 AM',
           '4/26/2016 10:00:00 AM', '4/26/2016 11:00:00 AM',
           '4/26/2016 12:00:00 PM', '4/26/2016 1:00:00 PM',
           '4/26/2016 2:00:00 PM', '4/26/2016 3:00:00 PM',
           '4/26/2016 4:00:00 PM', '4/26/2016 5:00:00 PM',
           '4/26/2016 6:00:00 PM', '4/26/2016 7:00:00 PM',
           '4/26/2016 8:00:00 PM', '4/26/2016 9:00:00 PM',
           '4/26/2016 10:00:00 PM', '4/26/2016 11:00:00 PM',
           '4/27/2016 12:00:00 AM', '4/27/2016 1:00:00 AM',
           '4/27/2016 2:00:00 AM', '4/27/2016 3:00:00 AM',
           '4/27/2016 4:00:00 AM', '4/27/2016 5:00:00 AM',
           '4/27/2016 6:00:00 AM', '4/27/2016 7:00:00 AM',
           '4/27/2016 8:00:00 AM', '4/27/2016 9:00:00 AM',
           '4/27/2016 10:00:00 AM', '4/27/2016 11:00:00 AM',
           '4/27/2016 12:00:00 PM', '4/27/2016 1:00:00 PM',
           '4/27/2016 2:00:00 PM', '4/27/2016 3:00:00 PM',
           '4/27/2016 4:00:00 PM', '4/27/2016 5:00:00 PM',
           '4/27/2016 6:00:00 PM', '4/27/2016 7:00:00 PM',
           '4/27/2016 8:00:00 PM', '4/27/2016 9:00:00 PM',
           '4/27/2016 10:00:00 PM', '4/27/2016 11:00:00 PM',
           '4/28/2016 12:00:00 AM', '4/28/2016 1:00:00 AM',
           '4/28/2016 2:00:00 AM', '4/28/2016 3:00:00 AM',
           '4/28/2016 4:00:00 AM', '4/28/2016 5:00:00 AM',
           '4/28/2016 6:00:00 AM', '4/28/2016 7:00:00 AM',
           '4/28/2016 8:00:00 AM', '4/28/2016 9:00:00 AM',
           '4/28/2016 10:00:00 AM', '4/28/2016 11:00:00 AM',
           '4/28/2016 12:00:00 PM', '4/28/2016 1:00:00 PM',
           '4/28/2016 2:00:00 PM', '4/28/2016 3:00:00 PM',
           '4/28/2016 4:00:00 PM', '4/28/2016 5:00:00 PM',
           '4/28/2016 6:00:00 PM', '4/28/2016 7:00:00 PM',
           '4/28/2016 8:00:00 PM', '4/28/2016 9:00:00 PM',
           '4/28/2016 10:00:00 PM', '4/28/2016 11:00:00 PM',
           '4/29/2016 12:00:00 AM', '4/29/2016 1:00:00 AM',
           '4/29/2016 2:00:00 AM', '4/29/2016 3:00:00 AM',
           '4/29/2016 4:00:00 AM', '4/29/2016 5:00:00 AM',
           '4/29/2016 6:00:00 AM', '4/29/2016 7:00:00 AM',
           '4/29/2016 8:00:00 AM', '4/29/2016 9:00:00 AM',
           '4/29/2016 10:00:00 AM', '4/29/2016 11:00:00 AM',
           '4/29/2016 12:00:00 PM', '4/29/2016 1:00:00 PM',
           '4/29/2016 2:00:00 PM', '4/29/2016 3:00:00 PM',
           '4/29/2016 4:00:00 PM', '4/29/2016 5:00:00 PM',
           '4/29/2016 6:00:00 PM', '4/29/2016 7:00:00 PM',
           '4/29/2016 8:00:00 PM', '4/29/2016 9:00:00 PM',
           '4/29/2016 10:00:00 PM', '4/29/2016 11:00:00 PM',
           '4/30/2016 12:00:00 AM', '4/30/2016 1:00:00 AM',
           '4/30/2016 2:00:00 AM', '4/30/2016 3:00:00 AM',
           '4/30/2016 4:00:00 AM', '4/30/2016 5:00:00 AM',
           '4/30/2016 6:00:00 AM', '4/30/2016 7:00:00 AM',
           '4/30/2016 8:00:00 AM', '4/30/2016 9:00:00 AM',
           '4/30/2016 10:00:00 AM', '4/30/2016 11:00:00 AM',
           '4/30/2016 12:00:00 PM', '4/30/2016 1:00:00 PM',
           '4/30/2016 2:00:00 PM', '4/30/2016 3:00:00 PM',
           '4/30/2016 4:00:00 PM', '4/30/2016 5:00:00 PM',
           '4/30/2016 6:00:00 PM', '4/30/2016 7:00:00 PM',
           '4/30/2016 8:00:00 PM', '4/30/2016 9:00:00 PM',
           '4/30/2016 10:00:00 PM', '4/30/2016 11:00:00 PM',
           '05/01/2016 00:00', '05/01/2016 01:00', '05/01/2016 02:00',
           '05/01/2016 03:00', '05/01/2016 04:00', '05/01/2016 05:00',
           '05/01/2016 06:00', '05/01/2016 07:00', '05/01/2016 08:00',
           '05/01/2016 09:00', '05/01/2016 10:00', '05/01/2016 11:00',
           '05/01/2016 12:00', '05/01/2016 13:00', '05/01/2016 14:00',
           '05/01/2016 15:00', '05/01/2016 16:00', '05/01/2016 17:00',
           '05/01/2016 18:00', '05/01/2016 19:00', '05/01/2016 20:00',
           '05/01/2016 21:00', '05/01/2016 22:00', '05/01/2016 23:00',
           '05/02/2016 00:00', '05/02/2016 01:00', '05/02/2016 02:00',
           '05/02/2016 03:00', '05/02/2016 04:00', '05/02/2016 05:00',
           '05/02/2016 06:00', '05/02/2016 07:00', '05/02/2016 08:00',
           '05/02/2016 09:00', '05/02/2016 10:00', '05/02/2016 11:00',
           '05/02/2016 12:00', '05/02/2016 13:00', '05/02/2016 14:00',
           '05/02/2016 15:00', '05/02/2016 16:00', '05/02/2016 17:00',
           '05/02/2016 18:00', '05/02/2016 19:00', '05/02/2016 20:00',
           '05/02/2016 21:00', '05/02/2016 22:00', '05/02/2016 23:00',
           '05/03/2016 00:00', '05/03/2016 01:00', '05/03/2016 02:00',
           '05/03/2016 03:00', '05/03/2016 04:00', '05/03/2016 05:00',
           '05/03/2016 06:00', '05/03/2016 07:00', '05/03/2016 08:00',
           '05/03/2016 09:00', '05/03/2016 10:00', '05/03/2016 11:00',
           '05/03/2016 12:00', '05/03/2016 13:00', '05/03/2016 14:00',
           '05/03/2016 15:00', '05/03/2016 16:00', '05/03/2016 17:00',
           '05/03/2016 18:00', '05/03/2016 19:00', '05/03/2016 20:00',
           '05/03/2016 21:00', '05/03/2016 22:00', '05/03/2016 23:00',
           '05/04/2016 00:00', '05/04/2016 01:00', '05/04/2016 02:00',
           '05/04/2016 03:00', '05/04/2016 04:00', '05/04/2016 05:00',
           '05/04/2016 06:00', '05/04/2016 07:00', '05/04/2016 08:00',
           '05/04/2016 09:00', '05/04/2016 10:00', '05/04/2016 11:00',
           '05/04/2016 12:00', '05/04/2016 13:00', '05/04/2016 14:00',
           '05/04/2016 15:00', '05/04/2016 16:00', '05/04/2016 17:00',
           '05/04/2016 18:00', '05/04/2016 19:00', '05/04/2016 20:00',
           '05/04/2016 21:00', '05/04/2016 22:00', '05/04/2016 23:00',
           '05/05/2016 00:00', '05/05/2016 01:00', '05/05/2016 02:00',
           '05/05/2016 03:00', '05/05/2016 04:00', '05/05/2016 05:00',
           '05/05/2016 06:00', '05/05/2016 07:00', '05/05/2016 08:00',
           '05/05/2016 09:00', '05/05/2016 10:00', '05/05/2016 11:00',
           '05/05/2016 12:00', '05/05/2016 13:00', '05/05/2016 14:00',
           '05/05/2016 15:00', '05/05/2016 16:00', '05/05/2016 17:00',
           '05/05/2016 18:00', '05/05/2016 19:00', '05/05/2016 20:00',
           '05/05/2016 21:00', '05/05/2016 22:00', '05/05/2016 23:00',
           '05/06/2016 00:00', '05/06/2016 01:00', '05/06/2016 02:00',
           '05/06/2016 03:00', '05/06/2016 04:00', '05/06/2016 05:00',
           '05/06/2016 06:00', '05/06/2016 07:00', '05/06/2016 08:00',
           '05/06/2016 09:00', '05/06/2016 10:00', '05/06/2016 11:00',
           '05/06/2016 12:00', '05/06/2016 13:00', '05/06/2016 14:00',
           '05/06/2016 15:00', '05/06/2016 16:00', '05/06/2016 17:00',
           '05/06/2016 18:00', '05/06/2016 19:00', '05/06/2016 20:00',
           '05/06/2016 21:00', '05/06/2016 22:00', '05/06/2016 23:00',
           '05/07/2016 00:00', '05/07/2016 01:00', '05/07/2016 02:00',
           '05/07/2016 03:00', '05/07/2016 04:00', '05/07/2016 05:00',
           '05/07/2016 06:00', '05/07/2016 07:00', '05/07/2016 08:00',
           '05/07/2016 09:00', '05/07/2016 10:00', '05/07/2016 11:00',
           '05/07/2016 12:00', '05/07/2016 13:00', '05/07/2016 14:00',
           '05/07/2016 15:00', '05/07/2016 16:00', '05/07/2016 17:00',
           '05/07/2016 18:00', '05/07/2016 19:00', '05/07/2016 20:00',
           '05/07/2016 21:00', '05/07/2016 22:00', '05/07/2016 23:00',
           '05/08/2016 00:00', '05/08/2016 01:00', '05/08/2016 02:00',
           '05/08/2016 03:00', '05/08/2016 04:00', '05/08/2016 05:00',
           '05/08/2016 06:00', '05/08/2016 07:00', '05/08/2016 08:00',
           '05/08/2016 09:00', '05/08/2016 10:00', '05/08/2016 11:00',
           '05/08/2016 12:00', '05/08/2016 13:00', '05/08/2016 14:00',
           '05/08/2016 15:00', '05/08/2016 16:00', '05/08/2016 17:00',
           '05/08/2016 18:00', '05/08/2016 19:00', '05/08/2016 20:00',
           '05/08/2016 21:00', '05/08/2016 22:00', '05/08/2016 23:00',
           '05/09/2016 00:00', '05/09/2016 01:00', '05/09/2016 02:00',
           '05/09/2016 03:00', '05/09/2016 04:00', '05/09/2016 05:00',
           '05/09/2016 06:00', '05/09/2016 07:00', '05/09/2016 08:00',
           '05/09/2016 09:00', '05/09/2016 10:00', '05/09/2016 11:00',
           '05/09/2016 12:00', '05/09/2016 13:00', '05/09/2016 14:00',
           '05/09/2016 15:00', '05/09/2016 16:00', '05/09/2016 17:00',
           '05/09/2016 18:00', '05/09/2016 19:00', '05/09/2016 20:00',
           '05/09/2016 21:00', '05/09/2016 22:00', '05/09/2016 23:00',
           '05/10/2016 00:00', '05/10/2016 01:00', '05/10/2016 02:00',
           '05/10/2016 03:00', '05/10/2016 04:00', '05/10/2016 05:00',
           '05/10/2016 06:00', '05/10/2016 07:00', '05/10/2016 08:00',
           '05/10/2016 09:00', '05/10/2016 10:00', '05/10/2016 11:00',
           '05/10/2016 12:00', '05/10/2016 13:00', '05/10/2016 14:00',
           '05/10/2016 15:00', '05/10/2016 16:00', '05/10/2016 17:00',
           '05/10/2016 18:00', '05/10/2016 19:00', '05/10/2016 20:00',
           '05/10/2016 21:00', '05/10/2016 22:00', '05/10/2016 23:00',
           '05/11/2016 00:00', '05/11/2016 01:00', '05/11/2016 02:00',
           '05/11/2016 03:00', '05/11/2016 04:00', '05/11/2016 05:00',
           '05/11/2016 06:00', '05/11/2016 07:00', '05/11/2016 08:00',
           '05/11/2016 09:00', '05/11/2016 10:00', '05/11/2016 11:00',
           '05/11/2016 12:00', '05/11/2016 13:00', '05/11/2016 14:00',
           '05/11/2016 15:00', '05/11/2016 16:00', '05/11/2016 17:00',
           '05/11/2016 18:00', '05/11/2016 19:00', '05/11/2016 20:00',
           '05/11/2016 21:00', '05/11/2016 22:00', '05/11/2016 23:00',
           '05/12/2016 00:00', '05/12/2016 01:00', '05/12/2016 02:00',
           '05/12/2016 03:00', '05/12/2016 04:00', '05/12/2016 05:00',
           '05/12/2016 06:00', '05/12/2016 07:00', '05/12/2016 08:00',
           '05/12/2016 09:00', '05/12/2016 10:00', '05/12/2016 11:00',
           '05/12/2016 12:00', '05/12/2016 13:00', '05/12/2016 14:00',
           '05/12/2016 15:00'], dtype=object)




```python
steps.dtypes
```




    Id               int64
    ActivityHour    object
    StepTotal        int64
    dtype: object



ActivityHour needs to be changed to a time


```python
#Convert the column to a pandas datetime format
steps['ActivityHour'] = pd.to_datetime(steps['ActivityHour'], errors='coerce')

# If 'errors' is set to 'coerce', any unparseable dates will be converted to NaT (Not a Time)

# Display the DataFrame to check the converted dates
steps['ActivityHour'].unique()
```




    array(['2016-04-12T00:00:00.000000000', '2016-04-12T01:00:00.000000000',
           '2016-04-12T02:00:00.000000000', '2016-04-12T03:00:00.000000000',
           '2016-04-12T04:00:00.000000000', '2016-04-12T05:00:00.000000000',
           '2016-04-12T06:00:00.000000000', '2016-04-12T07:00:00.000000000',
           '2016-04-12T08:00:00.000000000', '2016-04-12T09:00:00.000000000',
           '2016-04-12T10:00:00.000000000', '2016-04-12T11:00:00.000000000',
           '2016-04-12T12:00:00.000000000', '2016-04-12T13:00:00.000000000',
           '2016-04-12T14:00:00.000000000', '2016-04-12T15:00:00.000000000',
           '2016-04-12T16:00:00.000000000', '2016-04-12T17:00:00.000000000',
           '2016-04-12T18:00:00.000000000', '2016-04-12T19:00:00.000000000',
           '2016-04-12T20:00:00.000000000', '2016-04-12T21:00:00.000000000',
           '2016-04-12T22:00:00.000000000', '2016-04-12T23:00:00.000000000',
           '2016-04-13T00:00:00.000000000', '2016-04-13T01:00:00.000000000',
           '2016-04-13T02:00:00.000000000', '2016-04-13T03:00:00.000000000',
           '2016-04-13T04:00:00.000000000', '2016-04-13T05:00:00.000000000',
           '2016-04-13T06:00:00.000000000', '2016-04-13T07:00:00.000000000',
           '2016-04-13T08:00:00.000000000', '2016-04-13T09:00:00.000000000',
           '2016-04-13T10:00:00.000000000', '2016-04-13T11:00:00.000000000',
           '2016-04-13T12:00:00.000000000', '2016-04-13T13:00:00.000000000',
           '2016-04-13T14:00:00.000000000', '2016-04-13T15:00:00.000000000',
           '2016-04-13T16:00:00.000000000', '2016-04-13T17:00:00.000000000',
           '2016-04-13T18:00:00.000000000', '2016-04-13T19:00:00.000000000',
           '2016-04-13T20:00:00.000000000', '2016-04-13T21:00:00.000000000',
           '2016-04-13T22:00:00.000000000', '2016-04-13T23:00:00.000000000',
           '2016-04-14T00:00:00.000000000', '2016-04-14T01:00:00.000000000',
           '2016-04-14T02:00:00.000000000', '2016-04-14T03:00:00.000000000',
           '2016-04-14T04:00:00.000000000', '2016-04-14T05:00:00.000000000',
           '2016-04-14T06:00:00.000000000', '2016-04-14T07:00:00.000000000',
           '2016-04-14T08:00:00.000000000', '2016-04-14T09:00:00.000000000',
           '2016-04-14T10:00:00.000000000', '2016-04-14T11:00:00.000000000',
           '2016-04-14T12:00:00.000000000', '2016-04-14T13:00:00.000000000',
           '2016-04-14T14:00:00.000000000', '2016-04-14T15:00:00.000000000',
           '2016-04-14T16:00:00.000000000', '2016-04-14T17:00:00.000000000',
           '2016-04-14T18:00:00.000000000', '2016-04-14T19:00:00.000000000',
           '2016-04-14T20:00:00.000000000', '2016-04-14T21:00:00.000000000',
           '2016-04-14T22:00:00.000000000', '2016-04-14T23:00:00.000000000',
           '2016-04-15T00:00:00.000000000', '2016-04-15T01:00:00.000000000',
           '2016-04-15T02:00:00.000000000', '2016-04-15T03:00:00.000000000',
           '2016-04-15T04:00:00.000000000', '2016-04-15T05:00:00.000000000',
           '2016-04-15T06:00:00.000000000', '2016-04-15T07:00:00.000000000',
           '2016-04-15T08:00:00.000000000', '2016-04-15T09:00:00.000000000',
           '2016-04-15T10:00:00.000000000', '2016-04-15T11:00:00.000000000',
           '2016-04-15T12:00:00.000000000', '2016-04-15T13:00:00.000000000',
           '2016-04-15T14:00:00.000000000', '2016-04-15T15:00:00.000000000',
           '2016-04-15T16:00:00.000000000', '2016-04-15T17:00:00.000000000',
           '2016-04-15T18:00:00.000000000', '2016-04-15T19:00:00.000000000',
           '2016-04-15T20:00:00.000000000', '2016-04-15T21:00:00.000000000',
           '2016-04-15T22:00:00.000000000', '2016-04-15T23:00:00.000000000',
           '2016-04-16T00:00:00.000000000', '2016-04-16T01:00:00.000000000',
           '2016-04-16T02:00:00.000000000', '2016-04-16T03:00:00.000000000',
           '2016-04-16T04:00:00.000000000', '2016-04-16T05:00:00.000000000',
           '2016-04-16T06:00:00.000000000', '2016-04-16T07:00:00.000000000',
           '2016-04-16T08:00:00.000000000', '2016-04-16T09:00:00.000000000',
           '2016-04-16T10:00:00.000000000', '2016-04-16T11:00:00.000000000',
           '2016-04-16T12:00:00.000000000', '2016-04-16T13:00:00.000000000',
           '2016-04-16T14:00:00.000000000', '2016-04-16T15:00:00.000000000',
           '2016-04-16T16:00:00.000000000', '2016-04-16T17:00:00.000000000',
           '2016-04-16T18:00:00.000000000', '2016-04-16T19:00:00.000000000',
           '2016-04-16T20:00:00.000000000', '2016-04-16T21:00:00.000000000',
           '2016-04-16T22:00:00.000000000', '2016-04-16T23:00:00.000000000',
           '2016-04-17T00:00:00.000000000', '2016-04-17T01:00:00.000000000',
           '2016-04-17T02:00:00.000000000', '2016-04-17T03:00:00.000000000',
           '2016-04-17T04:00:00.000000000', '2016-04-17T05:00:00.000000000',
           '2016-04-17T06:00:00.000000000', '2016-04-17T07:00:00.000000000',
           '2016-04-17T08:00:00.000000000', '2016-04-17T09:00:00.000000000',
           '2016-04-17T10:00:00.000000000', '2016-04-17T11:00:00.000000000',
           '2016-04-17T12:00:00.000000000', '2016-04-17T13:00:00.000000000',
           '2016-04-17T14:00:00.000000000', '2016-04-17T15:00:00.000000000',
           '2016-04-17T16:00:00.000000000', '2016-04-17T17:00:00.000000000',
           '2016-04-17T18:00:00.000000000', '2016-04-17T19:00:00.000000000',
           '2016-04-17T20:00:00.000000000', '2016-04-17T21:00:00.000000000',
           '2016-04-17T22:00:00.000000000', '2016-04-17T23:00:00.000000000',
           '2016-04-18T00:00:00.000000000', '2016-04-18T01:00:00.000000000',
           '2016-04-18T02:00:00.000000000', '2016-04-18T03:00:00.000000000',
           '2016-04-18T04:00:00.000000000', '2016-04-18T05:00:00.000000000',
           '2016-04-18T06:00:00.000000000', '2016-04-18T07:00:00.000000000',
           '2016-04-18T08:00:00.000000000', '2016-04-18T09:00:00.000000000',
           '2016-04-18T10:00:00.000000000', '2016-04-18T11:00:00.000000000',
           '2016-04-18T12:00:00.000000000', '2016-04-18T13:00:00.000000000',
           '2016-04-18T14:00:00.000000000', '2016-04-18T15:00:00.000000000',
           '2016-04-18T16:00:00.000000000', '2016-04-18T17:00:00.000000000',
           '2016-04-18T18:00:00.000000000', '2016-04-18T19:00:00.000000000',
           '2016-04-18T20:00:00.000000000', '2016-04-18T21:00:00.000000000',
           '2016-04-18T22:00:00.000000000', '2016-04-18T23:00:00.000000000',
           '2016-04-19T00:00:00.000000000', '2016-04-19T01:00:00.000000000',
           '2016-04-19T02:00:00.000000000', '2016-04-19T03:00:00.000000000',
           '2016-04-19T04:00:00.000000000', '2016-04-19T05:00:00.000000000',
           '2016-04-19T06:00:00.000000000', '2016-04-19T07:00:00.000000000',
           '2016-04-19T08:00:00.000000000', '2016-04-19T09:00:00.000000000',
           '2016-04-19T10:00:00.000000000', '2016-04-19T11:00:00.000000000',
           '2016-04-19T12:00:00.000000000', '2016-04-19T13:00:00.000000000',
           '2016-04-19T14:00:00.000000000', '2016-04-19T15:00:00.000000000',
           '2016-04-19T16:00:00.000000000', '2016-04-19T17:00:00.000000000',
           '2016-04-19T18:00:00.000000000', '2016-04-19T19:00:00.000000000',
           '2016-04-19T20:00:00.000000000', '2016-04-19T21:00:00.000000000',
           '2016-04-19T22:00:00.000000000', '2016-04-19T23:00:00.000000000',
           '2016-04-20T00:00:00.000000000', '2016-04-20T01:00:00.000000000',
           '2016-04-20T02:00:00.000000000', '2016-04-20T03:00:00.000000000',
           '2016-04-20T04:00:00.000000000', '2016-04-20T05:00:00.000000000',
           '2016-04-20T06:00:00.000000000', '2016-04-20T07:00:00.000000000',
           '2016-04-20T08:00:00.000000000', '2016-04-20T09:00:00.000000000',
           '2016-04-20T10:00:00.000000000', '2016-04-20T11:00:00.000000000',
           '2016-04-20T12:00:00.000000000', '2016-04-20T13:00:00.000000000',
           '2016-04-20T14:00:00.000000000', '2016-04-20T15:00:00.000000000',
           '2016-04-20T16:00:00.000000000', '2016-04-20T17:00:00.000000000',
           '2016-04-20T18:00:00.000000000', '2016-04-20T19:00:00.000000000',
           '2016-04-20T20:00:00.000000000', '2016-04-20T21:00:00.000000000',
           '2016-04-20T22:00:00.000000000', '2016-04-20T23:00:00.000000000',
           '2016-04-21T00:00:00.000000000', '2016-04-21T01:00:00.000000000',
           '2016-04-21T02:00:00.000000000', '2016-04-21T03:00:00.000000000',
           '2016-04-21T04:00:00.000000000', '2016-04-21T05:00:00.000000000',
           '2016-04-21T06:00:00.000000000', '2016-04-21T07:00:00.000000000',
           '2016-04-21T08:00:00.000000000', '2016-04-21T09:00:00.000000000',
           '2016-04-21T10:00:00.000000000', '2016-04-21T11:00:00.000000000',
           '2016-04-21T12:00:00.000000000', '2016-04-21T13:00:00.000000000',
           '2016-04-21T14:00:00.000000000', '2016-04-21T15:00:00.000000000',
           '2016-04-21T16:00:00.000000000', '2016-04-21T17:00:00.000000000',
           '2016-04-21T18:00:00.000000000', '2016-04-21T19:00:00.000000000',
           '2016-04-21T20:00:00.000000000', '2016-04-21T21:00:00.000000000',
           '2016-04-21T22:00:00.000000000', '2016-04-21T23:00:00.000000000',
           '2016-04-22T00:00:00.000000000', '2016-04-22T01:00:00.000000000',
           '2016-04-22T02:00:00.000000000', '2016-04-22T03:00:00.000000000',
           '2016-04-22T04:00:00.000000000', '2016-04-22T05:00:00.000000000',
           '2016-04-22T06:00:00.000000000', '2016-04-22T07:00:00.000000000',
           '2016-04-22T08:00:00.000000000', '2016-04-22T09:00:00.000000000',
           '2016-04-22T10:00:00.000000000', '2016-04-22T11:00:00.000000000',
           '2016-04-22T12:00:00.000000000', '2016-04-22T13:00:00.000000000',
           '2016-04-22T14:00:00.000000000', '2016-04-22T15:00:00.000000000',
           '2016-04-22T16:00:00.000000000', '2016-04-22T17:00:00.000000000',
           '2016-04-22T18:00:00.000000000', '2016-04-22T19:00:00.000000000',
           '2016-04-22T20:00:00.000000000', '2016-04-22T21:00:00.000000000',
           '2016-04-22T22:00:00.000000000', '2016-04-22T23:00:00.000000000',
           '2016-04-23T00:00:00.000000000', '2016-04-23T01:00:00.000000000',
           '2016-04-23T02:00:00.000000000', '2016-04-23T03:00:00.000000000',
           '2016-04-23T04:00:00.000000000', '2016-04-23T05:00:00.000000000',
           '2016-04-23T06:00:00.000000000', '2016-04-23T07:00:00.000000000',
           '2016-04-23T08:00:00.000000000', '2016-04-23T09:00:00.000000000',
           '2016-04-23T10:00:00.000000000', '2016-04-23T11:00:00.000000000',
           '2016-04-23T12:00:00.000000000', '2016-04-23T13:00:00.000000000',
           '2016-04-23T14:00:00.000000000', '2016-04-23T15:00:00.000000000',
           '2016-04-23T16:00:00.000000000', '2016-04-23T17:00:00.000000000',
           '2016-04-23T18:00:00.000000000', '2016-04-23T19:00:00.000000000',
           '2016-04-23T20:00:00.000000000', '2016-04-23T21:00:00.000000000',
           '2016-04-23T22:00:00.000000000', '2016-04-23T23:00:00.000000000',
           '2016-04-24T00:00:00.000000000', '2016-04-24T01:00:00.000000000',
           '2016-04-24T02:00:00.000000000', '2016-04-24T03:00:00.000000000',
           '2016-04-24T04:00:00.000000000', '2016-04-24T05:00:00.000000000',
           '2016-04-24T06:00:00.000000000', '2016-04-24T07:00:00.000000000',
           '2016-04-24T08:00:00.000000000', '2016-04-24T09:00:00.000000000',
           '2016-04-24T10:00:00.000000000', '2016-04-24T11:00:00.000000000',
           '2016-04-24T12:00:00.000000000', '2016-04-24T13:00:00.000000000',
           '2016-04-24T14:00:00.000000000', '2016-04-24T15:00:00.000000000',
           '2016-04-24T16:00:00.000000000', '2016-04-24T17:00:00.000000000',
           '2016-04-24T18:00:00.000000000', '2016-04-24T19:00:00.000000000',
           '2016-04-24T20:00:00.000000000', '2016-04-24T21:00:00.000000000',
           '2016-04-24T22:00:00.000000000', '2016-04-24T23:00:00.000000000',
           '2016-04-25T00:00:00.000000000', '2016-04-25T01:00:00.000000000',
           '2016-04-25T02:00:00.000000000', '2016-04-25T03:00:00.000000000',
           '2016-04-25T04:00:00.000000000', '2016-04-25T05:00:00.000000000',
           '2016-04-25T06:00:00.000000000', '2016-04-25T07:00:00.000000000',
           '2016-04-25T08:00:00.000000000', '2016-04-25T09:00:00.000000000',
           '2016-04-25T10:00:00.000000000', '2016-04-25T11:00:00.000000000',
           '2016-04-25T12:00:00.000000000', '2016-04-25T13:00:00.000000000',
           '2016-04-25T14:00:00.000000000', '2016-04-25T15:00:00.000000000',
           '2016-04-25T16:00:00.000000000', '2016-04-25T17:00:00.000000000',
           '2016-04-25T18:00:00.000000000', '2016-04-25T19:00:00.000000000',
           '2016-04-25T20:00:00.000000000', '2016-04-25T21:00:00.000000000',
           '2016-04-25T22:00:00.000000000', '2016-04-25T23:00:00.000000000',
           '2016-04-26T00:00:00.000000000', '2016-04-26T01:00:00.000000000',
           '2016-04-26T02:00:00.000000000', '2016-04-26T03:00:00.000000000',
           '2016-04-26T04:00:00.000000000', '2016-04-26T05:00:00.000000000',
           '2016-04-26T06:00:00.000000000', '2016-04-26T07:00:00.000000000',
           '2016-04-26T08:00:00.000000000', '2016-04-26T09:00:00.000000000',
           '2016-04-26T10:00:00.000000000', '2016-04-26T11:00:00.000000000',
           '2016-04-26T12:00:00.000000000', '2016-04-26T13:00:00.000000000',
           '2016-04-26T14:00:00.000000000', '2016-04-26T15:00:00.000000000',
           '2016-04-26T16:00:00.000000000', '2016-04-26T17:00:00.000000000',
           '2016-04-26T18:00:00.000000000', '2016-04-26T19:00:00.000000000',
           '2016-04-26T20:00:00.000000000', '2016-04-26T21:00:00.000000000',
           '2016-04-26T22:00:00.000000000', '2016-04-26T23:00:00.000000000',
           '2016-04-27T00:00:00.000000000', '2016-04-27T01:00:00.000000000',
           '2016-04-27T02:00:00.000000000', '2016-04-27T03:00:00.000000000',
           '2016-04-27T04:00:00.000000000', '2016-04-27T05:00:00.000000000',
           '2016-04-27T06:00:00.000000000', '2016-04-27T07:00:00.000000000',
           '2016-04-27T08:00:00.000000000', '2016-04-27T09:00:00.000000000',
           '2016-04-27T10:00:00.000000000', '2016-04-27T11:00:00.000000000',
           '2016-04-27T12:00:00.000000000', '2016-04-27T13:00:00.000000000',
           '2016-04-27T14:00:00.000000000', '2016-04-27T15:00:00.000000000',
           '2016-04-27T16:00:00.000000000', '2016-04-27T17:00:00.000000000',
           '2016-04-27T18:00:00.000000000', '2016-04-27T19:00:00.000000000',
           '2016-04-27T20:00:00.000000000', '2016-04-27T21:00:00.000000000',
           '2016-04-27T22:00:00.000000000', '2016-04-27T23:00:00.000000000',
           '2016-04-28T00:00:00.000000000', '2016-04-28T01:00:00.000000000',
           '2016-04-28T02:00:00.000000000', '2016-04-28T03:00:00.000000000',
           '2016-04-28T04:00:00.000000000', '2016-04-28T05:00:00.000000000',
           '2016-04-28T06:00:00.000000000', '2016-04-28T07:00:00.000000000',
           '2016-04-28T08:00:00.000000000', '2016-04-28T09:00:00.000000000',
           '2016-04-28T10:00:00.000000000', '2016-04-28T11:00:00.000000000',
           '2016-04-28T12:00:00.000000000', '2016-04-28T13:00:00.000000000',
           '2016-04-28T14:00:00.000000000', '2016-04-28T15:00:00.000000000',
           '2016-04-28T16:00:00.000000000', '2016-04-28T17:00:00.000000000',
           '2016-04-28T18:00:00.000000000', '2016-04-28T19:00:00.000000000',
           '2016-04-28T20:00:00.000000000', '2016-04-28T21:00:00.000000000',
           '2016-04-28T22:00:00.000000000', '2016-04-28T23:00:00.000000000',
           '2016-04-29T00:00:00.000000000', '2016-04-29T01:00:00.000000000',
           '2016-04-29T02:00:00.000000000', '2016-04-29T03:00:00.000000000',
           '2016-04-29T04:00:00.000000000', '2016-04-29T05:00:00.000000000',
           '2016-04-29T06:00:00.000000000', '2016-04-29T07:00:00.000000000',
           '2016-04-29T08:00:00.000000000', '2016-04-29T09:00:00.000000000',
           '2016-04-29T10:00:00.000000000', '2016-04-29T11:00:00.000000000',
           '2016-04-29T12:00:00.000000000', '2016-04-29T13:00:00.000000000',
           '2016-04-29T14:00:00.000000000', '2016-04-29T15:00:00.000000000',
           '2016-04-29T16:00:00.000000000', '2016-04-29T17:00:00.000000000',
           '2016-04-29T18:00:00.000000000', '2016-04-29T19:00:00.000000000',
           '2016-04-29T20:00:00.000000000', '2016-04-29T21:00:00.000000000',
           '2016-04-29T22:00:00.000000000', '2016-04-29T23:00:00.000000000',
           '2016-04-30T00:00:00.000000000', '2016-04-30T01:00:00.000000000',
           '2016-04-30T02:00:00.000000000', '2016-04-30T03:00:00.000000000',
           '2016-04-30T04:00:00.000000000', '2016-04-30T05:00:00.000000000',
           '2016-04-30T06:00:00.000000000', '2016-04-30T07:00:00.000000000',
           '2016-04-30T08:00:00.000000000', '2016-04-30T09:00:00.000000000',
           '2016-04-30T10:00:00.000000000', '2016-04-30T11:00:00.000000000',
           '2016-04-30T12:00:00.000000000', '2016-04-30T13:00:00.000000000',
           '2016-04-30T14:00:00.000000000', '2016-04-30T15:00:00.000000000',
           '2016-04-30T16:00:00.000000000', '2016-04-30T17:00:00.000000000',
           '2016-04-30T18:00:00.000000000', '2016-04-30T19:00:00.000000000',
           '2016-04-30T20:00:00.000000000', '2016-04-30T21:00:00.000000000',
           '2016-04-30T22:00:00.000000000', '2016-04-30T23:00:00.000000000',
           '2016-05-01T00:00:00.000000000', '2016-05-01T01:00:00.000000000',
           '2016-05-01T02:00:00.000000000', '2016-05-01T03:00:00.000000000',
           '2016-05-01T04:00:00.000000000', '2016-05-01T05:00:00.000000000',
           '2016-05-01T06:00:00.000000000', '2016-05-01T07:00:00.000000000',
           '2016-05-01T08:00:00.000000000', '2016-05-01T09:00:00.000000000',
           '2016-05-01T10:00:00.000000000', '2016-05-01T11:00:00.000000000',
           '2016-05-01T12:00:00.000000000', '2016-05-01T13:00:00.000000000',
           '2016-05-01T14:00:00.000000000', '2016-05-01T15:00:00.000000000',
           '2016-05-01T16:00:00.000000000', '2016-05-01T17:00:00.000000000',
           '2016-05-01T18:00:00.000000000', '2016-05-01T19:00:00.000000000',
           '2016-05-01T20:00:00.000000000', '2016-05-01T21:00:00.000000000',
           '2016-05-01T22:00:00.000000000', '2016-05-01T23:00:00.000000000',
           '2016-05-02T00:00:00.000000000', '2016-05-02T01:00:00.000000000',
           '2016-05-02T02:00:00.000000000', '2016-05-02T03:00:00.000000000',
           '2016-05-02T04:00:00.000000000', '2016-05-02T05:00:00.000000000',
           '2016-05-02T06:00:00.000000000', '2016-05-02T07:00:00.000000000',
           '2016-05-02T08:00:00.000000000', '2016-05-02T09:00:00.000000000',
           '2016-05-02T10:00:00.000000000', '2016-05-02T11:00:00.000000000',
           '2016-05-02T12:00:00.000000000', '2016-05-02T13:00:00.000000000',
           '2016-05-02T14:00:00.000000000', '2016-05-02T15:00:00.000000000',
           '2016-05-02T16:00:00.000000000', '2016-05-02T17:00:00.000000000',
           '2016-05-02T18:00:00.000000000', '2016-05-02T19:00:00.000000000',
           '2016-05-02T20:00:00.000000000', '2016-05-02T21:00:00.000000000',
           '2016-05-02T22:00:00.000000000', '2016-05-02T23:00:00.000000000',
           '2016-05-03T00:00:00.000000000', '2016-05-03T01:00:00.000000000',
           '2016-05-03T02:00:00.000000000', '2016-05-03T03:00:00.000000000',
           '2016-05-03T04:00:00.000000000', '2016-05-03T05:00:00.000000000',
           '2016-05-03T06:00:00.000000000', '2016-05-03T07:00:00.000000000',
           '2016-05-03T08:00:00.000000000', '2016-05-03T09:00:00.000000000',
           '2016-05-03T10:00:00.000000000', '2016-05-03T11:00:00.000000000',
           '2016-05-03T12:00:00.000000000', '2016-05-03T13:00:00.000000000',
           '2016-05-03T14:00:00.000000000', '2016-05-03T15:00:00.000000000',
           '2016-05-03T16:00:00.000000000', '2016-05-03T17:00:00.000000000',
           '2016-05-03T18:00:00.000000000', '2016-05-03T19:00:00.000000000',
           '2016-05-03T20:00:00.000000000', '2016-05-03T21:00:00.000000000',
           '2016-05-03T22:00:00.000000000', '2016-05-03T23:00:00.000000000',
           '2016-05-04T00:00:00.000000000', '2016-05-04T01:00:00.000000000',
           '2016-05-04T02:00:00.000000000', '2016-05-04T03:00:00.000000000',
           '2016-05-04T04:00:00.000000000', '2016-05-04T05:00:00.000000000',
           '2016-05-04T06:00:00.000000000', '2016-05-04T07:00:00.000000000',
           '2016-05-04T08:00:00.000000000', '2016-05-04T09:00:00.000000000',
           '2016-05-04T10:00:00.000000000', '2016-05-04T11:00:00.000000000',
           '2016-05-04T12:00:00.000000000', '2016-05-04T13:00:00.000000000',
           '2016-05-04T14:00:00.000000000', '2016-05-04T15:00:00.000000000',
           '2016-05-04T16:00:00.000000000', '2016-05-04T17:00:00.000000000',
           '2016-05-04T18:00:00.000000000', '2016-05-04T19:00:00.000000000',
           '2016-05-04T20:00:00.000000000', '2016-05-04T21:00:00.000000000',
           '2016-05-04T22:00:00.000000000', '2016-05-04T23:00:00.000000000',
           '2016-05-05T00:00:00.000000000', '2016-05-05T01:00:00.000000000',
           '2016-05-05T02:00:00.000000000', '2016-05-05T03:00:00.000000000',
           '2016-05-05T04:00:00.000000000', '2016-05-05T05:00:00.000000000',
           '2016-05-05T06:00:00.000000000', '2016-05-05T07:00:00.000000000',
           '2016-05-05T08:00:00.000000000', '2016-05-05T09:00:00.000000000',
           '2016-05-05T10:00:00.000000000', '2016-05-05T11:00:00.000000000',
           '2016-05-05T12:00:00.000000000', '2016-05-05T13:00:00.000000000',
           '2016-05-05T14:00:00.000000000', '2016-05-05T15:00:00.000000000',
           '2016-05-05T16:00:00.000000000', '2016-05-05T17:00:00.000000000',
           '2016-05-05T18:00:00.000000000', '2016-05-05T19:00:00.000000000',
           '2016-05-05T20:00:00.000000000', '2016-05-05T21:00:00.000000000',
           '2016-05-05T22:00:00.000000000', '2016-05-05T23:00:00.000000000',
           '2016-05-06T00:00:00.000000000', '2016-05-06T01:00:00.000000000',
           '2016-05-06T02:00:00.000000000', '2016-05-06T03:00:00.000000000',
           '2016-05-06T04:00:00.000000000', '2016-05-06T05:00:00.000000000',
           '2016-05-06T06:00:00.000000000', '2016-05-06T07:00:00.000000000',
           '2016-05-06T08:00:00.000000000', '2016-05-06T09:00:00.000000000',
           '2016-05-06T10:00:00.000000000', '2016-05-06T11:00:00.000000000',
           '2016-05-06T12:00:00.000000000', '2016-05-06T13:00:00.000000000',
           '2016-05-06T14:00:00.000000000', '2016-05-06T15:00:00.000000000',
           '2016-05-06T16:00:00.000000000', '2016-05-06T17:00:00.000000000',
           '2016-05-06T18:00:00.000000000', '2016-05-06T19:00:00.000000000',
           '2016-05-06T20:00:00.000000000', '2016-05-06T21:00:00.000000000',
           '2016-05-06T22:00:00.000000000', '2016-05-06T23:00:00.000000000',
           '2016-05-07T00:00:00.000000000', '2016-05-07T01:00:00.000000000',
           '2016-05-07T02:00:00.000000000', '2016-05-07T03:00:00.000000000',
           '2016-05-07T04:00:00.000000000', '2016-05-07T05:00:00.000000000',
           '2016-05-07T06:00:00.000000000', '2016-05-07T07:00:00.000000000',
           '2016-05-07T08:00:00.000000000', '2016-05-07T09:00:00.000000000',
           '2016-05-07T10:00:00.000000000', '2016-05-07T11:00:00.000000000',
           '2016-05-07T12:00:00.000000000', '2016-05-07T13:00:00.000000000',
           '2016-05-07T14:00:00.000000000', '2016-05-07T15:00:00.000000000',
           '2016-05-07T16:00:00.000000000', '2016-05-07T17:00:00.000000000',
           '2016-05-07T18:00:00.000000000', '2016-05-07T19:00:00.000000000',
           '2016-05-07T20:00:00.000000000', '2016-05-07T21:00:00.000000000',
           '2016-05-07T22:00:00.000000000', '2016-05-07T23:00:00.000000000',
           '2016-05-08T00:00:00.000000000', '2016-05-08T01:00:00.000000000',
           '2016-05-08T02:00:00.000000000', '2016-05-08T03:00:00.000000000',
           '2016-05-08T04:00:00.000000000', '2016-05-08T05:00:00.000000000',
           '2016-05-08T06:00:00.000000000', '2016-05-08T07:00:00.000000000',
           '2016-05-08T08:00:00.000000000', '2016-05-08T09:00:00.000000000',
           '2016-05-08T10:00:00.000000000', '2016-05-08T11:00:00.000000000',
           '2016-05-08T12:00:00.000000000', '2016-05-08T13:00:00.000000000',
           '2016-05-08T14:00:00.000000000', '2016-05-08T15:00:00.000000000',
           '2016-05-08T16:00:00.000000000', '2016-05-08T17:00:00.000000000',
           '2016-05-08T18:00:00.000000000', '2016-05-08T19:00:00.000000000',
           '2016-05-08T20:00:00.000000000', '2016-05-08T21:00:00.000000000',
           '2016-05-08T22:00:00.000000000', '2016-05-08T23:00:00.000000000',
           '2016-05-09T00:00:00.000000000', '2016-05-09T01:00:00.000000000',
           '2016-05-09T02:00:00.000000000', '2016-05-09T03:00:00.000000000',
           '2016-05-09T04:00:00.000000000', '2016-05-09T05:00:00.000000000',
           '2016-05-09T06:00:00.000000000', '2016-05-09T07:00:00.000000000',
           '2016-05-09T08:00:00.000000000', '2016-05-09T09:00:00.000000000',
           '2016-05-09T10:00:00.000000000', '2016-05-09T11:00:00.000000000',
           '2016-05-09T12:00:00.000000000', '2016-05-09T13:00:00.000000000',
           '2016-05-09T14:00:00.000000000', '2016-05-09T15:00:00.000000000',
           '2016-05-09T16:00:00.000000000', '2016-05-09T17:00:00.000000000',
           '2016-05-09T18:00:00.000000000', '2016-05-09T19:00:00.000000000',
           '2016-05-09T20:00:00.000000000', '2016-05-09T21:00:00.000000000',
           '2016-05-09T22:00:00.000000000', '2016-05-09T23:00:00.000000000',
           '2016-05-10T00:00:00.000000000', '2016-05-10T01:00:00.000000000',
           '2016-05-10T02:00:00.000000000', '2016-05-10T03:00:00.000000000',
           '2016-05-10T04:00:00.000000000', '2016-05-10T05:00:00.000000000',
           '2016-05-10T06:00:00.000000000', '2016-05-10T07:00:00.000000000',
           '2016-05-10T08:00:00.000000000', '2016-05-10T09:00:00.000000000',
           '2016-05-10T10:00:00.000000000', '2016-05-10T11:00:00.000000000',
           '2016-05-10T12:00:00.000000000', '2016-05-10T13:00:00.000000000',
           '2016-05-10T14:00:00.000000000', '2016-05-10T15:00:00.000000000',
           '2016-05-10T16:00:00.000000000', '2016-05-10T17:00:00.000000000',
           '2016-05-10T18:00:00.000000000', '2016-05-10T19:00:00.000000000',
           '2016-05-10T20:00:00.000000000', '2016-05-10T21:00:00.000000000',
           '2016-05-10T22:00:00.000000000', '2016-05-10T23:00:00.000000000',
           '2016-05-11T00:00:00.000000000', '2016-05-11T01:00:00.000000000',
           '2016-05-11T02:00:00.000000000', '2016-05-11T03:00:00.000000000',
           '2016-05-11T04:00:00.000000000', '2016-05-11T05:00:00.000000000',
           '2016-05-11T06:00:00.000000000', '2016-05-11T07:00:00.000000000',
           '2016-05-11T08:00:00.000000000', '2016-05-11T09:00:00.000000000',
           '2016-05-11T10:00:00.000000000', '2016-05-11T11:00:00.000000000',
           '2016-05-11T12:00:00.000000000', '2016-05-11T13:00:00.000000000',
           '2016-05-11T14:00:00.000000000', '2016-05-11T15:00:00.000000000',
           '2016-05-11T16:00:00.000000000', '2016-05-11T17:00:00.000000000',
           '2016-05-11T18:00:00.000000000', '2016-05-11T19:00:00.000000000',
           '2016-05-11T20:00:00.000000000', '2016-05-11T21:00:00.000000000',
           '2016-05-11T22:00:00.000000000', '2016-05-11T23:00:00.000000000',
           '2016-05-12T00:00:00.000000000', '2016-05-12T01:00:00.000000000',
           '2016-05-12T02:00:00.000000000', '2016-05-12T03:00:00.000000000',
           '2016-05-12T04:00:00.000000000', '2016-05-12T05:00:00.000000000',
           '2016-05-12T06:00:00.000000000', '2016-05-12T07:00:00.000000000',
           '2016-05-12T08:00:00.000000000', '2016-05-12T09:00:00.000000000',
           '2016-05-12T10:00:00.000000000', '2016-05-12T11:00:00.000000000',
           '2016-05-12T12:00:00.000000000', '2016-05-12T13:00:00.000000000',
           '2016-05-12T14:00:00.000000000', '2016-05-12T15:00:00.000000000'],
          dtype='datetime64[ns]')




```python
# Extract the hour from the datetime column and add it as a new column
steps['hour'] = steps['ActivityHour'].dt.hour

steps['hour'].unique()
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19, 20, 21, 22, 23], dtype=int64)




```python
steps.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Id</th>
      <th>ActivityHour</th>
      <th>StepTotal</th>
      <th>hour</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1503960366</td>
      <td>2016-04-12 00:00:00</td>
      <td>373</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1503960366</td>
      <td>2016-04-12 01:00:00</td>
      <td>160</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1503960366</td>
      <td>2016-04-12 02:00:00</td>
      <td>151</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1503960366</td>
      <td>2016-04-12 03:00:00</td>
      <td>0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1503960366</td>
      <td>2016-04-12 04:00:00</td>
      <td>0</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
average_steps_per_hour = steps.groupby(['Id', 'hour'])['StepTotal'].mean().reset_index()

# Create the graph using seaborn
plt.figure(figsize=(10, 6))
sns.lineplot(x='hour', y='StepTotal', hue='Id', data=average_steps_per_hour, markers=True, dashes=False)
plt.xlabel('Hour')
plt.ylabel('Average Total Steps')
plt.title('Average Total Steps per Hour for each Id')
plt.legend(title='Id', loc='upper right')
plt.tight_layout()
plt.show()
```


    
![Line graph](https://github.com/JonathanSmith11/JSmith_Portfolio/raw/main/images/DA - Line graph 1.png)
    


## Insights:

    - This shows that there are usual peaks around 7-8am which could be due to commuting.
    - Usual peaks at lunch time.
    - Surprisingly a peak at 7pm which could be some real exercise activity.

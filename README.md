# SurfsUp_Analysis

## Overview

While vacationing in Hawaii, the idea of living there came up. In order to make it become a fullproof plan, a business is required. A Surf and Shake shop serving surfboards and ice cream to locals and tourists could be the way to do it. There are some initial savings that could help get this plan going, however further investments are needed. W. Avy is a potential investor, who is famous for his love of surfing. W. Avy is interested, yet is concerned with the weather. Based on his past experiences, he had set up a similar store, yet had not researched weather patterns, and was rained out of existence. W. Avy has asked if weather data anslysis can be conducted from the very island he is from, Awahoo, and has provided the necessary data.

## Deliverable 1: Determine the Summary Statistics for June

A query was written to filter through the 'Measurement' table, in the 'hawaii.sqlite' database, to retrieve all the temperatures for the month of June. It utilized the extract function by determining that we are looking for the sixth month specifically.

```
june_tobs = session.query(Measurement.date, Measurement.tobs).filter(extract('month', Measurement.date) == 6).all()
```

The extracted temperature data was then input into a list, then into a dataframe, and with all the information stored neatly in the dataframe, a statistical analysis can be conducted using the describe function. The statistical summary appears as so:

![June_Temps_Describe](https://user-images.githubusercontent.com/111096246/197407941-0fe3350c-8c58-4d90-8cbe-fa986d12ae69.PNG)

From the table we can interpret the following: There are 1,700 measurements of temperature data for all the dates in the month of June from 2010 to 2017. The average temperature throughout all the Junes is 74.94 °F (23.86 °C). The lowest temperature recorded was 64.00 °F (17.78 °C). The highest temperature recorded was 85.00 °F (29.44 °C).

## Deliverable 2: Determine the Summary Statistics for December

Another query was conducted in a similar fashion to the previous one, however this time the month in question is December. By modifying the initial query to reference the twelfth month instead of the sixth, as seen below:

```
dec_tobs =session.query(Measurement.date, Measurement.tobs).filter(extract('month', Measurement.date) == 12).all()
```

The same procedure was applied to this extracted data. Converted to a list, then a dataframe, and the using the describe function to obtain the summary statistics, as seen below:

![Dec_Temps_Describe](https://user-images.githubusercontent.com/111096246/197408258-63dcdb0a-1e19-4670-876e-05e46cc3667f.PNG)

From this table we can interpret the following: There are 1,517 measurements of temperature data for all the dates in the month of December from 2010 to 2017. The average temperature throughout all the Decembers is 71.04 °F (21.69 °C), which is only a mere couple of degrees lower than June. The lowest temperature recorded was 56.00 °F (13.33 °C). The highest temperature recorded was 83.00 °F (28.33 °C).

## Analysis

Based on the previous data, we can now compare the temperature differences from what is supposed to be one of the most warmer months, and one of the most colder months, and see how six months passing affects the temperature:

![Temp_Diff](https://user-images.githubusercontent.com/111096246/197408919-e22e01a1-a17f-44cf-8e07-b2376892715e.PNG)

From the table of differences we can deduct the following:
- There was a drop of 3.90 °F (2.17 °C) between the average temperatures of all the June measurements and all the December measurements.
- There was a drop of 8.00 °F (4.44 °C) between the minimum temperatures of all the June measurements and all the December measurements.
- There was a drop of 2.00 °F (1.11 °C) between the maximum temperatures of all the June measurements and all the December measurements.

## Deliverable 3: Additional queries

In order to gather further weather data for June and December, another two queries were created. This time it would be to gather the levels of precipitation throughout all the measurements, just as before. The query is similart to the ones used to gather the temperature, as we are changing which column to gather the data from.

```
june_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 6).all()
```

Following the same steps as before, regarding the creation of a list and dataframe, the summary statistics for the levels of precipitation in the months of June are as follows:

![June_Precipitation_Describe](https://user-images.githubusercontent.com/111096246/197409233-7874b37a-6855-4f18-928b-41fc238cc8ee.PNG)

Where there are 1,574 measurements taken of precipitation. The average amount of rain was 0.14". The minimum amount of rain was 0.00", when it did not rain. The maximum amount of rain was 4.43".

The same query was run for the month of December using the previous query, but modified to filter for the month of December.

```
dec_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 12).all()
```

Applying the same methodology as all the prior summary statistics table, the output is as follows:

![Dec_Precipitation_Describe](https://user-images.githubusercontent.com/111096246/197409551-3daff62f-3a5d-492c-8b90-8fd65ec0c346.PNG)

Where there are 1,405 measurements taken of precipitation. The average amount of rain was 0.22". The minimum amount of rain was 0.00", when it did not rain. The maximum amount of rain was 6.42".

## Analysis

Taking the previous precipitation data, and comparing it we can determine what the precipiation differences are between all the measurement in June, and all the measurements in December.

![Precipitation_Diff](https://user-images.githubusercontent.com/111096246/197409804-10018bf5-1cb4-4ddf-a990-fb1c7a081b4d.PNG)

From the table of differences we can deduct the following:
- There was an increase of 0.08" of rain between the average precipitation levels of all the June measurements and all the December measurements.
- There was no difference in rain levels, as both are measurements taken when there was no rain recorded.
- There was an increase of 1.99" of rain between the maximum precipitation levels of all the June measurements and all the December measurements.

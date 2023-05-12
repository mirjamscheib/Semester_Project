# Proposal for Semester Project

**Patterns & Trends in Environmental Data / Computational Movement
Analysis Geo 880**

| Semester:      | FS23                                     |
|:---------------|:---------------------------------------- |
| **Data:**      | Trajectory data, weather data            | 
| **Title:**     | Effects of environmental factors on spatio-temporal movement patterns of students                |
| **Student 1:** | Mirjam Scheib                            |
| **Student 2:** | Miriam Steinhauer                        |

## Abstract 
<!-- (50-60 words) -->
In this study, we will address movement efficiency by investigating the effects of environmental factors (e.g., weather condition, influence of weekday, university affiliation) on average travelling distance of students, with the aim to reveal spatial and temporal patterns. 

## Research Questions 
Based on trajectory data from 20 students using the Posmo Project App we attempt to answer the following research questions: 

- Do students of different universities (ZHAW or UZH) show different spatio-temporal movement patterns?
- Does the day of the week (weekend vs. workday) have an impact on spatio-temporal movement patterns? 
- Does the weather condition (e.g. rain, sunshine) impact spatio-temporal patterns of students by foot and/or bicycle?  

<!-- (50-60 words) -->

## Results / products 
We expect that spatio-temporal movement patterns between students of different universities differ, as ZHAW Wädenswil is located more remote, and the average student probably has to travel a greater distance to come to the campus compared to UZH, which is located relatively central in the city of Zurich. Additionally, Zurich is considered the biggest student city in Switzerland, with around 45'000 students (https://www.einstieg.com/studium/studium-im-ausland/studieren-in-der-schweiz.html). Therefore we expect that students of UZH will have a lower average travelling distance per day as students of ZHAW, as we assume that many students of UZH life in close proximity of the university or the city of Zurich in general. 

We expect that spatio-temporal movement patterns differs when comparing the weekends to workdays, as commuting is a major part of workdays which probably adds up to travelling distance. Hence, we expect to find a higher average travelling distance on workdays than on weekends. 

We expect that the weather condition has an impact on spatio-temporal movement patterns by foot and/or bicycle of students. On rainy days average travel distance by foot and/or bicycle will be lower than on days with sunshine. Additionally, we expect to find a lower average travel distance over all travel modes on rainy days, compared to sunny days. 

<!-- What do you expect, anticipate? -->

## Data 
**What data will you use?**

Primary data to answer the research questions is the trajectory data from 20 students, which covers a timeframe of one to two months (ca. 01.04.23 until 31.05.23). The data was collected using the Posmo App, which only tracks activity events and differentiates between several travel modes (e.g. car, bicycle, foot, train, other....). Trajectory data from the App can be downloaded as a .csv-file containing the following attributes: 
-   **user_id:** entails the individual ID of the user (= student) (type: *character*)
-   **datetime:** date and time when a position of a user is tracked (type: *datetime*) 
-   **weekday:** abbreviated name of the weekday (e.g. Mon = Monday) (type: *character*)
-   **place_name:** names of a place, in which a user is at a specific time (type: *character*)
-   **transport_mode:** the type of transport used by a user (e.g. car, bicycle, foot, train, other....) (type: *character*)
-   **lon_x/lat_y:** coordinates of the user at a specific time (type: *numeric*)

**Will you require additional context data?**

Additional context data needed to answer the research questions is the type of university, in which the participating students are enrolled, which is either ZHAW or UZH (type: *character* or *factor*). Additionally, to answer the second question, weather data from weather stations are required, containing information from which a clustering of different weather modes can be obtained (e.g. rain, sunshine, wind). 

**Where do you get this data from?** 

The data containing the type of university of every student can be obtained from the information in the moodle course. Weather data from weather stations can be accessed through the internet on different data bases. 

**Do you already have all the data?**

Data from weather stations still have to be obtained, as it remains challenging choosing the right weather station and where to find the weather data exactly. 

## Analytical concepts 
<!-- Which analytical concepts will you use? What conceptual movement spaces and respective modelling approaches of trajectories will you be using? What additional spatial analysis methods will you be using? -->

Our movement data is tracked in a continuous movement space (the whole earth surface) and the best suitable conceptual model is probably a network space combined with an entity-based model. Our data structure is vector based so that we can obtain trajectories in a two-dimensional space where movement can be constrained by objects (e.g., houses) and movement corridors like streets and train tracks. The movement takes place in an intermittent manner and can be active (by foot) or passive (by train, boat). As all students have been tracked actively and in real-time by the posmo app (every 5s, 10s, or 15s) or by a GPS tracker, the perspective is Lagranian with a continuous sampling regime. 

Based on our research questions we are mainly interested in the average travelling distances of the students. Therefore, our semantic level of interest concerns only the segments of each trajectory. As a first step, the raw data must be inspected and pre-processed. We will start by getting an overview of our data by visualizing it in different ways and thereby also detect possible measurement errors, gaps and outliers that can be excluded as a next step. A map matching will help to detect low GPS accuracy or precision, where for this study the ladder is more relevant and could have a high impact on our results.

We might also calculate the sinuosity [s] as the chance of underestimating average travelling distance gets higher, the finer scale our data is in combination with a high sinuosity. The sinuosity measure in addition to a cross-scale movement analysis will help finding the suitable scale and granularity to calculate travelling distances. 

Once the pre-processing is done, we can proceed to computing our trajectory segments in the following four steps: a) specify a temporal window v, b) measure the distance from every point to every other point within this temporal window v, c) define a distance threshold between points below which the movement is defined as “static” and remove all static points and d) assign all segments with an individual ID. As a next step we might include a similarity measure between all trajectories to be able to detect possible patterns derived by effects of university affiliations, days of the week, and weather conditions. Furthermore, possible artifacts will be excluded by processing the segments.

As a last step, the length of all segments of a trajectory needs to be added up as a baseline for further comparison of average travelling distances and their dependences on other factors like weather condition. By filtering the dataset, average travelling distances per factor (for example student and weekday) can be calculated. To find possible effects of the weather condition on average travelling distances, the weather data must be categorized, so that comparisons of average travelling distances per weather category can be made. 

## R concepts 
The following R concepts, functions and packages we expect to mainly use in this project work: 

**1. Spatial data handling**:
Trajectory data contains spatial information (coordinates). Additionally, weather data may be available as raster data, which requires special handling in R. 

*Packages and functions:*

- **sf** - for spatial data analysis
  -   st_as_sf() - to convert data.frame into spatial object 
  -   st_transform() - to transform coordinate systems 
- **terra** - to handle raster data 
  -  rast() - to read rasters

**2. Data manipulation and transformation**:
Our data most probably needs to be manipulated and transformed in various ways. 

*Packages and functions:*

- **dplyr** - for data wrangling and filtering
  -   group_by() - to group data (e.g. according to university, travel mode, weekday or weekend etc.)
  -   summarise() - to summarise intermediate results into another table 
  -   filter() - to filter data 
  -   mutate() - to calculate variables from existing variables and/or to create additional variables
-  **tidyr** 
-  **readr** - to import tabular data (e.g. .csv)
  -   read_delim() - to import tabular data
  
**3. Visualization**:
Visualization allows to explore patterns and trends in the data. 

*Packages and functions:*

- **tmap** - for creating interactive maps
  -   tmshape() + shape argument - to create interactive maps 
- **ggplot2** - for creating visualizations
  - ggplot() + - with several geom_functions combined (e.g. geom_path(), geom_point() etc.)


**4. Spatial analysis**:
Trajectory data can be analyzed using various spatial analysis techniques (e.g. clustering).

*Packages and functions:*

- The spatstat, trip, and gdistance packages are commonly used for spatial analysis in R.

**5. Time series analysis**:
Both trajectory data and weather data are collected over time, and require time series analysis techniques to understand temporal patterns and trends.

*Packages and functions:*

- The zoo, xts, and forecast packages are commonly used for time series analysis in R.

**6. Data merging**:
Combining trajectory data with weather data requires merging the two datasets based on a common variable (e.g. time, location).

*Packages and functions:*

- **dplyr** - for data wrangling and filtering
  -   group_by() - to group data (e.g. according to university, travel mode, weekday or weekend etc.)
  -   summarise() - to summarise intermediate results into another table 
  -   filter() - to filter data 
  -   mutate() - to calculate variables from existing variables and/or to create additional variables 
-   **tidyr**

<!-- Which R concepts, functions, packages will you mainly use. What additional spatial analysis methods will you be using? -->

## Risk analysis 
The biggest challenges/problems probably occur with obtaining, handling and analysing the weather data. If not sufficient weather data is available (meaning not every movement space of all students can be covered), it would be possible to filter our data so that only trajectories within sufficient weather data coverage will be analysed. 

From an analytical point of view, outliers and artifacts could skew data drastically if removal is unsuccessful. Furthermore, the sampling frequency is very fine scale for our chosen research questions, if granularity is too high, short forward movements could be detected as stationary, leading to an underestimation of the total trajectory distance. 

Additionally it was brought to our attention, that tracking accuracy of the Posmo App is not always right, as travel modes can be misinterpreted (e.g., instead of tracking a trajectory made by bicycle Posmo tracks a trajectory made with a car). Furthermode it can be that movement data is either tracked where no movement took place or movement data is not being tracked where movement took place. It would  be probably very complicated to filter out these errors, as we don't have additional data covering real movement of all students to correct the Posmo App data. Therefore, our procedure would be to use the trajectory data as it is and discuss these limitations and problems of the App in the discussion of our project work. 

<!-- What could be the biggest challenges/problems you might face? What is your plan B? -->

## Questions? 
- How, where can we access weather data which meets the needs of our analysis? 
- How to handle/communicate the inherent uncertainty of the Posmo Data (since we know that the App doesn't track activity data right every time)?
<!-- Which questions would you like to discuss at the coaching session? -->

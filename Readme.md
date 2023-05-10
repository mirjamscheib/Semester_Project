# Proposal for Semester Project

**Patterns & Trends in Environmental Data / Computational Movement
Analysis Geo 880**

| Semester:      | FS23                                     |
|:---------------|:---------------------------------------- |
| **Data:**      | Trajectory data, weather data            | 
| **Title:**     | Effects of ... on average travelling distances of students                |
| **Student 1:** | Mirjam Scheib                            |
| **Student 2:** | Miriam Steinhauer                        |

## Abstract (Miri)
<!-- (50-60 words) -->

## - Research Questions (Mirj)
Based on trajectory data from 20 students using the Posmo Project App we attempt to answer the following research questions: 

- Does average travelling distance per day differ between students of different universities (ZHAW or UZH) and/or on weekends compared to workdays? 
- Does the weather condition (e.g. rain, sunshine) impact average travel distance of students by foot and/or bicycle?  

<!-- (50-60 words) -->

## - Results / products (Mirj)
We expect that average travelling distance between students of different universities differ, as ZHAW Wädenswil is located more remote, and the average student probably has to travel a greater distance to come to the campus compared to UZH, which is located relatively central in the city of Zurich. Additionally, Zurich is considered the biggest student city in Switzerland, with around 45'000 students (https://www.einstieg.com/studium/studium-im-ausland/studieren-in-der-schweiz.html). Therefore we expect that students of UZH will have a lower average travelling distance per day as students of ZHAW, as we assume that many students of UZH life in close proximity of the university or the city of Zurich in general. 

We expect that average travelling distance per day differs when comparing the weekends to workdays, as commuting is a major part of workdays which probably adds up to travelling distance. Hence, we expect to find a higher average travelling distance on workdays than on weekends. 

We expect that the weather condition has an impact on the average travel distance by foot and/or bicycle of students. On rainy days average travel distance by foot and/or bicycle will be lower than on days with sunshine. Additionally, we expect to find a lower average travel distance over all travel modes on rainy days, compared to sunny days. 

<!-- What do you expect, anticipate? -->

## Data (Mirj)
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

## Analytical concepts (Miri)
<!-- Which analytical concepts will you use? What conceptual movement spaces and respective modelling approaches of trajectories will you be using? What additional spatial analysis methods will you be using? -->

Our movement data is tracked in a continuous movement space (the whole earth surface) and the best suitable conceptual model is probably a network space combined with an entity based model. Our data structure is vector based so that we can obtain trajectories in a two dimensional space where movement can be constrained by objects (e.g. houses) and momevement corridors like streets and train tracks. The movement takes place in an intermittent manner and can be active (by foot) or passive (by train, boat). As all students have been tracked actively and in real-time by the posmo app (every 5s, 10s, or 15s) or by a GPS tracker, the perspective is Lagranian with a continuous sampling regime. 

Based on our research questions we are mainly interested in the average travelling distances of the students. Therefore our semantic level of interest concerns only the added up segments. 



## R concepts (Mirj)
The following R concepts, functions and packages we expect to mainly use in this project work: 

**1. Spatial data handling**:
Trajectory data contains spatial information (coordinates). Additionally, weather data may be available as raster data, which requires special handling in R. 

*Packages and functions:*

- **sf** - for spatial data analysis
  -   st_as_sf() - to convert data.frame into spatial object 
  -   st_transform() - to transform coordinate systems 
- **terra** - to handle raster data 

**2. Data manipulation and transformation**:
Our data most probably needs to be manipulated and transformed in various ways. 

*Packages and functions:*

- **dplyr** - for data wrangling and filtering
  -   group_by() - to group data (e.g. according to university, travel mode, weekday or weekend etc.)
  -   summarise() - to summarise intermediate results into another table 
  -   filter() - to filter data 
  -   mutate() - to calculate variables from existing variables and/or to create additional variables
-  **tidyr** 
-  **lubridate** - for working with dates and times
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

## - Risk analysis (Mirj)
The biggest challenges/problems probably occur with obtaining, handling and analysing the weather data. If not sufficient weather data is available (meaning not every movement space of all students can be covered), it would be possible to filter our data so that only trajectories within sufficient weather data coverage will be analysed. 

<!-- What could be the biggest challenges/problems you might face? What is your plan B? -->

## Questions? (Mirj + Miri)
- How, where can we access weather data which meets the needs of our analysis? 
- How to handle/communicate the inherent uncertainty of the Posmo Data (since we know that the App doesn't track activity data right every time)?
<!-- Which questions would you like to discuss at the coaching session? -->

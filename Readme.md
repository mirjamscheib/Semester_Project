# Proposal for Semester Project

**Patterns & Trends in Environmental Data / Computational Movement
Analysis Geo 880**

| Semester:      | FS23                                     |
|:---------------|:---------------------------------------- |
| **Data:**      | Trajectory data, weather data            | 
| **Title:**     | The title of your project                |
| **Student 1:** | Mirjam Scheib                            |
| **Student 2:** | Miriam Steinhauer                        |

## Abstract (Miri)
<!-- (50-60 words) -->

## Research Questions (Mirj)
Based on trajectory data from **20 students** using the Posmo Project App we attempt to answer the following research questions: 

- Does average travelling distance per day differ between students of different universities (ZHAW or UZH) and/or on weekends compared to workdays? 
- Does the weather condition (e.g. rain, sunshine) impact average travel distance of students by foot and/or bycicle?  

<!-- (50-60 words) -->

## Results / products (Mirj)
*Does average travelling distance per day differ between students of different universities (ZHAW or UZH) and/or on weekends compared to workdays?*

We expect that average travelling distance between students of different universities differ, as ZHAW Wädenswil is located more remote, and the average student probably has to travel a greater distance to come to the campus compared to UZH, which is located relatively central in the city of Zurich. Additionally, Zurich is considered the biggest student city in Switzerland, with around 45'000 students (https://www.einstieg.com/studium/studium-im-ausland/studieren-in-der-schweiz.html). Therefore we expect that students of UZH will have a lower average travelling distance per day as students of ZHAW. 

We expect that average travelling distance per day differs when comparing the weekends to workdays, as commuting is a major part of workdays which probably adds up to travelling distance. 

*Does the weather condition (e.g. rain, sunshine) impact average travel distance of students by foot and/or bycicle?*  

<!-- What do you expect, anticipate? -->

## Data (Mirj)
**What data will you use?**

Primary data to answer the research questions is the trajectory data from **20 students**, which covers a timeframe of one to two months (ca. 01.04.23 until 31.05.23). The data was collected using the Posmo App, which only tracks **activity data** and differentiates between several travel modes **(car, bicycle, foot, train, other....)**. Trajectory data from the App can be downloaded as a .csv-file containing the following attributes: 
-   **user_id:** entails the individual ID of the user (= student) (type: *character*)
-   **datetime:** date and time when a position of a user is tracked (type: *datetime*) 
-   **weekday:** abbreviated name of the weekday (e.g. Mon = Monday) (type: *character*)
-   **place_name:** names of a place, in which a user is at a specific time (type: *character*)
-   **transport_mode:** the type of transport used by a user **(e.g. car, bicycle, foot, train, other....)** (type: *character*)
-   **lon_x/lat_y:** coordinates of the user at a specific time (type: *numeric*)

**Will you require additional context data?**

- Weather data
- University of a student (ZHAW or UZH) 

**Where do you get this data from?** 

**Do you already have all the data?**

## Analytical concepts (Miri)
<!-- Which analytical concepts will you use? What conceptual movement spaces and respective modelling approaches of trajectories will you be using? What additional spatial analysis methods will you be using? -->

## R concepts (Mirj)
<!-- Which R concepts, functions, packages will you mainly use. What additional spatial analysis methods will you be using? -->

## Risk analysis (Mirj)
<!-- What could be the biggest challenges/problems you might face? What is your plan B? -->

## Questions? (Mirj + Miri)
<!-- Which questions would you like to discuss at the coaching session? -->

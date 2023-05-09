# Proposal for Semester Project

**Patterns & Trends in Environmental Data / Computational Movement
Analysis Geo 880**

| Semester:      | FS23                                     |
|:---------------|:---------------------------------------- |
| **Data:**      | What type of data are you focussing on?  |
| **Title:**     | The title of your project                |
| **Student 1:** | Mirjam Scheib                            |
| **Student 2:** | Miriam Steinhauer                        |

## Abstract (Miri)
<!-- (50-60 words) -->

## Research Questions (Mirj)
Based on trajectory data collected from **20 students** using the Posmo Project App in a timeframe of around one to two months (ca. 01.04.23 until 31.05.23) we attempt to answer the following research questions: 

- Does rain impact travel distance and/or travel mode? 
- Does distance impact travel mode?  
- Average travelling distance from home per day? Higher, lower or same on the weekends vs during week? 
- When riding the bycile or walking by foot -> avoidance of main roads? 
- Does the main location of a person have an impact on the primary travel mode (e.g. central point with a 100m diameter, classified in city, urban, land etc) 
- Does have age/university/status (student, teacher etc.) an impact on travelled distance/primary travel mode? 

<!-- (50-60 words) -->

## Results / products (Mirj)
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

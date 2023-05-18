# CubistHackathon2023 - Overview
This 1st-place project at Cubist Systemic Strategies' inaugural hackathon was a joint effort between 4 students at Columbia University, Cornell University, and Yale University. By analyzing publicly available motor vehicle collision and facility location data, the group identified areas of greatest need for ambulance stations in each of New York City's 5 boroughs.

## Hackathon Background
Cubist Systematic Strategies, the systematic investing business of Point72, hosted its first ever hackathon in April 2023, inviting roughly 50 students from top universities in the Northeast. The participants broke off into roughly 15 self-selected teams to explore publicly available New York City data and present meaningful, actionable insights. My team consisted of myself (an Applied Analytics Master's student at Columbia University), an Operations Research PhD student at Columbia University, and two Computer Science sophomores, one from Cornell University and the other from Yale University. 

## Problem
Roughly 65% of the ambulances in New York City are operated by the fire department (FDNY), and these ambulances face growing inefficiencies that threaten ambulance response time and, by extension, patient outcomes. Between July 2021 and October 2022, ambulances experienced a **35** second increase in time to travel to the scene. Furthermore, from July to October of 2022, ambulance response times (getting to the scene and getting the patient to the nearest hospital) averaged **7 minutes and 55 seconds**, a *full minute longer* than the set target.

These inefficiencies were largely attributed to a) a 10% increase (20,000) in life-threatening medical emergencies in the last year, b) worsening traffic, and c) insufficient staffing and equipment. As such, our group sought to determine locations of ambulance stations in each New York City borough (Manhattan, Brooklyn, Queens, the Bronx, and Staten Island) that would best minimize ambulance response time (our "cost") while identifying which current station is in the greatest need of added support.

## Approach
### Optimal Ambulance Facility Location
Using NYC data for the locations of current facilities (hospitals and ambulance stations) and a dataframe of motorvehicle collision instances in the last year, we clustered these accidents by the nearest ambulance station (by Haversine distance). For each hospital, we introduced five "dummy" ambulance stations, with one at the hospital and the others located a kilometer north, east, south, or west of the hospital. We then used discrete gradient descent to figure out which of these 5 potential ambulance station locations minimized the total ambulance response time across all accidents within the cluster belonging to the hospital. Finally, we compared each hospital's best result to determine, for each borough, where to place an ambulance station (EMS service center) that would best reduce ambulance response time.

### Immediate Support to Existing Station
Focusing specifically on Manhattan, we visualized accident patterns during the week, on weekends, and during rush hour. We further inspected these patterns by grouping by zip code, which highlighted a major issue in Manhattan's Lower East Side (LES); this particular neighborhood experienced the most injury/death-causing accidents by a wide margin in the last year and had just **one** ambulance station. This indicated that the Pier 35 and 36 EMS Center in LES is currently in greatest need of additional staffing and ambulances to address the disproportionate accidents in the area.

Here are how the number of injury/fatality-riddled accidents in LES compared to the second-most problematic neighborhoods for each grouping in the last year:
Rush Hour (weekdays from 8-9 AM and 3-7 PM)
- LES: **103** accidents
- Murray Hill/Kips Bay (1 ambulance station): 77 accidents
Weekdays
- LES: **237** accidents
- East Harlem (2 ambulance stations): 178 accidents
Weekends
- LES: **83** accidents
- East Harlem (2 ambulance stations): 62 accidents

## Target Audience and Call to Action
Our project was created with the intention of convincing New York City Mayor Eric Adams' Office of Management and Budget (OMB) to increase FDNY funding to support the following actions:
1. Construction of new EMS service centers for each of the 5 boroughs as follows:
   - Manhattan - 43rd Street & Broadway (Times Square)
   - 
   - Brooklyn - 64th Street & 21st Avenue (Mapleton)
   - The Bronx - Aldus Street & Bryant Avenue (Longwood)
   - Queens - 102nd Street & 103rd Avenue (Ozone Park)
   - Staten Island - Genesee Avenue & Stanley Circle (Eltingville)

2. Increased staffing and ambulances at the Pier 35 and 36 EMS station in Manhattan's Lower East Side.

## Datasets Used
[Motor Vehicle Collisions - Crashes](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95)

[Facilities Database](https://data.cityofnewyork.us/City-Government/Facilities-Database/ji82-xba5)

## Sources
[FDNY ambulance response times climb, *The Chief*](https://thechiefleader.com/stories/fdny-ambulance-response-times-climb,49831#:~:text=Average%20response%20times%20to%20medical,than%20the%20FDNY's%20targeted%20goal.)

[The Effects of Ambulance Response Time on Survival Following Out-of-Hospital Cardiac Arrest, *National Institute of Health*](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7718983/#:~:text=The%20odds%20of%20death%20if,of%20less%20than%208%20minutes.)

# Assessing the Traffic Injuries Involving Pedestrians and Bicyclists near school area in California

## Overview

This project aims to identify and analyze the factors contributing to traffic injuries and fatalities involving pedestrians and bicyclists in various counties of California. The study employs regression modeling to understand the influence of demographic, socioeconomic, and infrastructural variables on these incidents. The findings are intended to inform policymakers and urban planners on potential areas for intervention to enhance traffic safety.

## Data Sources

### 1. Census Data
The demographic and socioeconomic data used in this study were obtained from the American Community Survey (ACS) 2018, covering 12 counties in California. The data includes variables such as population density, racial composition (percentage of Black and Hispanic residents), median income, and average family size.

### 2. Public School Locations
Public school location data were collected from the National Center for Education Statistics (NCES) for the academic years 2015-16, 2018-19, and 2021-22. This data was used to examine the proximity of traffic incidents to school locations, which is critical for understanding the risk areas for students.

### 3. Traffic Injury Data
Traffic injury and fatality data were sourced from the University of California, Berkeley's Transportation Injury Mapping System (TIMS) for the years 2015 to 2022. This dataset includes detailed records of incidents involving pedestrians and bicyclists, including geographic coordinates, severity, and time of occurrence.

## Methodology

### Data Preprocessing

1. **Subsetting and Geocorrection**:
   - **Subsetting**: We focused on the counties of interest, filtering the datasets accordingly.
   - **Geocorrection**: The data was geocorrected to ensure all datasets were aligned to a consistent coordinate system, using a threshold of less than 0.05 errors.

2. **Feature Engineering**:
   - **Intersection Density**: Calculated the density of intersections within each census tract to capture the complexity of the road network.
   - **Local Road Percentage**: Measured the percentage of local roads as opposed to highways to understand the traffic mix.
   - **Crosswalk Density**: Calculated the density of crosswalks to account for pedestrian infrastructure.

### Regression Model

We constructed a multiple linear regression model to predict the total number of individuals killed or injured in traffic incidents, using the following formula:

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


| **Variable**                | **Data Source**                                                   |
|-----------------------------|-------------------------------------------------------------------|
| **NCES School Locations**    | National Center for Education Statistics (NCES)                  |
| **Crash Data**               | Transportation Injury Mapping System (TIMS) from UC Berkeley     |
| **Population Density**       | U.S. Census Bureau                                               |
| **Race Percentage**          | U.S. Census Bureau                                               |
| **Median Family Income**     | U.S. Census Bureau                                               |
| **Total Family Size**        | U.S. Census Bureau                                               |
| **Local Roads Percentage**   | OpenStreetMap (OSM)                                              |
| **Intersection Density**     | OpenStreetMap (OSM)                                              |
| **Crosswalk Density**        | OpenStreetMap (OSM)                                              |
| **Locale**                   | National Center for Education Statistics (NCES)                  |

## Variables and Data Description

| **Variable**           | **Data Type**    | **Explanation**                                                                 |
|------------------------|------------------|---------------------------------------------------------------------------------|
| **Local Roads Percentage** | Numeric Data      | The length of roads in the neighborhood divided by the total road length within a bounding box centered around the school location. |
| **Intersection Density**   |  Numeric Data      | The number of intersections per half-mile road within the bounding box centered around the school location. |
| **Crosswalk Density**      |  Numeric Data      | The number of crosswalks per road length mile. |
| **Total Family Size**      | Numeric Data      | The total number of families at the census tract level. |
| **Median Family Income**   |  Numeric Data      | The median family income at the census tract level. |
| **Population Density**     | Numeric Data      | The total population divided by the area size (miles/square miles). |
| **Race Percentage**        |  Numeric Data      | The number of different race populations as a percentage of the total population. |
| **Crash Data**             | Numeric Data      | The count of pedestrians and bicyclists killed or injured within 0.5 miles of the school during the school year. |
| **Locale**                 | Categorical Data  | A code describing the location of the school. |

## Methodology

### Data Preprocessing

1. **Subsetting and Geocorrection**:
   The data was geocorrected to ensure all datasets were aligned to a consistent coordinate system, using a threshold of less than 0.05 errors.

2. **Feature Engineering**:
   - **Intersection Density**: Calculated the density of intersections within each census tract to capture the complexity of the road network.
   - **Local Road Percentage**: Measured the percentage of local roads as opposed to highways to understand the traffic mix.
   - **Crosswalk Density**: Calculated the density of crosswalks to account for pedestrian infrastructure.

## Study Area

<div style="display: flex; align-items: center;">

<div style="flex: 1;">
<p>The study focuses on 12 counties in California, which are categorized as follows:</p>

### LA Counties:
- Los Angeles County
- Ventura County
- Orange County
- San Bernardino County
- Riverside County

### San Diego County:
- San Diego County

### Bay Area Counties:
- San Francisco County
- Alameda County
- San Mateo County
- Santa Clara County
- Contra Costa County
- Marin County

### Schools Coverage:
- **Total Schools in 2018:** 6,469 schools
</div>

<div style="flex: 1; text-align: right;">
    <img src="study_area.png" alt="Study Area" style="max-width: 100%; height: auto;">
</div>

</div>


### Regression Model

A multiple linear regression model was constructed to predict the total number of individuals killed or injured in traffic incidents, using the following formula:


### Regression Model for Total Killed or Injured

The estimated model for predicting the number of traffic injuries involving pedestrians and bicyclists near school areas in California is shown below:

![Regression Model](regression_model.png)

**Variables:**
- **population_density**: Number of people per square mile
- **total_pop**: Total population in the area
- **p_black**: Proportion of the population that is Black
- **p_hispanic**: Proportion of the population that is Hispanic
- **family_size**: Average family size in the area
- **median_income**: Median household income in the area
- **is_suburban**: A binary variable indicating whether the area is suburban (1 if suburban, 0 if not)
- **intersection_density**: Number of intersections per square mile
- **local_road_percentage**: Percentage of local roads in the area
- **crosswalk_density**: Number of crosswalks per square mile



## Diagnose Potential Problems

### Outliers and Model Diagnostics

- **Outliers Check**: Conducted an outlier analysis for the selected model.
- **Cook's Distance**: Charted the Cook's distance to identify points significantly distant from others.
- **Significant Outlier**: Identified a point with a Cook's distance significantly larger than others. This point corresponds to Treasure Island.
- **Final Model Adjustment**: Removed the identified outlier along with 5 other points that had a Cook's distance greater than 0.04.



<div style="display: flex;">
  <div style="flex: 1;">
    <ul>
      <li>Below is a visualization of the Cook's distance chart highlighting the outliers:</li>
<!--       <li>The map below shows the location of the significant outlier, Treasure Island:</li> -->
    </ul>
  </div>
  <div style="flex: 1;">
    <img src="cook_dis.png" alt="Cook's Distance Chart" style="float: right; width: 50%;">
<!--     <img src="path_to_your_image/treasure_island_outlier_map.png" alt="Treasure Island Outlier" style="float: right; width: 50%;"> -->
  </div>
</div>



## Nonlinearity Check

- **Dependent Variable**: The dependent variable is discrete and represents infrequent events.
- **Residuals Examination**: Conducted a visual examination of residuals to check for heteroskedasticity.
- **Clustering Observed**: Noticed a significant amount of clustering in the lower values in the residual plot.


<div style="display: flex;">
  <div style="flex: 1;">
    <ul>
      <li>The residual plot below illustrates the clustering observed in the lower values:</li>
    </ul>
  </div>
  <div style="flex: 1;">
    <img src="res_pre.png" alt="Residual Plot" style="float: right; width: 50%;">
  </div>
</div>

## Multicollinearity Check

- **Multicollinearity Issues**: Identified two instances of multicollinearity in our data.
  - **Locale Variable & Demographic Data**: High correlation observed between `is_urban` and `is_suburban` (-0.895).
  - **Subset Analysis**: When all groups were included, Hispanic percentage became largely determined by the others.
  - **White and Asian Correlation**: Found a negative correlation between White and Asian percentages (-0.501).
- **Final Model Decision**: 
  - Removed White and Asian percentages from the final model.
  - Kept Hispanic and Black percentages to reduce multicollinearity and improve model robustness.


<div style="display: flex;">
  <div style="flex: 1;">
    <ul>
      <li>The correlation matrix below highlights the multicollinearity issues:</li>
    </ul>
  </div>
  <div style="flex: 1;">
    <img src="multi1.png" alt="Correlation Matrix" style="float: right; width: 50%;">
     <img src="multi2.png" alt="Correlation Matrix" style="float: right; width: 50%;">
  </div>
</div>

### Conclusion

- After removing these outliers, the model's accuracy and reliability improved, providing a more accurate representation of the relationship between the variables.

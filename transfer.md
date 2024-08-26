# Assessing the Impact of Muni Metro Transit Station Location on Public Transportation Accessibility: Case Study in San Francisco 

---

## Abstract

The light rail transit system in San Francisco plays a crucial role in urban public transportation, significantly impacting mobility and accessibility. This study enhances the accessibility of the light rail system by integrating transit station location and travel time into accessibility calculations. A comprehensive approach was employed, leveraging data from SFMTA, Open Street Map, and U.S. Census, to analyze the spatial distribution of transit stations and their impact on accessibility.

---

## Introduction

### Background Information

In San Francisco, public transportation, particularly the light rail transit system managed by SFMTA, is vital for daily commuting. The city's network includes multiple lines with 113 stations across 38.9 miles. Despite the critical role of public transport, issues like inequitable access and slow recovery post-pandemic have raised concerns about accessibility and efficiency, prompting the need for a detailed evaluation of transit station accessibility.

**Objectives of the Project**:
- Evaluate the current accessibility of the Muni Metro transit system.
- Develop a robust accessibility index incorporating transit station location and travel time.
- Analyze the spatial distribution of stations and identify barriers to accessibility.
- Compare different accessibility models to identify effective methods for evaluating transit accessibility.

![Muni Metro Map](path/to/muni_metro_map.png)
*Figure 1: Muni Metro Map of San Francisco (Data Source: SFMTA)*

---

## Methodology

### Data Sources

- **SFMTA GTFS Dataset**: Provides real-time data for map visualization, including vehicle positions and estimated arrival times.
- **U.S. Census Bureau**: Supplies San Francisco shapefiles, population, and commuting data.

### Study Area

San Francisco is the focal area for this study, chosen for its dense population and extensive transit network.

![Study Area with Metro Routes and Stops](path/to/study_area.png)
*Figure 2: Study Area with Metro Routes and Stops*

### Transit Travel Time Component

This component models the probability of using a transit route based on travel time. A logistic decay function is used to represent how likely travelers are to wait for transit services.

### Transit Transfer Location Component

A binary parameter indicates whether a trip requires a transfer. Direct routes are preferred due to reduced travel time and increased convenience.

---

## Results

### Transit Accessibility Index

The transit accessibility index incorporates both the transfer location and transfer travel time components. This index provides a unique value for each Origin-Destination (OD) pair, reflecting the likelihood of transit demand.

### Zone-Based Accessibility

The accessibility of each census tract is represented by the average trip probability from that tract to others. 

![Zone-Based Transit Accessibility](path/to/zone_based_accessibility.png)
*Figure 3: Zone-Based Transit Accessibility of all Census Tracts in San Francisco*

### Transit Accessibility Example

To explore the impact of transfer locations on a single census tract area, census tract 168.02 is chosen. 

![Census Tract Population Distribution](path/to/census_tract_population_distribution.png)
*Figure 4: Census Tract Population Distribution of San Francisco Census Tract 168.02 (Data Source: US. Census. Data)*

---

## Discussion

### Implications of Findings

The study reveals that the strategic placement of transfer stations significantly enhances accessibility within the grid network of San Francisco. The results suggest that considering transfer locations in accessibility models can more accurately reflect actual accessibility levels.

### Limitations of the Study

The study focuses on the Muni Metro system and does not account for multimodal transit behavior. Additionally, it does not consider peak vs. non-peak hour variations, which could influence accessibility.

---

## Conclusion

Public transportation is crucial for equitable access to essential services. This study's analysis reveals that central and northern parts of San Francisco exhibit higher accessibility, with some southern tracts requiring improvements. The inclusion of location factors provides insights into travelers' behavior and accessibility modes.

![Change in Transit Accessibility Level](path/to/change_in_transit_accessibility.png)
*Figure 5: Change in Transit Accessibility Level by Incorporating the Transfer Location Component*

---

## References

1. Ben-Akiva, M., & Lerman, S. R. (1985). *Discrete Choice Analysis: Theory and Application to Travel Demand*. MIT Press.
2. Basso, F., et al. (2020). Accessibility to opportunities based on public transport GPS-monitored data: The case of Santiago, Chile. *Travel Behaviour and Society, 21*, 140–153. [DOI](https://doi.org/10.1016/j.tbs.2020.06.004)
3. Ceder, A., et al. (2013). Modelling public-transport users’ behaviour at connection point. *Transport Policy, 27*, 112–122. [DOI](https://doi.org/10.1016/j.tranpol.2013.01.002)
4. Cervero, R., & Murakami, J. (2010). Effects of built environments on vehicle miles traveled: Evidence from 370 US urbanized areas. *Environment and Planning A, 42(2)*, 400-418.
5. Chia, J., & Lee, J. B. (2020). Extending public transit accessibility models to recognize transfer location. *Journal of Transport Geography, 82*, 102618. [DOI](https://doi.org/10.1016/j.jtrangeo.2019.102618)

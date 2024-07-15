# Minimize-the-total-cost-of-oil-transportation-for-the-EU-countries
 Our project aims to minimize the total cost of oil transportation for EU countries, factoring in economic and environmental considerations. We sourced population and oil production data from Wikipedia and created a distance matrix using the geocoordinates of capital cities.
 **Conducted By:** Felix Grandner, Min Jegal

## Introduction

Our project focuses on minimizing the total cost of oil transportation for EU countries. We sourced population data for each country and the amount of oil each country produces from Wikipedia. The data consists of three main parts:
- **distance_matrix.csv**: Distance between countries.
- **oil_countries.csv**: Information on the amount of oil each country produces.
- **eu_countries.csv**: Population data of each country.

Given the complexity of obtaining exact oil consumption figures, we modified the data using a percentage of the total EU-27 area, rounded to the nearest whole number.

## Objective

The primary goal of our model is to determine the optimal distribution of oil imports among EU countries from various oil-producing countries, considering both economic and environmental factors. The model aims to minimize the total cost of transportation, including the direct cost associated with the distance of transportation and the environmental impact in terms of carbon emissions. The model also considers variable transportation capacities, reflecting real-world scenarios where transportation resources might fluctuate.

### Results

The optimization results from both parts of the project show the optimal distribution of oil imports among EU countries. The second part of the project, with the inclusion of the pipeline, significantly alters the distribution by increasing the flow of oil from transatlantic nations. The model also ensures diversification, preventing over-reliance on any single oil-producing country.


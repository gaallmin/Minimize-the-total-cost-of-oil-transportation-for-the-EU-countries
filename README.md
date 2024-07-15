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

## Methodology

### Data Preparation

To calculate distances between countries, we gathered the geocoordinates of each capital city and computed the distance using the Haversine distance function.

### Optimization Model - Part 1

The initial model is structured as a linear optimization problem with the following parameters:
- **I**: Set of oil-producing countries.
- **J**: Set of EU countries.
- **Cap_i**: Oil production capacity for country i.
- **Dem_j**: Oil demand for EU country j.
- **Distance_i,j**: Distance between oil-producing country i and EU country j.
- **carbon_emission_coefficient**: Coefficient for carbon emissions.

**Objective Function**: Minimize the total cost of transportation and environmental impact.

**Constraints**:
1. **Capacity Constraint**: Simulates an embargo on Russian oil by setting the capacity to 300. For non-Russian countries: \( \sum_{j \in J} x_{i,j} \leq Cap_i \forall i \in I \setminus \{ \text{"Russia"} \} \). For Russia: \( \sum_{j \in J} x_{\text{"Russia"},j} \leq 300 \).
2. **Demand Constraint**: \( \sum_{i \in I} x_{i,j} \geq Dem_j \forall j \in J \).
3. **Variable Capacity Adjustment**: \( TransCap_i = 0.75 \times Cap_i \forall i \in I \).

### Optimization Model - Part 2

The second part of the project incorporates additional geopolitical and logistical constraints, such as production capacities and diversification requirements. A proposed solution involves constructing a new pipeline at a cost of €8000 to significantly reduce transportation costs for transatlantic nations.

**Objective Function**: Minimize the total transportation cost and an additional cost factor, considering the linearization of the product term.

**Additional Constraints**:
1. **Diversification Constraint**: Each EU country must source oil from at least 5 different countries.
2. **Minimum Usage Constraint**: \( x_{2i,j} \geq 0.1 \times Dem_j \times y_{2i,j} \forall i \in I, j \in J \).
3. **Binary Constraints**: Ensure that \( x_{2i,j} \) is non-zero only if \( y_{2i,j} \) is one.
4. **Linearization Constraints**: Ensures the model remains linear by introducing an auxiliary variable \( z_{i,j} \).

### Results

The optimization results from both parts of the project show the optimal distribution of oil imports among EU countries. The second part of the project, with the inclusion of the pipeline, significantly alters the distribution by increasing the flow of oil from transatlantic nations. The model also ensures diversification, preventing over-reliance on any single oil-producing country.

## Conclusion

The project successfully demonstrates how linear optimization can be applied to minimize the cost of oil transportation within the EU, taking into account both economic and environmental factors. The inclusion of geopolitical constraints and the construction of a new pipeline further refine the model to reflect real-world scenarios. The results highlight the importance of diversification and strategic investment in infrastructure to optimize resource distribution. 

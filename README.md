
# Los Angeles County 2023 Crime Map 

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis and Transformation](#data-analysis-and-transformation)
- [Results](#results)
- [Limitations](#limitations)
- [Next Steps](#next-steps)
 
### Project Overview

This data project aims to provide valuable insights into crime trends across Los Angeles County for the year 2023. The goal is to develop a mapping tool that will help organizations focused on social justice initiatives target areas where decriminalization efforts and anti-carceral policies can be most effectively implemented. By visualizing crime patterns, the tool can assist organizations in shaping more focused outreach programs, ad campaigns, and secure funding.

### Data Sources

Crime Data: Crime Data: The primary dataset for this analysis is the 2023crimedata.csv file, sourced from the Los Angeles Sheriff's Office. This dataset includes detailed information on crime incidents across LA County in 2023.
[LA County GIS Data](https://lacounty.maps.arcgis.com/home/item.html?id=a76e9954365d4608aa8ae81959f402f7&sortOrder=desc&sortField=defaultFSOrder): The City_and_Unincorporated_Boundaries_(Legal).shp dataset provides the geographic boundaries for the cities and unincorporated areas within Los Angeles County. This serves as the base layer for geographical mapping.


### Tools

- Excel: Data cleaning and inspection
- PG Admin 4: Database management and analysis
- PostgreSQL: Relational Database Management System (RDBMS) for data analysis
- Python: Data transformation and visualization
- PyCharm: Integrated Development Environment (IDE)


### Data Cleaning/Preparation

The data preparation phase involved the following steps:

Loading and inspecting the dataset
Handling missing values
Cleaning and formatting the data

### Exploratory Data Analysis

During EDA, several questions arose:

Why does the crime dataset include more than 88 cities when Los Angeles County officially has only 88 cities?
Is all of the crime data contained within LA County?
How can crime categories be grouped or aggregated for further analysis?

### Data Analysis and Transformation

```sql
SELECT DISTINCT city
FROM crime2023la
ORDER BY city ASC
```

This query returned 200 cities. Los Angeles County has 88 incorporated cities. Further research led to the understanding that LA county has additional unincorporated cities. 


```sql
SELECT DISTINCT category
FROM crime2023la
ORDER BY category ASC
```

There are 30 distinct categories of crimes.  Initial observations suggest that these categories can likely be aggregated into broader categories such as property-related crimes and person-related crimes, if needed.

Moving on from SQL, I found and downloaded shapefiles of LA County’s official cities and unincorporated places boundaries.

I used Python: geopandas, plotly, dash web app, and other libraries to create a heat map, aggregated crime, and specific crime maps for 2023 LA county crime data.


### Results


### Limitations

Data Focus: The tool currently focuses solely on crime data. Future improvements could include the addition of demographic data (such as race and socio-economic status) to identify correlations between crime rates and these factors, further informing decriminalization efforts.
Heat Map Bias: The heat map may emphasize areas with higher population densities, which could skew the representation of crime across the county.

### Next Steps

- Normalization: Normalize the data based on population density to provide more accurate insights, which could be incorporated into the heat map as additional layers.
- Year Range: Include crime data from 2018-2023, allowing users to filter by specific years.
- Demographic Overlay: Implement features that overlay demographic data on the map, alongside crime statistics, to explore connections between demographic variables and crime patterns.est data points.

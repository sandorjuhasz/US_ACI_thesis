# Amenity complexity and neighborhood prosperity in US metropolitan areas

---

## Overview

How is the amenity complexity of urban neighborhoods related to their centrality and the economic prosperity of their residents? We estimate the amenity complexity of urban neighborhoods across the 50 largest US metropolitan areas and relate it to neighborhood income, housing prices, educational attainment, commuting patterns, and the infrastructural and physical centrality of tracts within the urban system. We test whether these relationships are robust across different POI datasets.

---

## Data

- **Context:** 50 largest US metropolitan areas (CBSAs), census-tract level
- **Points of interest:** Foursquare, Overture Maps, OpenStreetMap
- **Socioeconomic indicators:** American Community Survey (ACS) 5-year estimates — income, housing values, educational attainment
- **Commuting flows:** LEHD Origin-Destination Employment Statistics (LODES)
- **Geographies:** Census TIGER/Line tract boundaries, CBSA delineation files

---

## Structure of the repository

```
├── code/          # Data processing, ECI estimation, and analysis notebooks
├── data/
│   └── raw/ # Cleaned tract-level datasets used in the analysis
│   └── processed/ # Cleaned tract-level datasets used in the analysis
├── literature/    # Key papers for the conceptual framework
└── README.md
```

---

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

The datasets, and how to download them, are described in [`data/README.md`](data/README.md).

---

## Structure of the repository

```
├── code/              # Data overview, Foursquare cleaning, and ECI estimation notebooks
├── data/              # Data description (README) — files are downloaded separately
│   ├── raw/           # Original POI, ACS, and census tract files
│   └── processed/     # Cleaned datasets created by the notebooks
├── literature/        # Key papers for the conceptual framework
└── README.md
```

---

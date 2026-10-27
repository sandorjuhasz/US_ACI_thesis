# Data

The data files are **not stored on GitHub** because they are too large. Download them from this link:

**[LINK — provided by your supervisor]**

Copy the **content** of the downloaded folder into `data/raw/` (do not create an extra subfolder). The notebooks in `code/` expect exactly this structure:

```
data/
├── raw/
│   ├── POI_US_top50_metros/                       # 50 files, one per metro area
│   │   ├── foursquare_12060_atlanta_places.parquet
│   │   ├── ...
│   │   └── foursquare_47900_washington_places.parquet
│   ├── acs_data_census_tracts_2012_2020.csv.gz
│   └── censustract_geoms_top50.geojson
└── processed/                                     # created by the notebooks
```

---

## Raw data

**`POI_US_top50_metros/`** — Foursquare Open Source Places for the 50 largest US metropolitan areas
- One parquet file per metro: `foursquare_<cbsacode>_<name>_places.parquet`, e.g. `foursquare_40060_richmond_places.parquet`
- ~13.2 million POIs in total
- Key columns: `fsq_place_id`, `name`, `latitude`, `longitude`, `fsq_category_labels`, `date_created`, `date_closed`, `cbsacode`
- `fsq_category_labels` holds the category hierarchy, e.g. `["Dining and Drinking > Restaurant > Italian Restaurant"]`. About 8% of POIs have no category. See `code/02_FS_data_cleaning.ipynb` for how to clean it.

**`acs_data_census_tracts_2012_2020.csv.gz`** — American Community Survey (ACS) 5-year estimates by census tract
- 38,788 census tracts, wide format: one column per variable and year (2012–2020), e.g. `income2020`
- `tract_id` — census tract ID (e.g. `14000US34003001000`)
- `population<year>` — total population
- `income<year>` — median household income (USD)
- `education_bachelor<year>`, `education_total<year>` — population with a bachelor's degree / total population used for the education share
- `race_total<year>`, `white<year>`, `black<year>`, `native<year>`, `asian<year>` — population by race

**`censustract_geoms_top50.geojson`** — census tract boundaries of the 50 metro areas
- 38,788 tracts, coordinates in WGS84 (EPSG:4326)
- `full_geoid` — census tract ID, matches `tract_id` in the ACS file
- Also: `display_name`, `aland` / `awater` (land / water area in m²), `population`
- **Note:** the file has one GeoJSON feature per line, so `gpd.read_file()` reads only the first tract. Read it line by line instead (see `code/01_data_overview.ipynb`).
- The file has no metro code. Assign tracts to metros with a spatial join to the POIs, or with the Census CBSA delineation files.

---

## Processed data

Created by `code/02_FS_data_cleaning.ipynb`:

**`foursquare_top50_metros_clean.parquet`** — POIs from all 50 metros with a cleaned category (~12.1 million POIs)
- `fsq_place_id`, `name`, `latitude`, `longitude`, `cbsacode`
- `top` — level 1 Foursquare category (10 categories, e.g. `Dining and Drinking`)
- `category` — level 2 category, or level 1 if nothing more detailed exists (e.g. `Restaurant`)

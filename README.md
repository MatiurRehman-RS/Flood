# Flood Inundation Mapping and Change Detection — Ravi, Jhelum & Chenab Rivers (2025)

SAR-based multi-temporal flood mapping for the 2025 monsoon
flood events across three major river systems in Punjab, Pakistan.

---

## Background

Optical remote sensing is severely limited during flood events
due to persistent cloud cover associated with monsoon conditions.
Sentinel-1 C-band SAR penetrates cloud cover and provides
reliable surface water delineation through backscatter contrast
between inundated surfaces (specular reflection, low backscatter)
and dry land (high backscatter). This study applies multi-temporal
SAR change detection to map inundation extent across three rivers
affected by the 2025 Pakistan flood events.

---

## Study Rivers

| River | Province | Flood Peak Period |
|---|---|---|
| Ravi | Punjab | 2025 monsoon season |
| Jhelum | Punjab / AJK | 2025 monsoon season |
| Chenab | Punjab | 2025 monsoon season |

---

## Methodology

1. Pre-flood and during-flood Sentinel-1 GRD scenes acquired
   for each river system
2. Preprocessing: thermal noise removal, radiometric calibration,
   terrain correction (SRTM DEM)
3. Water body delineation using backscatter thresholding
   (VV polarization, IW mode)
4. Change detection: binary difference between pre- and
   during-flood water masks
5. Inundation extent quantified per river in km²
6. Cross-validation against GPM-IMERG daily precipitation
   accumulation to confirm hydrometeorological consistency
   with globally reported flood records

---

## Data

| Dataset | Source | GEE Collection |
|---|---|---|
| Sentinel-1 GRD | ESA Copernicus | `COPERNICUS/S1_GRD` |
| GPM IMERG Final | NASA GES DISC | `NASA/GPM_L3/IMERG_V06` |
| SRTM DEM | NASA/USGS | `USGS/SRTMGL1_003` |

---

## Repository Structure

```
├── src/
│   ├── flood_mapping_ravi.js      ← GEE: Ravi River
│   ├── flood_mapping_jhelum.js    ← GEE: Jhelum River
│   ├── flood_mapping_chenab.js    ← GEE: Chenab River
│   └── gpm_validation.js         ← GEE: precipitation cross-check
├── results/
│   ├── inundation_extent_km2.csv  ← area per river per date
│   └── flood_boundaries/         ← GeoJSON per river
├── figures/
│   ├── pre_flood_composite.png
│   ├── flood_inundation_maps.png
│   └── gpm_precipitation.png
└── docs/
    └── change_detection_approach.md
```

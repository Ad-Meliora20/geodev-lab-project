# My Project Brief

## The Question

**In southern Nigeria, how well do geospatial models trained on multi-source Earth-observation data generalise to different locations and time periods?**

## Why It Matters

A geospatial model can perform well when training and testing data come from similar conditions but perform poorly when deployed elsewhere or at another time. Measuring this performance change will help determine how reliable Earth-observation models are when transferred beyond their original training conditions.

## The Data I Need

| Dataset | Purpose | Key details |
|---|---|---|
| Southern Nigeria Wetland Reference Dataset | Training/reference locations | 1,500 reference points; 8 land-cover classes; associated 10 m map |
| Sentinel-2 Level-2A Surface Reflectance | Optical features | 10 m, 20 m & 60 m bands; ~5-day revisit; 2017–present |
| Sentinel-1 GRD SAR | Radar features | C-band SAR; VV/VH; ~10 m relevant GRD spatial resolution; 2014–present |
| Landsat Collection 2 | Independent temporal evidence | ~30 m multispectral resolution; Landsat 8/9 from 2013/2021–present |
| JRC Global Surface Water | Water persistence/change | 30 m; 1984–2024 |
| Dynamic World | Supporting temporal/land-cover evidence | 10 m; 2015–present; 9 classes |
| SRTM DEM | Topographic context | ~30 m |
| Google Earth Historical Imagery | Visual temporal verification | Historical imagery; availability varies by location/date |

## Where Each Dataset Comes From

- **Southern Nigeria Wetland Reference Dataset:** https://archive.researchdata.leeds.ac.uk/1254/
- **Sentinel-2 Level-2A Surface Reflectance:** https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED
- **Sentinel-1 GRD SAR:** https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S1_GRD
- **Landsat Collection 2:** https://developers.google.com/earth-engine/datasets/catalog/landsat
- **JRC Global Surface Water:** https://global-surface-water.appspot.com/download
- **Dynamic World:** https://developers.google.com/earth-engine/datasets/catalog/GOOGLE_DYNAMICWORLD_V1
- **SRTM DEM:** https://developers.google.com/earth-engine/datasets/catalog/USGS_SRTMGL1_003
- **Google Earth Historical Imagery:** https://developers.google.com/maps/documentation/earth/historical-imagery

*Satellite dataset sizes will depend on the study area, dates, bands and processing. The published Wetland_Data.zip is approximately 71 kB.*

## What I Would Build

**A reproducible geospatial modelling pipeline that combines Sentinel-1 SAR and Sentinel-2 optical data to train a wetland classification model and evaluate it under random, spatial, temporal and combined spatiotemporal validation. The output will show where and how much model performance changes when deployment conditions differ from training conditions.**

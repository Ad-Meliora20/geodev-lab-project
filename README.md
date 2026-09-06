# Geospatial Model Generalisation Under Spatial and Temporal Domain Shift

## Wetland Case Study — Southern Nigeria

## Project Question

In southern Nigeria, how well do geospatial models trained on multi-source Earth-observation data generalise to different locations and time periods?

## Project Overview

This project investigates the reliability of geospatial models when they are applied outside the geographic and temporal conditions represented in their training data.

Wetland environments in southern Nigeria will be used as the experimental case study. The project combines Sentinel-1 SAR and Sentinel-2 optical Earth-observation data to develop a wetland classification model and evaluate its performance under different deployment conditions.

The main focus is **model generalisation**, rather than simply producing another wetland map.

## Why This Matters

A model can achieve high accuracy when training and testing data are similar, while performing substantially worse when applied to a different location or time period.

This project compares model performance under:

1. Random validation
2. Spatial domain shift
3. Temporal domain shift
4. Combined spatial and temporal domain shift

The objective is to determine how reliable the model remains as the deployment environment becomes increasingly different from the training environment.

## Study Area

The initial study region is southern Nigeria.

The exact spatial domains will be determined after inspecting the geographic distribution of the available reference data rather than being selected arbitrarily.

## Data

### Southern Nigeria Wetland Reference Dataset

The primary reference dataset contains **1,500 reference points** representing eight land-cover classes across southern Nigeria, with an associated 10 m land-cover map.

**Source:** https://archive.researchdata.leeds.ac.uk/1254/

**Published ZIP size:** approximately 71 kB

**Licence:** CC BY 4.0

### Sentinel-2 Level-2A Surface Reflectance

Sentinel-2 optical imagery will provide spectral information for wetland classification.

Potential variables include Blue, Green, Red, Red-edge, NIR, SWIR, NDVI, NDWI, MNDWI and NDMI.

**Resolution:** 10 m, 20 m and 60 m depending on band.

**Temporal availability:** 2017–present.

**Revisit:** approximately 5 days.

**Source:** https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED

**Data size:** varies according to study area, dates and selected bands.

### Sentinel-1 GRD SAR

Sentinel-1 Ground Range Detected (GRD) data will provide radar information complementary to Sentinel-2.

Potential variables include VV, VH, VV/VH and VV−VH.

**Sensor:** C-band SAR

**Temporal availability:** 2014–present.

**Relevant spatial resolution:** approximately 10 m.

**Source:** https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S1_GRD

**Data size:** varies according to study area, dates and filtering.

### Landsat Collection 2

Landsat imagery will provide an independent Earth-observation source for assessing temporal conditions at selected reference locations.

**Spatial resolution:** approximately 30 m for multispectral bands.

**Temporal availability:** Landsat 8 from 2013–present; Landsat 9 from 2021–present.

**Source:** https://developers.google.com/earth-engine/datasets/catalog/landsat

### JRC Global Surface Water

JRC Global Surface Water will support investigation of historical water occurrence and change at reference locations.

**Spatial resolution:** 30 m

**Temporal coverage:** 1984–2024

**Source:** https://global-surface-water.appspot.com/download

### Dynamic World

Dynamic World will provide supporting 10 m land-cover information for temporal consistency assessment and environmental interpretation.

**Spatial resolution:** 10 m

**Temporal availability:** 2015–present

**Classes:** 9 land-cover classes

**Source:** https://developers.google.com/earth-engine/datasets/catalog/GOOGLE_DYNAMICWORLD_V1

Dynamic World predictions will not automatically be treated as ground truth.

### SRTM DEM

SRTM elevation data may be used as additional environmental/topographic information where appropriate.

**Spatial resolution:** approximately 30 m

**Source:** https://developers.google.com/earth-engine/datasets/catalog/USGS_SRTMGL1_003

### Google Earth Historical Imagery

Historical imagery may be used as supporting visual evidence when assessing whether selected reference locations have remained stable or changed through time.

**Temporal coverage:** varies by location.

**Source:** https://developers.google.com/maps/documentation/earth/historical-imagery

Historical imagery will be treated as supporting reference evidence rather than automatically as formal ground truth.

## Proposed Method

### Data Preparation

1. Inspect and clean the reference dataset.
2. Analyse the geographic distribution of reference points.
3. Define appropriate spatial domains/blocks.
4. Acquire and preprocess Sentinel-1 and Sentinel-2 data.
5. Generate selected spectral and SAR features.
6. Extract predictor values at reference locations.

### Modelling

The initial model will be **Random Forest**.

The primary classification task will initially be:

**Wetland vs Non-wetland**

The available reference data contain 724 wetland-related observations and 776 non-wetland observations, providing a relatively balanced binary classification problem.

A multiclass wetland-type experiment may be considered later if the spatial distribution and reference quality support it.

## Validation Experiments

### Random Validation

A conventional train-test split will establish the baseline model performance.

### Spatial Domain Shift

Training and testing data will come from geographically separated domains.

### Temporal Domain Shift

Training and testing will use different time periods while accounting for genuine environmental change.

### Combined Spatiotemporal Domain Shift

Training and testing will differ in both geographic location and time.

## Evaluation

Performance will be assessed using:

- F1-score
- Precision
- Recall
- Accuracy
- Confusion matrix

The key result will be the change in model performance between validation scenarios.

## Domain Shift Analysis

The project will investigate differences between training and deployment environments.

Potential measures include:

- Jensen-Shannon divergence
- Wasserstein distance
- Kolmogorov-Smirnov statistics
- Feature-space/PCA distance

The final method will be selected after examining the data.

The objective is to determine whether greater environmental/domain difference is associated with greater model-performance degradation.

## Research Hypotheses

### H1 — Spatial Generalisation

Spatially separated validation will produce lower model performance than conventional random validation.

### H2 — Temporal Generalisation

Temporal separation will reduce model performance.

### H3 — Combined Domain Shift

Combined spatial and temporal separation will produce greater performance degradation than either shift individually.

### H4 — Domain Dissimilarity

Greater difference between training and deployment feature distributions will be associated with greater model-performance degradation.

## Expected Outputs

- Reproducible geospatial modelling workflow
- Wetland classification results
- Random-validation benchmark
- Spatial generalisation assessment
- Temporal generalisation assessment
- Spatiotemporal generalisation assessment
- Domain-shift measurements
- Performance-degradation analysis
- Maps and statistical summaries of model reliability

## Current Status

### Completed

- Research question defined
- Case study selected
- Primary reference dataset identified
- Core EO datasets identified
- Initial modelling approach defined
- Initial validation framework defined

### Next Step

A detailed audit of the 1,500 reference points will determine:

- geographic distribution;
- class distribution by location;
- suitable spatial domains;
- feasibility of spatial holdout;
- appropriate temporal validation locations.

The final spatial-validation design will be determined from the actual data.

## Reproducibility

The project will use a reproducible workflow with documented data sources, preprocessing procedures, modelling scripts and evaluation procedures.

Proposed repository structure:

```text
geospatial-model-generalisation-wetlands/
│
├── README.md
├── project_brief.md
├── data/
│   ├── raw/
│   ├── processed/
│   └── README.md
│
├── notebooks/
│
├── scripts/
│   ├── preprocessing/
│   ├── feature_engineering/
│   ├── modelling/
│   ├── validation/
│   └── domain_shift/
│
├── results/
│   ├── figures/
│   └── tables/
│
└── docs/
    └── methodology.md
```

Raw external datasets will not necessarily be uploaded to this repository. Their official sources, licences and acquisition procedures will be documented instead.

## Core Principle

The project does not assume that high random-validation accuracy means that a geospatial model is reliable in general.

It investigates the difference between:

**performance under familiar conditions**

and

**performance under changed spatial and temporal conditions.**

The central objective is to understand the transferability and reliability of geospatial models beyond their original training domain.

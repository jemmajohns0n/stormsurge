# stormsurge

This repository contains code and data for analyzing storm surge events at three tide gauge locations (Karachi, PAK | Booby Island, AUS | Maasvlakte Amaliahaven, NLD) using high-rate coastal satellite altimetry from the DGFI-TUM Open Altimeter Database (ADB) ALES sea level anomalies (SLA).

The analysis identifies extreme sea level events in tide gauge records, investigates whether these events are detected with the altimetry data, and validates the altimetry-derived results against tide gauge observations and the Global Tide and Surge Model (GTSM).

## Data Sources

### High-Rate Coastal Altimetry

- **DGFI-TUM Open Altimeter Database:** [https://openadb.dgfi.tum.de/en/](https://openadb.dgfi.tum.de/en/)
- **Product:** ALES SLA

### Tide Gauge Data

Tide gauge observations are provided as Parquet files for the three study locations.

- **Source: GESLA Version 4.1** [https://gesla787883612.wordpress.com/]

Haigh, I. D., Marcos, M., Talke, S. A., Woodworth, P. L., Hunter, J. R., Hague, B. S., Arns, A., Bradshaw, E., & Thompson, P. (2022). GESLA Version 3: A major update to the global higher-frequency sea-level dataset. Geoscience Data Journal. [https://doi.org/10.1002/gdj3.174]

Woodworth, P. L., Hunter, J. R., Marcos, M., Caldwell, P., Menéndez, M., & Haigh, I. (2017). Towards a global higher-frequency sea level dataset. Geoscience Data Journal. [https://doi.org/10.1002/gdj3.42]

### Global Tide and Surge Model (GTSM)

- **Deltares - GTSM:** [https://www.deltares.nl/en/expertise/projects/global-modelling-of-tides-and-storm-surges]
- **Download from the CDS:** [https://cds.climate.copernicus.eu/datasets/sis-water-level-change-timeseries-cmip6?tab=overview]
- 
GTSM data are used to independently validate the altimetry-based storm surge results and tide gauge observations.

- **Data type:** Storm surge residuals
- **Product:** Reanalysis
- **Temporal resolution:** Hourly
- **Period:** January 2013 – December 2019 (01-01-2013 to 31-12-2019)
- **Model version:** v3

- **Download size:** Approx. 2.8 GB

## Data Preparation

1. Relocate the tide gauge files to a dedicated folder.
2. Download the required GTSM data.
3. Ensure that the downloaded files are accessible and that the file paths are configured correctly.

## Analysis Workflow

The code performs the following steps:

1. **Identify extreme events:** Detect storm surge events in the tide gauge records for the three study locations.
2. **Create an event dictionary:** Compile the dates of all identified extreme events into a dictionary for subsequent analysis.
3. **Match tide gauge locations with altimetry files:** Identify the altimetry files that correspond to each tide gauge based on spatial proximity.
4. **Analyze high-rate altimetry:** Extract and analyze coincident ADB observations to assess whether the storm surge events are detectable in the altimetry.
5. **Validate against tide gauges:** Compare the altimetry results with the corresponding tide gauge storm surge observations.
6. **Validate against GTSM:** Further compare with GTSM surge residuals.
7. 

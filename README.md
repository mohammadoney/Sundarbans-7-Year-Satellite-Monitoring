# NDVI-Time-Series-Analysis-2016-2024-

Objective:
The primary objective of this project is to assess the health and temporal dynamics of the mangrove forests within the Sundarbans region of Bangladesh. This is achieved by generating a long-term, monthly-averaged NDVI (Normalized Difference Vegetation Index) time series from 2016 to 2024. NDVI serves as a proxy for vegetation density and health, allowing for the monitoring of growth, stress, and potential changes in the mangrove ecosystem over time.

Data Acquisition:
Mangrove Baseline Data: The project used the Global Mangrove Forests Distribution (2000) dataset from Landsat to establish the baseline extent of the mangroves.
Satellite Imagery for Time-Series: The Sentinel-2 MSI Harmonized image collection was used for the primary analysis due to its high spatial resolution (10m) and frequent revisit time.
Ancillary Data: The Google Cloud Score+ dataset was integrated to provide pixel-level quality assessment for robust cloud and shadow masking.

Data Processing:
The project was executed in two distinct phases:
Phase 1: Defining the Region of Interest (ROI)
The baseline mangrove map for Bangladesh was clipped to a specific study area within the Sundarbans using a user-defined rectangle.
This raster data was then converted into a single, unified vector polygon using reduceToVectors and union(). This step was crucial to create a precise boundary that encompasses only the mangrove forest area for accurate NDVI extraction.
Phase 2: Time-Series Analysis
Filtering: The Sentinel-2 collection was filtered by date (2016-2024) and the mangrove polygon geometry.
Cloud Masking: The Cloud Score+ dataset was linked to the imagery, and a function was applied to mask out pixels with a high probability of being clouds.
NDVI Calculation: The NDVI was computed for each cloud-masked image using the Red (B4) and Near-Infrared (B8) bands.
Temporal Aggregation: The processed images were grouped by year and month, and a monthly mean NDVI composite was generated for the entire mangrove polygon. This step reduces noise and data volume, creating a clean, consistent time series.

Data Analysis:
The final output is an interactive line chart that plots the average NDVI value for the entire mangrove forest against time. This visualization allows for the analysis of:
Seasonal Patterns: Observing regular, intra-annual cycles of growth and senescence in the mangroves.
Long-Term Trends: Identifying gradual increases or decreases in overall forest health and density over the 8-year period.
Anomalies: Detecting sudden drops in NDVI that could indicate events like cyclones, drought, or illegal logging.

Potential Usage and Impact:
Environmental Monitoring: Track the impact of climate change, sea-level rise, and extreme weather events on the world's largest mangrove forest.
Conservation Management: Provide data-driven insights for government and NGOs to evaluate the effectiveness of conservation policies and reforestation efforts.
Scientific Research: Serve as a baseline for studies on carbon sequestration, biodiversity, and coastal ecosystem services.
Disaster Assessment: Quickly assess damage to the mangrove belt after major cyclones, which act as a natural bio-shield for the coastline.


# Flood and Waterlogging Analysis - São Paulo, Brazil (2013-2025)

This project utilizes Python and the Folium library to map the recurrence of hydrological events in the city of São Paulo.

### Data Sources
* **Drainage Network (SEMIL):** State-level mapping (2022, 1:50,000 scale). Source: https://semil.sp.gov.br/sma/cessao-de-dados/#1694729758233-237be3b9-66ca
* **Flood/Waterlogging Occurrences (GeoSampa/SIGRC):** Civil Defense records (2013-2026). Source: https://geosampa.prefeitura.sp.gov.br/PaginasPublicas/_SBC.aspx

### Technical Definitions (Ministry of Cities/IPT)
* **Waterlogging (Alagamento):** Temporary accumulation of water caused by failures in the urban drainage system.
* **Flooding (Inundação):** Overflow of the drainage channel into marginal areas (floodplains/várzeas).

### Data Processing & Workflow
1. **Coordinate Transformation:** The raw shapefiles lacked a defined CRS. They were first set to SIRGAS 2000 (EPSG:31983) and then reprojected to WGS84 (EPSG:4326), as Folium requires Geographic Coordinates for rendering.
2. **Filtering:** Data was filtered by the "ocorrencia" column to include only "INUNDACAO" and "ALAGAMENTO" events, excluding other unrelated categories within the dataset.
3. **Spatial Clipping:** The state-wide drainage shapefile was clipped using a Convex Hull polygon generated from the occurrence points, ensuring the drainage network fit the city's study area.
4. **Visualization:**
   * **HeatMap:** To visualize density and susceptibility trends.
   * **MarkerCluster:** To provide interactive count and exact location of each Civil Defense record.

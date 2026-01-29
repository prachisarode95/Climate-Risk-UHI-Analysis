# Urban Heat Island Detection & Cooling Infrastructure Assessment  

## Project Summary  

Urban Heat Islands (UHI) significantly impact urban livability, energy consumption, and public health.  
This project implements an **end-to-end automated geospatial pipeline** to detect UHI hotspots and evaluate cooling infrastructure using satellite-derived Land Surface Temperature (LST) and OpenStreetMap spatial features.

---

## Technical Objectives  

- Automate LST extraction and preprocessing from Landsat 9  
- Perform spatial zonal statistics on cooling infrastructure  
- Classify urban heat zones using unsupervised machine learning (K-Means)  
- Produce reproducible geospatial outputs for GIS workflows  

---

## Data Sources  

| Dataset | Source |
|----------|--------|
| Land Surface Temperature (LST) | Landsat 9 via Google Earth Engine |
| Green spaces & Water bodies | OpenStreetMap (Overpass API) |
| Administrative Boundary | Pune City GeoJSON |

---

## Technology Stack  

| Category | Tools / Libraries |
|-----------|------------------|
| Remote Sensing | Google Earth Engine, Rasterio |
| Spatial Analysis | GeoPandas, RasterStats, Shapely |
| Machine Learning | Scikit-learn (K-Means clustering) |
| Data Handling | Pandas, NumPy |
| Visualization | Matplotlib |
| Automation | Python scripting pipeline |
| Environment | Google Colab / Python |

---

## Pipeline Architecture  

### **Phase 1 – Study Area & Feature Extraction**
- Defined Pune city boundary using GeoJSON  
- Extracted green spaces and water bodies using Overpass API  

### **Phase 2 – Land Surface Temperature Processing**
- Retrieved Landsat 9 LST data from Google Earth Engine  
- Cleaned raster, masked invalid values, and clipped to city boundary  

### **Phase 3 – Cooling Feature Zonal Statistics**
- Computed mean LST for each green and water feature  
- Enriched vector datasets with temperature metrics  

### **Phase 4 – Urban Heat Island Classification**
- Applied K-Means clustering on cleaned LST raster  
- Classified the city into thermal zones (cool → extreme heat)  

### **Phase 5 – Visualization & Export**
- Generated heatmaps and spatial overlays  
- Exported GeoTIFF and GeoJSON for GIS integration  

---

## Repository Structure  
```
/Urban_Heat_Island_Detection
├── uhi.py                           # Main Python script
├── UHID.md                          # Project documentation
├── UHI
│   ├── Raw/
│   │   ├── pune_boundary.geojson    # Study area boundary
│   ├── Outputs/
│   │   ├── pune_green_water_fulltags.geojson   # Green & water features
│   │   ├── pune_cooling_with_LST.geojson       # Features enriched with LST
│   │   ├── LST.tif                            # Original LST raster
│   │   ├── LST_cleaned.tif                    # Preprocessed/masked raster
│   │   └── kmeans_uhi_clusters.tif            # Classified UHI zones
│   └── PNG/
│       ├── masked_LST_cleaned.png             # Cleaned LST preview
│       └── phase4_kmeans_clusters.png         # UHI clustering visualization
```
---

## Key Outputs  

| File | Description |
|------|-------------|
| `kmeans_uhi_clusters.tif` | Classified UHI thermal zones raster |
| `pune_cooling_with_LST.geojson` | Cooling features enriched with zonal mean temperature |
| `masked_LST_cleaned.png` | Cleaned LST visualization |
| `phase4_kmeans_clusters.png` | UHI clustering heatmap |

---

## How to Run  

```bash
# Clone repository
git clone https://github.com/prachisarode95/Urban-Heat-Island-Detection-Pipeline
cd Urban-Heat-Island-Detection-Pipeline

# Install dependencies
pip install -r requirements.txt

# Run automation pipeline
python scripts/uhi.py

```

## Requirements.txt

```txt
geemap
geopandas
rasterio
numpy
pandas
scikit-learn
rasterstats
matplotlib
shapely

```
## Key Outcomes

| File | Description |
|------|-------------|
| `kmeans_uhi_clusters.tif` | Classified UHI thermal zones raster |
| `pune_cooling_with_LST.geojson` | Cooling features enriched with zonal mean temperature |
| `masked_LST_cleaned.png` | Cleaned LST visualization |
| `phase4_kmeans_clusters.png` | UHI clustering heatmap | 

```

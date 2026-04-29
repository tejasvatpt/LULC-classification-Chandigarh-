# Chandigarh LULC Change Detection (2016-2024)

This project performs a Land Use/Land Cover (LULC) classification for Chandigarh, India, to detect infrastructure and land changes between 2016 and 2024.

It uses a data fusion approach, combining:
* **Sentinel-2 (Optical):** For spectral information.
* **Sentinel-1 (SAR):** For structural information and to see through clouds.

The final classification is generated using a Random Forest model in Google Colab.

## Project Workflow
1.  **SAR Pre-processing:** Sentinel-1 GRD data is pre-processed in ESA SNAP (Orbit File, Calibrate, Speckle Filter, Terrain Correction).
2.  **Data Preparation (Colab):** Sentinel-2 and Sentinel-1 data are loaded, aligned to a 10m grid, and stacked into a 10-band image.
3.  **Training:** A Random Forest model is trained on labeled polygons (Built-Up, Vegetation, Water, Barren).
4.  **Classification:** The model classifies the full 2016 and 2024 data stacks.
5.  **Change Detection:** The two classified maps are compared to create a final change map.

## How to Run This Project

1.  **Clone or download** this repository.
2.  **Get the Data:** The data files are not included in this repository due to their large size. You must acquire the data and place it in your Google Drive.
    * **AOI & Training Data:** `chd_boundary.geojson`, `Chandigarh_training.geojson`
    * **Sentinel-2 Bands:** (List the 2016 and 2024 bands)
    * **Sentinel-1 Processed:** `S1_2016_processed_...tif`, `S1_2024_processed_...tif`
3.  **Set up Google Drive:**
    * Create a root folder (e.g., `Chandigarh_Project`).
    * Upload this notebook (`.ipynb`) to that folder.
    * Organize all your data files according to the paths defined in **Step 0** of the notebook.
4.  **Run the Notebook:** Open the notebook in Google Colab, connect to a runtime, and run all cells.

## Requirements
The notebook will install the following:
`!pip install rasterio geopandas scikit-learn folium matplotlib scipy seaborn`

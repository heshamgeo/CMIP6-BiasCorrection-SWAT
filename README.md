Bias-Corrected CMIP6 Climate Data Processing for SWAT Modeling

This repository provides a streamlined workflow for downloading, processing, and analyzing CMIP6 climate data for hydrological modeling using the Soil and Water Assessment Tool (SWAT). The workflow includes bias correction via Quantile Mapping and prepares SWAT-compatible climate inputs, followed by an extreme event analysis of projected streamflow.

Workflow Overview

This project follows a structured pipeline using four Jupyter notebooks:

Download_clip_CMIP6.ipynb - Automates downloading and spatially clipping CMIP6 data to a study region.

Preprocessing.ipynb - Standardizes the datasets and prepares them for bias correction.

Quantile_mapping.ipynb - Performs bias correction using Quantile Mapping with observed data(CHIPS).

SWAT_inputs_Format.ipynb - Converts bias-corrected climate data into SWAT-ready input files(5 PARAMETERS).

Extreme_event_analysis.ipynb - Analyzes extreme precipitation events and return periods under future climate projections.

1⃣ Download and Clip CMIP6 Data

📌 Notebook: Download_clip_CMIP6.ipynb🔹 Purpose: Automatically downloads daily climate data from the NASA Earth Exchange (NEX) GDDP-CMIP6 dataset and clips it to the study area using a shapefile.

✅ Key Features:

Retrieves CMIP6 daily data (e.g., precipitation, temperature, humidity, wind speed, radiation).

Supports multiple models and scenarios (e.g., ssp245, ssp585).

Clips data to the study region.

Organizes downloaded files by model, scenario, and parameter.

📂 Output:

Clipped NetCDF files stored under:

D:/CMIP6-BiasCorrection-SWAT/workingfolder/clipped_data/

2⃣ Preprocessing (Standardization)

📌 Notebook: Preprocessing.ipynb🔹 Purpose: Ensures all NetCDF files have consistent time formatting and unit conversions.

✅ Key Features:

Standardizes time formats across CMIP6 datasets.

Converts units to SWAT-compatible formats:

Precipitation (kg/m²/s → mm/day)

Temperature (K → °C)

Relative Humidity (% → fraction)

Solar Radiation (W/m² → MJ/m²/day)

Saves preprocessed NetCDF files.

📂 Output:

Processed NetCDF files stored under:

D:/CMIP6-BiasCorrection-SWAT/workingfolder/standardized_data/

3⃣ Bias Correction using Quantile Mapping

📌 Notebook: Quantile_mapping.ipynb🔹 Purpose: Applies Quantile Mapping (QM) to correct biases in CMIP6 precipitation data.

✅ Key Features:

Uses observed CHIRPS precipitation data for bias correction.

Computes empirical quantiles from observed and historical model data (2015-2024).

Applies quantile mapping correction to future projections (2025-2100).

Saves bias-corrected NetCDF files for each model and scenario.

📂 Output:

Bias-corrected NetCDF files stored under:

D:/CMIP6-BiasCorrection-SWAT/workingfolder/bias_corrected/

4⃣ SWAT Climate Input Formatting

📌 Notebook: SWAT_inputs_Format.ipynb🔹 Purpose: Converts bias-corrected CMIP6 data into SWAT input format.

✅ Key Features:

Extracts climate data for each SWAT weather station from a centroid shapefile.

Generates daily SWAT input files (pcp.txt, tmp.txt, rh.txt, etc.).

Ensures consistent formatting required by SWAT.

📂 Output:

SWAT input files stored under:

D:/CMIP6-BiasCorrection-SWAT/workingfolder/SWAT_INPUT/

5⃣ Extreme Event Analysis

📌 Notebook: Extreme_event_analysis.ipynb🔹 Purpose: Analyzes annual maximum streamflow series (AMS) and estimates return periods.

✅ Key Features:

Extracts annual maximum monthly streamflow from SWAT.

Fits extreme value distributions (GEV, Gumbel, Pearson-III).

Uses bootstrap resampling (1000 iterations) for uncertainty estimation.

Generates return period curves comparing historical and future precipitation extremes.

📂 Output:

Return period plots saved in:

DD:/CMIP6-BiasCorrection-SWAT/workingfolder/Results_Plots/

🌍 Supported CMIP6 Models & Scenarios


🔧 How to Run the Workflow

Step 1: Clone the Repository

git clone https://github.com/yourusername/CMIP6-SWAT-Processing.git
cd CMIP6-SWAT-Processing

Step 2: Install Required Python Packages

Create a virtual environment and install dependencies:

pip install -r requirements.txt

Step 3: Run Each Notebook Sequentially

Execute the notebooks in order:

Download_clip_CMIP6.ipynb → Download & Clip CMIP6 Data

Preprocessing.ipynb → Standardize Time & Units

Quantile_mapping.ipynb → Apply Bias Correction

SWAT_inputs_Format.ipynb → Convert Data for SWAT

Extreme_event_analysis.ipynb → Analyze Extreme Events

🛠 Dependencies

The following Python libraries are required:

xarray

numpy

pandas

matplotlib

scipy

rioxarray

geopandas

netCDF4

Ensure they are installed before running the notebooks.

📚 License

This project is open-source and distributed under the Apache License.

👨‍💻 Author & Contact

Hesham Elhaddad📧 Email: h.elhaddad@wmich 🌐 GitHub


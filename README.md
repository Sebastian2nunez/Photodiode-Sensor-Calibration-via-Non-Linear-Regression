# Photodiode Sensor Calibration via Non-Linear Regression

### 🔬 Project Overview
This project implements an end-to-end data pipeline to calibrate and characterize **ML8511 UV Photodiode Sensors** for astrobiology simulations.

To simulate habitable zones (like TRAPPIST-1), precise control of UV radiation is critical. This solution processes raw telemetry data, corrects for dark current noise, and applies non-linear regression to derive the sensor's physical irradiance equation.

### 🛠️ Key Features
* **ETL Pipeline (Python/Pandas):** Automated ingestion of raw `.xlsx` telemetry data, featuring dark-current voltage correction and signal cleaning.
* **Non-Linear Regression (SciPy):** Optimized a power-law model (`I = K * V / S`) to characterize the sensor's decay curve ($I \propto h^{-2.17}$) with high statistical confidence.
* **Material Analysis:** Comparative study of optical transmittance between Glass and PDMS, identifying PDMS as 40% more efficient for UVB (310nm) transmission.
* **Visualization:** Automated generation of calibration plots using Matplotlib.

### 📂 Repository Structure
* `Src/`: Contains the main Python pipeline script (`sensor_calibration_pipeline.py`).
* `Data/`: Raw experimental data from UV sensors.
* `Docs/`: Technical presentation and theoretical background (`calibracion.pdf`).

### 🚀 How to Run
1. Clone the repository.
2. Install requirements: `pip install pandas numpy matplotlib scipy openpyxl`.
3. Run the pipeline:
   ```bash
   python Src/sensor_calibration_pipeline.py

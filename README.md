# Crime Analytics & FIR Management System

A modular crime management and analytics system that simulates an end-to-end **FIR (First Information Report) workflow** using **synthetically generated crime data**. The project integrates an **Oracle-backed database**, backend case management modules, machine learning–based analytics, and an interactive **Streamlit dashboard** to support crime analysis and decision-making.

**Note:** This project uses **synthetic data only** and does not contain real or sensitive crime records.


## Features

* FIR and case management (complaint registration, case assignment, investigation tracking, evidence uploads, case closure)
* Interactive Streamlit dashboard for crime visualization and analysis
* Crime type prediction and severity estimation using machine learning
* Spatial hotspot detection and density mapping
* Anomaly detection for identifying unusual crime patterns


## Project Structure

```
Crime-Management-System/
├── analytics_module/        # ML and analytics pipeline
├── modules/                 # FIR and case management modules
├── utils/                   # Helper utilities
├── assets/                  # Static assets
├── app.py                   # Streamlit dashboard
├── db_connection.py         # Oracle DB connection
├── requirements.txt
└── README.md
```

## Machine Learning & Analytics

* Crime type prediction using Random Forest with 5-fold cross-validation (~75–80% accuracy on synthetic data)
* Crime severity estimation using Random Forest regression (low RMSE)
* Hotspot detection using K-Means and DBSCAN
* Crime density visualization using Kernel Density Estimation
* Anomaly detection using Isolation Forest (~5% anomaly rate)




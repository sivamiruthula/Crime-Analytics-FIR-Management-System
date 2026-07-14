# 🛡️ Crime Analytics & FIR Management System

A comprehensive modular crime management platform that combines **FIR (First Information Report) workflow management**, **Oracle database integration**, and **advanced ML analytics** to provide law enforcement agencies with intelligent crime tracking, investigation management, and predictive analytics capabilities.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Project Structure](#project-structure)
- [Technology Stack](#technology-stack)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Database Configuration](#database-configuration)
- [Running the Application](#running-the-application)
- [Module Documentation](#module-documentation)
- [Analytics Pipeline](#analytics-pipeline)
- [Usage Guide](#usage-guide)
- [Troubleshooting](#troubleshooting)
- [License](#license)

---

## 🎯 Overview

This system provides a complete solution for crime management with:
- **Centralized Case Management**: Register, track, and manage FIR complaints
- **Investigation Tracking**: Assign investigators and monitor case progress
- **Evidence Management**: Upload and manage digital evidence with chain of custody
- **ML-Powered Analytics**: 
  - Crime type prediction
  - Crime severity estimation
  - Hotspot detection & mapping
  - Anomaly detection
  - Temporal analysis
- **Interactive Dashboard**: Real-time visualization of crime patterns and trends

---

## ✨ Key Features

### 1. **Complaint Registration Module**
   - Register new crime complaints
   - Capture complainant details
   - Automatic FIR generation
   - Complaint categorization by crime type

### 2. **Case Assignment Module**
   - Assign cases to investigators
   - Track assignment history
   - Reassign cases as needed
   - Resource allocation management

### 3. **Investigation Module**
   - Track investigation progress
   - Record investigation findings
   - Update case status
   - Timeline management

### 4. **Evidence Management**
   - Upload digital evidence (files, images, documents)
   - Track evidence chain of custody
   - Evidence categorization
   - Secure evidence storage

### 5. **Case Closure Module**
   - Close resolved cases
   - Generate closure reports
   - Archive case data
   - Resolution tracking

### 6. **Crime Analytics**
   - **Crime Prediction**: Predict future crime types based on patterns
   - **Severity Estimation**: Estimate crime severity levels
   - **Hotspot Detection**: Identify crime hotspots using KDE and clustering
   - **Anomaly Detection**: Detect unusual crime patterns
   - **Temporal Analysis**: Track crime trends over time
   - **Interactive Maps**: Visualize crime locations and clusters
   - **Dashboard**: Real-time analytical insights

### 7. **Reporting & Visualization**
   - Generate analytical reports
   - Interactive Plotly dashboards
   - Crime hotspot heatmaps
   - Temporal trend charts
   - Summary statistics

---

## 📁 Project Structure

```
Crime-Analytics-FIR-Management-System/
│
├── app.py                          # Main Streamlit application entry point
├── db_connection.py                # Oracle database connection management
├── filemanager.py                  # File upload and evidence management
├── check_tables.py                 # Database table verification script
├── verify_tables.py                # Database setup verification
├── test_connection.py              # Test Oracle DB connectivity
│
├── requirements.txt                # Python dependencies
├── LICENSE                         # MIT License
├── README.md                       # This file
│
├── modules/                        # Core application modules
│   ├── __init__.py
│   ├── complaint_registration.py   # Complaint filing interface
│   ├── case_assignment.py          # Case assignment management
│   ├── investigation.py            # Investigation tracking
│   ├── case_closure.py             # Case closure processing
│   ├── evidence_upload.py          # Evidence upload interface
│   ├── reports.py                  # Report generation
│   └── Report.py                   # Analytics & visualization
│
├── analytics_module/               # ML Analytics Pipeline
│   ├── main.py                     # Pipeline orchestration
│   ├── data/                       # Data storage
│   │   ├── raw/                    # Raw synthetic data
│   │   ├── processed/              # Processed data
│   │   └── models/                 # Trained ML models
│   ├── outputs/                    # Generated outputs
│   │   ├── maps/                   # Interactive crime maps
│   │   ├── charts/                 # Statistical charts
│   │   └── reports/                # Analysis reports
│   └── src/                        # Analytics source code
│       ├── data_generator.py       # Synthetic data generation
│       ├── data_preprocessor.py    # Data cleaning & features
│       ├── model_trainer.py        # ML model training
│       └── visualizer.py           # Visualization creation
│
├── utils/                          # Utility modules
│   ├── session_state.py            # Streamlit session management
│   └── charts.py                   # Chart utilities
│
└── assets/                         # Static assets (images, icons)
```

---

## 🛠 Technology Stack

### Backend & Frontend
- **Streamlit**: Interactive web dashboard
- **Python 3.8+**: Core programming language

### Database
- **Oracle Database**: Primary data storage (XE/PDB)
- **OracleDB Python Driver**: Database connectivity

### Data Processing & ML
- **Pandas**: Data manipulation
- **NumPy**: Numerical computing
- **Scikit-learn**: Machine learning models
- **Folium**: Interactive mapping
- **Plotly**: Interactive visualizations
- **Matplotlib**: Statistical plots
- **OpenCV**: Image processing

### Utilities
- **python-dotenv**: Environment variable management
- **Pillow**: Image handling

---

## 📦 Prerequisites

### System Requirements
- **Python**: 3.8 or higher
- **Oracle Database**: 19c, 21c, or 23c (Enterprise/Express/XE)
- **Disk Space**: Minimum 2GB for data and models
- **RAM**: Minimum 4GB (8GB recommended)

### Required Software
- Oracle Database with accessible PDB (Pluggable Database)
- Python virtual environment
- Oracle Instant Client (optional, for connection setup)

---

## 🚀 Installation & Setup

### Step 1: Clone or Download Repository

```bash
git clone https://github.com/sivamiruthula/Crime-Analytics-FIR-Management-System.git
cd Crime-Analytics-FIR-Management-System
```

### Step 2: Create Virtual Environment

```bash
# Windows
python -m venv frontend_env
frontend_env\Scripts\activate

# macOS/Linux
python3 -m venv frontend_env
source frontend_env/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

**requirements.txt** includes:
```
streamlit
streamlit-option-menu
pandas
mysql-connector-python
Pillow
plotly
matplotlib
numpy
folium
opencv-python
python-dotenv
oracledb
```

### Step 4: Configure Environment Variables

Create a `.env` file in the project root:

```env
# Oracle Database Configuration
DB_USER=system
DB_PASSWORD=your_password
DB_DSN=localhost:1521/XEPDB1
```

Or update directly in `db_connection.py`:

```python
DB_USER = "system"
DB_PASSWORD = "your_password"
DB_DSN = "localhost:1521/XEPDB1"
```

---

## 🗄️ Database Configuration

### Step 1: Oracle Database Setup

1. **Install Oracle Database** (if not already installed)
   - [Oracle Database Express Edition (XE)](https://www.oracle.com/database/technologies/xe-downloads.html)
   - Or use existing Oracle instance

2. **Verify Connection**
   ```bash
   python test_connection.py
   ```
   Expected output:
   ```
   ✅ CONNECTION SUCCESSFUL!
   Connected as: system
   ```

### Step 2: Create Required Tables

The system requires the following tables in Oracle:

```sql
-- CASE_TABLE: Main case information
CREATE TABLE case_table (
    case_id NUMBER PRIMARY KEY,
    complaint_id NUMBER,
    crime_type VARCHAR2(100),
    case_status VARCHAR2(50),
    created_date DATE,
    updated_date DATE
);

-- COMPLAINANT: Complainant details
CREATE TABLE complainant (
    complainant_id NUMBER PRIMARY KEY,
    name VARCHAR2(100),
    contact VARCHAR2(20),
    address VARCHAR2(500),
    case_id NUMBER REFERENCES case_table(case_id)
);

-- CRIME_TYPE: Crime categories
CREATE TABLE crime_type (
    crime_type_id NUMBER PRIMARY KEY,
    crime_name VARCHAR2(100),
    description VARCHAR2(500)
);

-- USERLOGIN: User authentication
CREATE TABLE userlogin (
    user_id NUMBER PRIMARY KEY,
    username VARCHAR2(50) UNIQUE,
    password VARCHAR2(100),
    role VARCHAR2(50)
);

-- INVESTIGATION: Investigation records
CREATE TABLE investigation (
    investigation_id NUMBER PRIMARY KEY,
    case_id NUMBER REFERENCES case_table(case_id),
    investigator_id NUMBER,
    findings VARCHAR2(1000),
    status VARCHAR2(50)
);

-- CASE_ASSIGNMENT_HISTORY: Assignment tracking
CREATE TABLE case_assignment_history (
    assignment_id NUMBER PRIMARY KEY,
    case_id NUMBER REFERENCES case_table(case_id),
    investigator_id NUMBER,
    assigned_date DATE,
    status VARCHAR2(50)
);

-- EVIDENCE: Evidence records
CREATE TABLE evidence (
    evidence_id NUMBER PRIMARY KEY,
    case_id NUMBER REFERENCES case_table(case_id),
    evidence_type VARCHAR2(100),
    description VARCHAR2(500),
    collected_by VARCHAR2(100),
    storage_location VARCHAR2(200),
    chain_of_custody VARCHAR2(500),
    status VARCHAR2(50)
);

-- EVIDENCE_FILE: Digital evidence storage
CREATE TABLE evidence_file (
    file_id NUMBER PRIMARY KEY,
    evidence_id NUMBER REFERENCES evidence(evidence_id),
    filename VARCHAR2(200),
    file_type VARCHAR2(50),
    file_size NUMBER,
    file_content BLOB,
    uploaded_by VARCHAR2(100),
    description VARCHAR2(500),
    upload_date DATE
);

-- SUSPECT: Suspect information
CREATE TABLE suspect (
    suspect_id NUMBER PRIMARY KEY,
    case_id NUMBER REFERENCES case_table(case_id),
    name VARCHAR2(100),
    description VARCHAR2(500)
);

-- WITNESS: Witness information
CREATE TABLE witness (
    witness_id NUMBER PRIMARY KEY,
    case_id NUMBER REFERENCES case_table(case_id),
    name VARCHAR2(100),
    contact VARCHAR2(20),
    statement VARCHAR2(1000)
);
```

### Step 3: Verify Database Setup

```bash
python check_tables.py
python verify_tables.py
```

---

## ▶️ Running the Application

### Option 1: Run Main Streamlit Dashboard

```bash
streamlit run app.py
```

The application will open at `http://localhost:8501`

**Available Pages:**
- 🏠 Home - Dashboard overview
- ✏️ Complaint Registration - File new complaints
- 👤 Case Assignment - Assign cases to investigators
- 🔍 Investigation - Track investigation progress
- ✅ Case Closure - Close resolved cases
- 📄 Reports - Generate case reports
- 📤 Evidence Upload - Upload digital evidence
- 📊 Crime Analytics - View ML analytics & insights

### Option 2: Run Analytics Pipeline

```bash
# Run complete pipeline (generate data, preprocess, train models, visualize)
cd analytics_module
python main.py

# Or run specific steps
python main.py generate      # Generate demo data only
python main.py preprocess    # Preprocess data only
python main.py train         # Train models only
python main.py visualize     # Create visualizations only
python main.py quick         # Quick analysis from existing data
python main.py help          # Show usage guide
```

**Output Locations:**
- 📊 Interactive maps: `analytics_module/outputs/maps/`
- 📈 Charts: `analytics_module/outputs/charts/`
- 📄 Reports: `analytics_module/outputs/reports/`
- 🤖 Models: `analytics_module/data/models/`

---

## 📚 Module Documentation

### 1. **app.py** - Main Application
- Entry point for Streamlit application
- Handles page routing and navigation
- Integrates all modules

```bash
streamlit run app.py
```

### 2. **db_connection.py** - Database Management
- Persistent Oracle database connection
- Safe query execution
- Connection pooling and session management

**Key Functions:**
- `get_connection()`: Get active database connection
- `execute_query(query, params)`: Execute INSERT/UPDATE/DELETE
- `fetch_data(query, params)`: Fetch query results
- `check_tables_exist()`: Verify table availability

### 3. **filemanager.py** - Evidence File Management
- Handles file uploads to database
- Manages BLOB storage
- Chain of custody tracking

**Key Functions:**
- `insert_evidence_record()`: Create evidence record
- `insert_evidence_file()`: Store file in database

### 4. **Modules/**

#### complaint_registration.py
- Register new FIR complaints
- Capture complainant information
- Crime type selection

#### case_assignment.py
- Assign cases to investigators
- Manage assignment history
- Track assignment status

#### investigation.py
- Update investigation progress
- Record findings
- Modify case status

#### evidence_upload.py
- Upload evidence files
- Track chain of custody
- Organize evidence by case

#### case_closure.py
- Close resolved cases
- Generate closure reports
- Archive case data

#### Report.py & reports.py
- Generate analytical reports
- Create visualizations
- Display dashboards

### 5. **Analytics Pipeline** (analytics_module/)

#### data_generator.py
- Generate synthetic crime data
- 5000+ realistic crime records
- Feature-rich datasets

#### data_preprocessor.py
- Data cleaning and validation
- Feature engineering
- Missing value handling
- Aggregated feature creation

#### model_trainer.py
**Models Trained:**
1. **Random Forest Classifier** - Crime type prediction
2. **Random Forest Regressor** - Severity prediction
3. **K-Means Clustering** - Hotspot identification
4. **DBSCAN** - Density-based clustering
5. **Isolation Forest** - Anomaly detection
6. **Kernel Density Estimator** - Crime density mapping

#### visualizer.py
- Interactive crime hotspot heatmaps
- Cluster visualization maps
- Temporal trend analysis
- Interactive Plotly dashboards
- Statistical charts
- Anomaly visualizations

---

## 🧠 Analytics Pipeline

### Pipeline Workflow

```
1. DATA GENERATION
   ↓
   Synthetic crime data with realistic patterns
   
2. DATA PREPROCESSING
   ↓
   Cleaning, feature engineering, aggregation
   
3. MODEL TRAINING
   ↓
   Train 6 different ML models
   
4. VISUALIZATION & REPORTING
   ↓
   Create maps, charts, dashboards, reports
```

### Generated Outputs

```
outputs/
├── maps/
│   ├── crime_hotspot_heatmap.html      # Interactive heatmap
│   └── crime_clusters_map.html         # Cluster visualization
├── charts/
│   ├── temporal_analysis.png           # Time-based trends
│   └── anomaly_detection.png           # Anomalies visualization
└── reports/
    ├── interactive_dashboard.html      # Full analytics dashboard
    ├── summary_statistics.txt          # Statistical summary
    └── detected_anomalies.csv          # Anomalous cases
```

---

## 📖 Usage Guide

### Managing Complaints

1. Navigate to **Complaint Registration**
2. Fill in complainant details
3. Select crime type
4. Submit complaint
5. System generates automatic FIR ID

### Assigning Cases

1. Go to **Case Assignment**
2. Select case from list
3. Choose investigator
4. Set priority
5. Confirm assignment

### Tracking Investigations

1. Open **Investigation** module
2. Select case
3. Update findings
4. Modify status
5. Track timeline

### Uploading Evidence

1. Navigate to **Evidence Upload**
2. Select case
3. Upload file(s)
4. Add description
5. Track chain of custody

### Viewing Analytics

1. Click **Crime Analytics**
2. View tabs:
   - 🗺️ Hotspot Maps - Geographic distribution
   - 📌 Cluster Map - Crime clusters
   - 📈 Temporal Charts - Time trends
   - 📑 Summary Dashboard - All analytics

---

## 🐛 Troubleshooting

### Issue: "Database connection failed"

**Solution:**
```bash
# 1. Verify database is running
# 2. Check credentials in db_connection.py
# 3. Test connection
python test_connection.py

# 4. Verify DSN format: hostname:port/pdb_name
# Example: localhost:1521/XEPDB1
```

### Issue: "Missing required tables"

**Solution:**
```bash
# 1. Run database verification
python verify_tables.py

# 2. Create tables using provided SQL scripts
# 3. Grant necessary permissions to user:
GRANT CREATE TABLE TO system;
```

### Issue: "ImportError: No module named..."

**Solution:**
```bash
# Reinstall dependencies
pip install -r requirements.txt

# Or install specific package
pip install streamlit oracledb pandas
```

### Issue: "Analytics module not finding data files"

**Solution:**
```bash
# Ensure correct path structure
cd analytics_module
python main.py generate  # Generate data first
```

### Issue: "Streamlit app not responding"

**Solution:**
```bash
# Clear Streamlit cache
rm -rf ~/.streamlit/

# Restart app
streamlit run app.py
```

---

## 📊 System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    STREAMLIT FRONTEND                       │
│  (Web-based UI for case management & analytics)             │
└────────────────────────┬────────────────────────────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
   ┌────▼──────┐  ┌─────▼──────┐  ┌──────▼──────┐
   │  Modules  │  │  Analytics │  │   Utils     │
   │  Package  │  │  Pipeline  │  │   Package   │
   └────┬──────┘  └─────┬──────┘  └──────┬──────┘
        │                │                │
        └────────────────┼────────────────┘
                         │
         ┌───────────────▼───────────────┐
         │   DATABASE CONNECTION LAYER   │
         │  (OracleDB Python Driver)     │
         └───────────────┬───────────────┘
                         │
         ┌───────────────▼───────────────┐
         │    ORACLE DATABASE (19c+)     │
         │  - Case Management Tables     │
         │  - User & Investigation Data  │
         │  - Evidence & BLOB Storage    │
         └───────────────────────────────┘
```

---

## 🔐 Security Considerations

1. **Database Credentials**: Store in `.env` file (not in code)
2. **User Authentication**: Implement OAuth/SSO for production
3. **Evidence Privacy**: Encrypt BLOB data at rest
4. **Access Control**: Implement role-based access control (RBAC)
5. **Audit Logging**: Track all data modifications
6. **Data Backup**: Regular Oracle database backups

---

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Push to branch
5. Create Pull Request

---

## 📝 License

This project is licensed under the **MIT License** - see [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Siva Miruthula**  
GitHub: [@sivamiruthula](https://github.com/sivamiruthula)

---

## 📞 Support & Contact

For issues, questions, or suggestions:
- Open an Issue on GitHub
- Contact through repository discussions

---

## 📚 References & Resources

- [Streamlit Documentation](https://docs.streamlit.io/)
- [Oracle Database Documentation](https://docs.oracle.com/en/database/)
- [Scikit-learn Documentation](https://scikit-learn.org/)
- [Folium Documentation](https://python-visualization.github.io/folium/)
- [Plotly Documentation](https://plotly.com/python/)

---

**Last Updated**: 2026-07-14  
**Version**: 1.0.0

# 769 Final Water Quality Detection

## Overview
This project implements a water potability prediction pipeline entirely within a single Jupyter Notebook (`769_Group6_final.ipynb`). It automatically downloads the dataset, preprocesses it, trains multiple models (classical ML, ensemble methods, simple deep learning), performs hyperparameter tuning and SMOTE balancing, then compares model performance with visualizations.

## Repository Structure
```
├── 769_Group6_final.ipynb    # Main experiment notebook  
├── requirements.txt          # Python dependencies  
└── README.md                 # This file  
```

## Environment Setup
1. **Clone the repository**  
   ```bash
   git clone https://your.repo.url/Group6-WaterQuality.git
   cd Group6-WaterQuality
   ```
2. **(Optional) Create & activate a virtual environment**  
   ```bash
   python3 -m venv venv
   source venv/bin/activate    # Linux / macOS
   venv\Scripts\activate     # Windows
   ```
3. **Install dependencies**  
   ```bash
   pip install -r requirements.txt
   ```

## Data Download
The notebook uses the Kaggle API to fetch the “Water Potability” dataset automatically—no manual download required.  
1. Place your Kaggle API token file (`kaggle.json`) in `~/.kaggle/` and set its permissions to `600`.  
2. The notebook calls:
   ```python
   from kaggle.api.kaggle_api_extended import KaggleApi
   api = KaggleApi()
   api.authenticate()
   api.dataset_download_files("adityakadiwal/water-potability", path="data/", unzip=True)
   ```
   which produces `data/water_potability.csv`.

## Running the Notebook
1. **Launch Jupyter**  
   ```bash
   jupyter notebook
   ```
2. **Open** `769_Group6_final.ipynb` in your browser.  
3. **Execute** cells in order; the notebook will:
   - Load and preprocess data (missing values, outliers, scaling)
   - Train baseline models (Logistic Regression, Naive Bayes, etc.)
   - Train and tune ensemble models (Random Forest, XGBoost, LightGBM) via Grid Search
   - Apply SMOTE to balance classes
   - Train a simple deep learning classifier
   - Compute and display Accuracy, F1-Score, ROC-AUC metrics
   - Plot comparative bar charts and ROC curves

## FAQ
- **ModuleNotFoundError: No module named ‘kaggle’**  
  Ensure you’ve installed `kaggle` via `pip install -r requirements.txt` and placed `kaggle.json` correctly.
- **PermissionError on kaggle.json**  
  Run `chmod 600 ~/.kaggle/kaggle.json` to secure the file.
- **Notebook crashes or hangs**  
  Try restarting the kernel in a fresh Python ≥3.8 virtual environment.

## Contact
For questions or feedback, please reach out to the project lead:  
- **Name:** XXX  
- **Email:** your_email@domain.com  

Enjoy reproducing the experiments!

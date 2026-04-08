# Yelp Dataset Analysis

A comprehensive machine learning project analyzing the Yelp Academic Dataset with data exploration, feature engineering, and classification modeling to predict business characteristics.

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Features](#features)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [Methodology](#methodology)
- [Results](#results)
- [Model Performance](#model-performance)

## Overview

This project performs an in-depth analysis of the Yelp Academic Dataset, focusing on data preprocessing, exploratory data analysis (EDA), feature extraction, and machine learning classification. The goal is to build and compare multiple machine learning models to predict business attributes and patterns.

## Dataset

The project uses the **Yelp Academic Dataset**, which includes:

- **Business Information**: Business IDs, names, addresses, ratings, review counts, and operational status
- **Attributes**: Business features like WiFi availability, parking, delivery options, alcohol service, etc.
- **Geographic Data**: Latitude and longitude coordinates
- **Categories**: Business types and classifications
- **Operating Hours**: Business schedule information

### Data Processing

The dataset is processed in chunks (1000 records at a time) to handle large file sizes efficiently:
- Unnecessary columns (like postal code) are dropped during loading
- JSON data is parsed and converted to pandas DataFrames
- Data is cleaned and prepared for analysis and modeling

## Features

- **Data Loading**: Efficient chunked reading of JSON formatted Yelp dataset
- **Exploratory Data Analysis**: 
  - Statistical summaries
  - Distribution analysis
  - Correlation analysis
  - Data visualization with matplotlib and seaborn
- **Feature Engineering**: Extraction and transformation of business attributes
- **Machine Learning Classification**:
  - Logistic Regression
  - Decision Tree Classifier
  - Random Forest Classifier
  - Support Vector Machines (SVM)
- **Hyperparameter Tuning**: GridSearchCV for optimal model parameters
- **Model Evaluation**: Accuracy scoring and cross-validation

## Installation

### Prerequisites

- Python 3.7+
- Jupyter Notebook or JupyterLab

### Dependencies

```bash
pip install numpy pandas seaborn matplotlib scikit-learn
```

### Clone Repository

```bash
git clone https://github.com/yourusername/yelp-dataset-analysis.git
cd yelp-dataset-analysis
```

## Project Structure

```
yelp-dataset-analysis/
├── README.md
├── Yelp_Dataset_Analysis.ipynb
├── Yelp/
│   └── yelp_academic_dataset_business.json
├── requirements.txt
└── data/
    └── (processed data files)
```

## Usage

### Running the Analysis

1. **Start Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```

2. **Open the notebook**:
   - Navigate to `Yelp_Dataset_Analysis.ipynb`
   - Run cells sequentially from top to bottom

3. **Dataset Setup**:
   - Ensure the Yelp dataset JSON file is located at `Yelp/yelp_academic_dataset_business.json`
   - Download from [Yelp Dataset](https://www.yelp.com/dataset) if needed

### Key Steps in the Notebook

1. **Data Import**: Load JSON dataset with chunked reading
2. **Data Exploration**: Analyze structure, types, and distributions
3. **Feature Extraction**: Create feature matrix from business attributes
4. **Train/Test Split**: 70% training, 30% testing
5. **Model Training**: Train four classification models with grid search
6. **Evaluation**: Compare accuracy scores and best parameters

## Methodology

### Data Preprocessing

- **Chunked Loading**: Read 1000 records at a time to manage memory efficiently
- **Column Selection**: Drop unnecessary columns like postal codes
- **Attribute Extraction**: Convert nested attribute dictionaries into binary features

### Feature Engineering

The analysis extracts 15 key features from business attributes (columns 12-27):
- Parking availability
- WiFi status
- Delivery options
- Alcohol service
- Outdoor seating
- Accepts credit cards
- Good for kids
- Catering services
- Noise level
- And more...

### Model Training Strategy

Each model is trained using GridSearchCV with 5-fold cross-validation:

**Hyperparameter Grids:**
- **Logistic Regression**: C values [0.1, 1, 10], penalties [l1, l2]
- **Decision Tree**: max_depth [1, 5, 10], min_samples_split [2, 5, 10]
- **Random Forest**: n_estimators [100, 200, 500], max_depth [10, 20, None]
- **SVM**: C values [0.1, 1, 10], kernels [linear, rbf]

## Results

### Model Comparison

| Model | Best Parameters | Accuracy Score |
|-------|-----------------|-----------------|
| Logistic Regression | C=0.1, penalty='l2' | **85.60%** |
| Decision Tree | max_depth=10, min_samples_split=10 | 85.01% |
| Random Forest | max_depth=10, n_estimators=200 | **85.99%** ✓ |
| Support Vector Machines | C=1, kernel='rbf' | 85.79% |

### Key Findings

- **Best Performer**: Random Forest achieved the highest accuracy at **85.99%**
- **Consistent Performance**: All models achieved similar accuracy (~85%), indicating reliable predictions
- **Feature Importance**: The extracted business attributes provide strong predictive signals
- **Stability**: Cross-validation helped prevent overfitting

## Model Performance

### Accuracy Scores
- Random Forest leads with **85.99%** accuracy
- Support Vector Machines follow closely at **85.79%**
- Logistic Regression achieves **85.60%**
- Decision Tree baseline at **85.01%**

### Evaluation Metrics Used
- Accuracy Score: Percentage of correct predictions
- GridSearchCV: 5-fold cross-validation for robust performance estimation
- Train-Test Split: 70-30 split to evaluate generalization

## Dependencies

```txt
numpy
pandas
seaborn
matplotlib
scikit-learn
```

## Requirements File

Create `requirements.txt`:
```bash
numpy>=1.19.0
pandas>=1.1.0
seaborn>=0.11.0
matplotlib>=3.3.0
scikit-learn>=0.24.0
```

Install all dependencies:
```bash
pip install -r requirements.txt
```


## References

- [Yelp Dataset Official Documentation](https://www.yelp.com/dataset)
- [scikit-learn Documentation](https://scikit-learn.org/)
- [Pandas Documentation](https://pandas.pydata.org/)

---

**Last Updated**: 2024
**Python Version**: 3.9.7
**Status**: Active Development

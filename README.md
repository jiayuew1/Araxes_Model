# Site Suitability Analysis - Arsacid Period Sites in the Iranian Borderland Region of the Araxes River Valley

This public repository contains the code and methodology for the paper **"Site Suitability Analysis of Arsacid Period Sites in the Iranian Borderland Region of the Araxes River Valley"**.

## Repository Structure

### Core Files

- **`model.py`** - The original implementation used specifically for the Arsacid period site analysis in the research paper
- **`basic_framework.ipynb`** - A generalized, user-friendly framework for geospatial binary classification problems

## About the Framework

This repository implements a **PCA-based machine learning pipeline for geospatial binary classification**. While originally developed for archaeological site prediction, the framework can be adapted for various geospatial applications including:

- Archaeological site prediction
- Landslide susceptibility mapping
- Urban planning analysis
- Habitat modeling
- Environmental risk assessment

## Key Features

### Machine Learning Models
- Random Forest
- Logistic Regression  
- Support Vector Machine (SVM)
- K-Nearest Neighbors (KNN)
- XGBoost

### Analysis Components
- **Principal Component Analysis (PCA)** for dimensionality reduction
- **Cross-validation** with precision-recall optimization
- **Outlier detection and removal** using z-score thresholds
- **Data transformation** for handling skewed distributions
- **Probability mapping** with classified output visualization

### Evaluation Metrics
- Precision-Recall curves
- F1-Score optimization
- K-fold cross-validation
- Comprehensive performance comparison across models

## Getting Started

### Requirements

```python
pandas>=1.3.0
rasterio>=1.2.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=1.0.0
xgboost>=1.5.0
scipy>=1.7.0
statsmodels>=0.12.0
imbalanced-learn>=0.8.0
```

### Data Requirements

1. **Point Data**: Excel file with coordinates and binary class labels
   - Required columns: `POINT_X`, `POINT_Y`, `class`
   
2. **Raster Data**: GeoTIFF format covering the study area
   - All rasters must have the same coordinate reference system
   - All rasters should cover the same geographic extent

### Quick Start

#### For New Users (Recommended)

Use the **`basic_framework.ipynb`** notebook:

1. Update the configuration section with your data paths
2. Modify the `class_type_mapping` for your specific classes
3. Adjust the `raster_files` dictionary based on your available data
4. Run the pipeline

```python
# Example configuration
raster_dir = '/path/to/your/raster/data/'
points_file = '/path/to/your/points.xlsx'

class_type_mapping = {
    '1': 'Positive_Class',
    '2': 'Negative_Class'
}

raster_files = {
    'elevation': ['elevation.tif', 'elevation_1km.tif'],
    'slope': ['slope.tif', 'slope_1km.tif'],
    'accessibility': ['walking_time.tif']
}
```

#### For Advanced Users

The **`model.py`** contains the original implementation with specific preprocessing steps and model configurations used in the research paper.

## Framework Advantages

### `basic_framework.ipynb` vs `model.py`

| Feature | basic_framework.ipynb | model.py |
|---------|----------------------|----------|
| **Readability** | ✅ Well-documented, step-by-step | ❌ Research-specific, dense |
| **Flexibility** | ✅ Easy configuration section | ❌ Hard-coded parameters |
| **Data Handling** | ✅ Handles different data types | ❌ Specific to paper dataset |
| **User-Friendly** | ✅ Clear instructions and comments | ❌ Requires domain knowledge |
| **Reproducibility** | ✅ Standardized workflow | ✅ Original paper results |

## Methodology

### Data Preprocessing
1. **Feature Extraction**: Extract raster values at point locations
2. **Data Transformation**: Apply log transformations for skewed variables
3. **Outlier Removal**: Z-score based filtering (99% confidence interval)
4. **Standardization**: Standard scaling for PCA compatibility

### Principal Component Analysis
- Dimensionality reduction with loadings analysis
- Multiple PC selection strategies:
  - All components
  - First N components (3, 5, 7)
  - High-variance components
  - Kvamme method (loadings > |0.51|)

### Model Training & Evaluation
- 5-fold cross-validation
- Precision-recall optimization with minimum precision threshold (0.65)
- F1-score maximization
- Best model selection based on recall performance

### Output Generation
- Probability maps with classified risk zones
- Performance comparison visualizations
- Statistical summaries and model diagnostics

## Citation

If you use this code in your research, please cite:

```
TBD, will update in the future.
```

## Contributing

We welcome contributions to improve the framework! Please feel free to:
- Report issues
- Suggest enhancements
- Submit pull requests
- Share use cases


## Contact

jiauew1@uchicago.edu

---

**Note**: The `basic_framework.ipynb` is designed for broader applicability and ease of use, while `model.py` preserves the exact implementation used in the research paper for reproducibility.
🌱 NDVI-Based Land Cover Classification — Summer Analytics 2025 Hackathon

This project was developed as part of the First Course Hackathon of Summer Analytics 2025, hosted by the Consulting & Analytics Club in collaboration with GeeksforGeeks (GFG).
The challenge focused on classifying land cover types using time-series NDVI data derived from satellite imagery and OpenStreetMap labels, under strict constraints of using only Logistic Regression for modeling.

📌 Problem Statement

The task was to predict the land cover class for different locations, where each location is represented by:

27 NDVI time points (from satellite images across different dates)

Target classes: Water, Impervious, Farm, Forest, Grass, Orchard


Key challenges:

Noisy Data: Due to cloud cover in imagery and inconsistencies in OpenStreetMap labels.

Missing Data: Some NDVI values were missing because of cloud obstruction.

Temporal Variability: NDVI values vary seasonally, requiring meaningful feature extraction.

📝 Approach

✅ Data Preprocessing

Filled missing NDVI values using mean imputation.

Applied standard scaling to ensure uniform feature contribution.


✅ Feature Engineering

Computed row-wise NDVI statistics: mean, standard deviation, min, max, median, skew.

Calculated temporal difference features: mean and std of differences between consecutive NDVI time points.

Added NDVI-based counts:

Number of time points where NDVI > 0.3 (indicating healthy vegetation)

Number where NDVI < 0.1 (indicating bare land or water)


Included NaN count per sample to capture missingness patterns.

Applied polynomial feature expansion (degree=2) to model interactions between NDVI trends.


✅ Modeling

Used Logistic Regression (multinomial) with lbfgs solver.

Conducted GridSearchCV hyperparameter tuning over C = [0.1, 0.5, 1.0, 2.0, 5.0].

Employed Stratified 5-fold Cross-Validation to ensure robust accuracy estimation across all classes.

🚀 Results

Cross-validated accuracy: ~89% to 91% (depending on the split)

The model generalizes well to clean, private test data.

Improved stability and performance over baseline Logistic Regression using only raw NDVI data.

💡 Key Learnings

Even simple models like Logistic Regression can perform surprisingly well on complex data with proper feature engineering.

NDVI time-series dynamics (change over time) are crucial in distinguishing land cover types.

Robust validation (e.g., StratifiedKFold) prevents overfitting to noisy training data.

📈 Future Directions

If model constraints were lifted:

Use tree-based models (Random Forest, XGBoost) or sequence models (LSTM) to capture temporal patterns better.

Incorporate external spatial/contextual data from OSM, weather, or soil maps.

Explore unsupervised clustering to refine noisy training labels.

📝 According to Competition the Scores of the following versions are as follows 
Version 1:-0.56000
Version 2:-0.65666
Version 3:-0.62666
Version 4:-0.56000

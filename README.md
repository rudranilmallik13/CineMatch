# 🎬 Netflix Movie Recommendation System

## 📌 Overview
This project builds a **movie recommendation system** using machine learning on a subset of the **Netflix Prize dataset**.

The goal is to:
- Predict user ratings for movies
- Recommend movies users are likely to enjoy

The project covers:
- Data loading & preprocessing
- Exploratory Data Analysis (EDA)
- Feature engineering
- Multiple recommendation algorithms
- Model comparison and evaluation

---

## 📂 Dataset
The dataset is derived from the **Netflix Prize dataset**:
- `combined_data_*.txt` → User–movie ratings
- `movie_titles.csv` → Movie metadata

### 📊 Data Statistics
| Metric | Count |
|------|------|
| Total Ratings | 100,480,507 |
| Total Users | 480,189 |
| Total Movies | 17,770 |

### 🔀 Data Split
**Train (80%)**
- Ratings: 80,384,405  
- Users: 405,041  
- Movies: 17,424  

**Test (20%)**
- Ratings: 20,096,102  
- Users: 349,312  
- Movies: 17,757  

---

## 📈 Exploratory Data Analysis (EDA)
Key insights from EDA:

- ⭐ **Ratings Distribution**: Mostly 3, 4, and 5 stars (4 is most common)
- 📅 **Ratings Over Time**: Monthly trend visible
- 👤 **Ratings per User**: Top 5% users contribute most ratings
- 🎥 **Ratings per Movie**: Few popular movies get most ratings
- 📆 **Day of Week**: No major difference in average ratings
- 🧩 **Sparsity**: User–movie matrix is over **99% sparse**
- ❄️ **Cold Start Problem**: New users/movies exist in test set

---

## 🧠 Methodology

### 🔧 Feature Engineering (for XGBoost)
For each (user, movie) pair, the following features were created:

- **Global Average Rating**
- **Similar User Ratings** (`sur1` – `sur5`)
- **Similar Movie Ratings** (`smr1` – `smr5`)
- **User Average Rating (UAvg)**
- **Movie Average Rating (MAvg)**
- **BaselineOnly Prediction**
- **KNNBaseline (User–User) Prediction**
- **KNNBaseline (Movie–Movie) Prediction**
- **SVD Prediction**
- **SVD++ Prediction**

---

## 🤖 Models Applied

### Collaborative Filtering (Surprise Library)
- BaselineOnly
- KNNBaseline (User–User)
- KNNBaseline (Movie–Movie)
- SVD
- SVD++

### Gradient Boosting
- XGBoost with engineered features
- XGBoost with Surprise model predictions
- Ensemble XGBoost models

---

## 📊 Results & Model Comparison

Due to computation limits, models were trained on a **smaller sample**:
- Train: 10,000 users × 1,000 movies
- Test: 5,000 users × 500 movies

### 📏 Evaluation Metrics
- **RMSE** (Root Mean Squared Error)
- **MAPE** (Mean Absolute Percentage Error)

| Model | Test RMSE | Test MAPE |
|-----|-----------|-----------|
| SVD | 1.0726 | 35.02 |
| KNNBaseline (User–User) | 1.0726 | 35.02 |
| KNNBaseline (Movie–Movie) | 1.0728 | 35.02 |
| SVD++ | 1.0728 | 35.04 |
| BaselineOnly | 1.0730 | 35.05 |
| XGBoost (Surprise Only) | 1.0755 | 35.02 |
| XGBoost (Initial Features) | 1.0762 | 34.50 |
| XGBoost (Initial + BaselineOnly) | 1.0763 | 34.49 |
| XGBoost (Initial + All Surprise) | 1.0764 | 34.49 |

### 📝 Observations
- **SVD and KNN-based models performed best in RMSE**
- **XGBoost ensembles showed competitive MAPE**
- Ensemble models may handle large errors better


---

## 🚀 Future Improvements
- Train on larger subsets (25K users, 3K movies)
- Hyperparameter tuning for all models
- Add time-based features (recency, trends)
- Try deep learning models (Neural Collaborative Filtering)
- Deploy as a real-time recommendation system

---

## 🛠 Tech Stack
**Python, Pandas, NumPy, Scikit-learn, Surprise, XGBoost, Matplotlib, Jupyter / Google Colab**

## ⭐ If you like this project
Give it a ⭐ on GitHub — it helps a lot!

# 🏠 Real Estate Analyzer

A full-stack machine learning web application that predicts real estate prices across major Indian cities — Bengaluru, Delhi, Chennai, and Mumbai. The project covers the complete end-to-end ML workflow: data acquisition, cleaning, EDA, model training, and deployment via a Flask web server.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Cities Supported](#cities-supported)
- [ML Workflow](#ml-workflow)
- [Installation & Setup](#installation--setup)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Screenshots](#screenshots)
- [Future Improvements](#future-improvements)

---

## Overview

Real Estate Analyzer is built to help users estimate property prices in major Indian cities by entering a few key details — location, area (sq. ft.), number of bedrooms (BHK), and bathrooms. The backend uses city-specific trained ML models to return an estimated price in real time via a REST API.

---

## Features

- 🔐 **User Authentication** — Login/logout with session management
- 🏙️ **Multi-city Support** — Separate trained models for Bengaluru, Delhi, Chennai, and Mumbai
- 📊 **EDA & Data Cleaning** — Comprehensive analysis notebooks per city
- 🤖 **ML-Powered Predictions** — City-specific models loaded on server startup
- 🌐 **Flask REST API** — Endpoints for location fetching and price prediction
- 💻 **Web Frontend** — Custom HTML/CSS interface for easy interaction

---

## Tech Stack

| Layer       | Technology                          |
|-------------|-------------------------------------|
| Language    | Python 3.x                          |
| ML/Data     | Pandas, NumPy, Scikit-learn, Matplotlib |
| Backend     | Flask                               |
| Frontend    | HTML, CSS, JavaScript               |
| Notebooks   | Jupyter Notebook                    |
| Data Format | CSV                                 |

---

## Project Structure

```
Real-Estate_Analyzer/
│
├── Images/                        # UI screenshots / assets
├── templates/                     # HTML templates (Jinja2)
│   ├── login.html
│   └── city_price_prediction.html
│
├── Bengaluru_House_Data.csv       # Raw dataset – Bengaluru
├── Chennai houseing sale.csv      # Raw dataset – Chennai
├── Delhi house data.csv           # Raw dataset – Delhi
│
├── chennai_hpp.ipynb              # EDA & model training – Chennai
├── delhi_hpp.ipynb                # EDA & model training – Delhi
├── mumbai_hpp.ipynb               # EDA & model training – Mumbai
├── just_end_it.ipynb              # EDA & model training – Bengaluru
│
├── util.py                        # Prediction utilities – Bengaluru
├── util_Ch.py                     # Prediction utilities – Chennai
├── util_D.py                      # Prediction utilities – Delhi
├── util_mum.py                    # Prediction utilities – Mumbai
│
├── main_server.py                 # Flask application entry point
└── README.md
```

---

## Cities Supported

| City       | Dataset File                    | Notebook              | Utility Module   |
|------------|---------------------------------|-----------------------|------------------|
| Bengaluru  | `Bengaluru_House_Data.csv`      | `just_end_it.ipynb`   | `util.py`        |
| Delhi      | `Delhi house data.csv`          | `delhi_hpp.ipynb`     | `util_D.py`      |
| Chennai    | `Chennai houseing sale.csv`     | `chennai_hpp.ipynb`   | `util_Ch.py`     |
| Mumbai     | *(embedded in notebook)*        | `mumbai_hpp.ipynb`    | `util_mum.py`    |

---

## ML Workflow

Each city follows the same end-to-end pipeline:

1. **Data Acquisition** — City-specific CSV datasets
2. **Data Cleaning** — Handling missing values, duplicates, and inconsistencies
3. **Outlier Removal** — Filtering unrealistic price-per-sqft and BHK ratios
4. **Feature Engineering** — Encoding locations, normalizing area, etc.
5. **EDA** — Visualizing price distributions, location-based trends, correlations
6. **Model Training** — Training and comparing regression models (e.g., Linear Regression, Lasso, Decision Tree) using cross-validation
7. **Model Export** — Saving the best model and column metadata as artifacts
8. **Deployment** — Loading artifacts in Flask and serving predictions via API

---

## Installation & Setup

### Prerequisites

- Python 3.8+
- pip

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/ram-krishna-tiwari/Real-Estate_Analyzer.git
cd Real-Estate_Analyzer

# 2. Install dependencies
pip install flask pandas numpy scikit-learn matplotlib

# 3. Train models (if artifacts are not pre-generated)
# Open and run each city notebook in Jupyter:
# just_end_it.ipynb, delhi_hpp.ipynb, chennai_hpp.ipynb, mumbai_hpp.ipynb

# 4. Start the Flask server
python main_server.py
```

The app will be available at `http://127.0.0.1:5000`

---

## Usage

1. Open `http://127.0.0.1:5000` in your browser
2. Log in using the credentials:
   - **Email:** `test@example.com`
   - **Password:** `password123`
3. Select a city from the dashboard
4. Enter property details: location, area (sq. ft.), BHK, and bathrooms
5. Click **Estimate Price** to get the predicted property value

---

## API Endpoints

| Method | Endpoint                | Description                              |
|--------|-------------------------|------------------------------------------|
| GET    | `/`                     | Renders the login page                   |
| POST   | `/api/login`            | Authenticates user and creates session   |
| GET    | `/logout`               | Clears session and redirects to login    |
| GET    | `/dashboard`            | Main prediction dashboard (auth required)|
| GET    | `/get_location_names`   | Returns locations for a given city       |
| POST   | `/predict_home_price`   | Returns estimated price for given inputs |

### Example: Predict Home Price

```
POST /predict_home_price
Content-Type: application/x-www-form-urlencoded

city=Bengaluru&location=Whitefield&total_sqft=1200&bhk=3&bath=2
```

**Response:**
```json
{
  "estimated_price": 85.42
}
```

---

## Screenshots

> Screenshots and UI previews are available in the `Images/` folder.

---



## Author

**Ram Krishna Tiwari**
[GitHub Profile](https://github.com/ram-krishna-tiwari)

---


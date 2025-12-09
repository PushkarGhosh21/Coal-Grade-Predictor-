# ⛏️ Coal Grade Prediction & Pricing System

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-Web%20Framework-lightgrey?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![Scikit-Learn](https://img.shields.io/badge/ML-Scikit_Learn-orange?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)]()

## 📜 Overview
This project is an AI-driven web application designed to predict the **quality and grade of coal** for mining operations (WCL and NCL subsidiaries). By leveraging historical mining data and real-time weather metrics, the system provides accurate estimates for critical parameters like **GCV (Gross Calorific Value), Ash Content, and Moisture**.

Crucially, it includes a financial module that calculates the **total estimated cost** based on the predicted grade and current market prices. The model utilizes a complex cascading architecture to achieve a **95% accuracy rate** in grade classification.

## 📸 Screenshots
| Dashboard Interface | Prediction Result |
|:-------------------:|:-----------------:|
| ![Dashboard](https://via.placeholder.com/400x200?text=Dashboard+UI) | ![Result](https://via.placeholder.com/400x200?text=Prediction+Modal) |
*(Replace these placeholders with actual screenshots of your `dashboard.html` and results)*

## ✨ Key Features
* **🤖 Multi-Stage Prediction Pipeline:** A cascading system of **16 specialized ML models** that sequentially predicts:
    1.  **Proximate Analysis:** Moisture (M), Total Moisture (TM), Ash Content.
    2.  **Calorific Value:** Gross Calorific Value (GCV).
    3.  **Classification:** Final Coal Grade (G1 - G17).
* **💰 Dynamic Pricing Engine:** Automatically maps the predicted grade to current price tables to compute shipment costs.
* **🌦️ Weather & Temporal Integration:** * Fetches historical weather data (Precipitation, Temp, Wind Speed).
    * Uses **Cyclical Time Encoding** (Sine/Cosine transformation) for months/days to capture seasonal trends accurately.
* **🏭 Multi-Subsidiary Support:** distinct model dictionaries for **Western Coalfields Ltd (WCL)** and **Northern Coalfields Ltd (NCL)**.

## 🛠️ Tech Stack
* **Backend:** Python, Flask (with Threading for auto-launch)
* **Machine Learning:** Scikit-learn, Pandas, NumPy
* **Frontend:** HTML5, CSS3, JavaScript (Jinja2 Templates)
* **Serialization:** Pickle (`.sav` models)

## 🚀 Installation & Setup

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/PushkarGhosh21/Coal-Grade-Predictor-AI.git](https://github.com/PushkarGhosh21/Coal-Grade-Predictor-AI.git)
    cd Coal-Grade-Predictor-AI
    ```

2.  **Install Dependencies**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Data & Model Setup**
    * Ensure all `.sav` model files (e.g., `WCL_FINAL_M_model.sav`) are in the root directory.
    * Ensure `wcl_weather_meteostat.csv` and `ncl_weather_meteostat.csv` are present for weather history lookups.

4.  **Run the Application**
    ```bash
    python app.py
    ```
    * The app will automatically launch in your default browser at `http://127.0.0.1:5000`.

## 🧠 Model Architecture
The system employs a **Cascaded Stacking Approach**:
1.  **Stage 1 (Physical Props):** Input `[Area, Date, Weather]` → Predicts `Ash`, `Moisture`, `TM`.
2.  **Stage 2 (Energy):** Input `[Stage 1 Outputs + Weather]` → Predicts `GCV`.
3.  **Stage 3 (Grade):** Input `[GCV + Area + Weather]` → Classifies `Grade`.
4.  **Stage 4 (Financial):** Input `[Grade + Quantity]` → Calculates `Price`.

## 👤 Author
**Pushkar Ghosh**
* [LinkedIn](https://www.linkedin.com/in/pushkar-ghosh)
* [GitHub](https://github.com/PushkarGhosh21)

---
*This project was developed as part of an internship at Coal India Limited.*

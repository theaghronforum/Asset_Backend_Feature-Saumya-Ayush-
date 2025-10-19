# Asset_Backend_Feature-Saumya-Ayush

💼 AI-Based Asset Allocation & Investment Recommendation System

🧠 Overview
This project is an AI-driven financial portfolio recommendation system that predicts the ideal asset allocation (Equity, Bonds, Crypto, etc.) for an investor based on their investment amount and risk capability.
It uses Machine Learning (Random Forest + MultiOutput Regression) to analyze investor patterns and generate intelligent, personalized portfolio suggestions.

🚀 Key Features
✅ Predicts optimal asset allocation percentages
✅ Handles large datasets (2M+ rows) efficiently
✅ Built with FastAPI backend and tested via Swagger UI
✅ Scalable model — easily integrates with any frontend (React / Next.js)
✅ Provides AI-based investment recommendations
✅ Modular folder structure with clean and reusable code

🧩 Project Architecture
AI_Asset_Backend/
│
├── app.py                # Main FastAPI backend app
├── recommend.py          # Model loading & prediction logic
│
├── data/
│   └── Merge_Features.csv  # Merged dataset (2M+ rows)
│
├── models/
│   ├── alloc_multi.joblib
│   ├── scaler.joblib
│   ├── feature_list.txt
│   └── alloc_target_cols.csv
│
└── api/
    ├── main.py
    └── utils.py
    
🧮 Model Training Pipeline
Data Merging:
Combined 42 JSON datasets into one large CSV (Merge_Features.csv)
Feature Engineering:
Extracted key features like log_investment, risk_cap_encoded, investment_amount, etc.
Model Training:
Algorithm: RandomForestRegressor (MultiOutputRegressor)
Scaler: StandardScaler
Targets:
['Equity_Large_Cap','Equity_Mid_Cap','Equity_Small_Cap',
 'Bonds_Government','Crypto_Currency','Hard_Commodity_Gold','Mutual_Fund_ETF']


Model Saving:
All trained artifacts are saved in /models directory as:
alloc_multi.joblib → Trained model
scaler.joblib → Scaler for standardization
feature_list.txt → Feature columns used in training
alloc_target_cols.csv → Allocation target column names

Model Validation:
Tested prediction in Jupyter Notebook
Function: recommend_notebook(investment_amount, risk_capability)
Verified predictions for all risk types (Aggressive, Moderate, Conservative)

⚙️ Backend API Setup
▶️ Run Locally
# Go to parent directory
cd C:\Users\saumy
# Run FastAPI using Uvicorn
python -m uvicorn AI_Asset_Backend.app:app --reload --port 8000

✅ Expected Log:
INFO:     Uvicorn running on http://127.0.0.1:8000
INFO:     Application startup complete.

🌐 API Testing
Swagger UI:
👉 http://127.0.0.1:8000/docs

Example Request:
{
  "investment_amount": 2100000,
  "risk_capability": "Aggressive"
}
Example Response:
{
  "investment_amount": 2100000,
  "risk_capability": "Aggressive",
  "recommendation": {
    "Equity_Large_Cap": 40.0,
    "Equity_Mid_Cap": 15.0,
    "Bonds_Government": 30.0,
    "Crypto_Currency": 5.0,
    "Mutual_Fund_ETF": 10.0
  }
}

🧠 Tech Stack
Layer	Technology
Language	Python 3.11
Framework	FastAPI
ML Model	Random Forest (MultiOutputRegressor)
Libraries	Pandas, NumPy, Scikit-learn, Joblib
Server	Uvicorn
API Testing	Swagger UI
Environment	Jupyter Notebook + Anaconda

📊 Sample Output
Asset Type	Allocation (%)
Equity_Large_Cap	40
Equity_Mid_Cap	15
Bonds_Government	30
Crypto_Currency	5
Mutual_Fund_ETF	10

👩‍💻 Author

Saumya Nigam
🎓 B.Tech CSE (Data Analytics) — GLA University (Batch 2025)
💡 Passionate about AI, Data Science, and Full-Stack Development
Ayush Kumar Gupta
🎓 M.C.A — GLA University (Batch 2025)
💡 Passionate about AI, Full-Stack Development and CloudDevops

# Fraud Detection with Machine Learning

This project demonstrates how to detect fraudulent transactions using machine learning. It includes data preprocessing, model training, evaluation, visualization, and tools to save/load trained models for reuse.


## Project Structure

data-dictionary.txt              # Dataset details
data/                            # Raw / sample datasets (ignored in Git, see data/README.md)
notebooks/                       # Jupyter notebooks for experiments
    detect_fraud_xgboost.ipynb   # Model being trained
requirements.txt                 # Python dependencies
README.md                        # Project overview
.gitignore                       # Git ignore rules


## Features

	•	Preprocesses transaction data (scaling, encoding, splitting).
	•	Trains a classification model (Random Forest by default).
	•	Evaluates performance with accuracy, precision, recall, F1-score, ROC-AUC.
	•	Visualizes confusion matrix and ROC curve.
	•	Saves & loads trained models (.pkl format).
	•	Detects fraud in new/unseen data.


## Installation

### Clone repo
git clone <your-repo-url>
cd fraud-detection

### Create environment
python3 -m venv detect-fraud-env
source detect-fraud-env/bin/activate   # On Mac/Linux
detect-fraud-env\Scripts\activate      # On Windows

### Install dependencies
pip install -r requirements.txt


# Usage

    1.	Launch Jupyter Notebook: 'jupyter notebook'
	2.	Open notebooks/fraud_detection.ipynb.
	3.	Run all cells to:
    	•	Train model
    	•	Evaluate performance
    	•	Save model to models/fraud_model.pkl

To load a saved model for prediction:
    from utils import load_model, predict_new_data
    model = load_model("models/fraud_model.pkl")
    predictions = predict_new_data(model, new_data)

# Data

Dataset (synthetic) it almost 500 mb so I can't upload on github.

If you want to use it then contact me and I will figure out a way to share it.

## Data Dictionary

    step - maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps 744 (30 days simulation).

    type - CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER.

    amount - amount of the transaction in local currency.

    nameOrig - customer who started the transaction

    oldbalanceOrg - initial balance before the transaction

    newbalanceOrig - new balance after the transaction

    nameDest - customer who is the recipient of the transaction

    oldbalanceDest - initial balance recipient before the transaction. Note that there is not information for customers that start with M (Merchants).

    newbalanceDest - new balance recipient after the transaction. Note that there is not information for customers that start with M (Merchants).

    isFraud - This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system.

    isFlaggedFraud - The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction.


# Tech Stack

	•	Python 3.x
	•	Scikit-learn
	•	Pandas
	•	Matplotlib & Seaborn
	•	Jupyter Notebook


# Next Steps

	•	Experiment with other ML algorithms (XGBoost, LightGBM, Neural Networks).
	•	Feature engineering for better fraud detection.
	•	Deploy as an API (Flask/FastAPI) for real-time fraud detection.

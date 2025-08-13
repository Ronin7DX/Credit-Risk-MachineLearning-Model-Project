# Credit Risk Modeling for Lauki Finance

## Description
This project develops a credit risk model for Lauki Finance, an India-based NBFC, to predict loan default probabilities and assign credit scores (Poor, Average, Good, Excellent) inspired by the CIBIL scoring system. Built using Python, it features a Logistic Regression model trained on historical loan, customer, and credit bureau data, achieving 97.5% AUC, 85.9% KS statistic, and 0.96 Gini coefficient. A Streamlit-based UI enables real-time loan application assessment for loan officers.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Features](#features)
- [Model Details](#model-details)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Installation
Follow these steps to set up the project locally:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/credit-risk-model.git
   ```
2. **Navigate to the Project Directory**:
   ```bash
   cd credit-risk-model
   ```
3. **Create a Virtual Environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
4. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   Required packages:
   - joblib
   - streamlit
   - scikit-learn
   - pandas
   - numpy
   - matplotlib

5. **Ensure Dataset Availability**:
   Place the datasets (`loan_customers.csv`, `loans.csv`, `bureau_data.csv`) in the `data/` folder.

## Usage
To explore the model or run the Streamlit application:

1. **Model Development**:
   - Open `Credit Risk Model.ipynb` in Jupyter Notebook to review data preprocessing, feature engineering, and model training.
   - Run the notebook to train the Logistic Regression model and save it to `artifacts/model_data.joblib`.

2. **Run the Streamlit App**:
   ```bash
   streamlit run Main.py
   ```
   - Open `http://localhost:8501` in your browser.
   - Input borrower details (age, income, loan amount, etc.), loan purpose, and credit bureau data.
   - Click "Calculate Risk" to view the default probability, credit score (300–900), and rating (Poor, Average, Good, Excellent).

### Example
```python
# Example input in Streamlit app
Age: 28
Income: 1,200,000
Loan Amount: 2,560,000
Loan Tenure (months): 36
Avg DPD per Delinquency: 20
Delinquency Ratio: 30
Credit Utilization Ratio: 30
Open Loan Accounts: 2
Residence Type: Owned
Loan Purpose: Home
Loan Type: Unsecured
```

Output:
- Default Probability: e.g., 12.34%
- Credit Score: e.g., 750
- Rating: e.g., Excellent

## Project Structure
```
credit-risk-model/
├── artifacts/                # Saved model and components (model_data.joblib)
├── data/                    # Input datasets (loan_customers.csv, loans.csv, bureau_data.csv)
├── Credit Risk Model.ipynb  # Jupyter Notebook for model development
├── Main.py                  # Streamlit app for real-time predictions
├── Prediction_helper.py     # Helper functions for prediction and preprocessing
├── requirements.txt         # Project dependencies
└── README.md                # Project documentation
```

## Features
- **Data Preprocessing**: Handles three datasets (50,000 records each) with customer demographics, loan details, and credit bureau data.
- **Feature Engineering**: Includes numerical features (e.g., age, loan_to_income, delinquency_ratio) and one-hot encoded categoricals (e.g., residence_type, loan_purpose).
- **Model**: Logistic Regression (C=0.1, class_weight='balanced', solver='liblinear') with high explainability via feature coefficients.
- **Streamlit UI**: User-friendly interface for loan officers to input data and view predictions.
- **Metrics**: Achieves 97.5% AUC, 85.9% KS statistic, and 0.96 Gini coefficient on test data.
- **Scalability**: Supports future ML Ops integration for monitoring and Straight Through Processing (STP).

## Model Details
- **Algorithm**: Logistic Regression
- **Features Used**:
  - Numerical: `age`, `loan_tenure_months`, `number_of_open_accounts`, `credit_utilization_ratio`, `loan_to_income`, `delinquency_ratio`, `avg_dpd_per_delinquency`
  - Categorical (one-hot encoded): `residence_type` (Owned, Rented), `loan_purpose` (Education, Home, Personal), `loan_type` (Unsecured)
- **Output**:
  - Default probability (0–1, displayed as percentage).
  - Credit score (300–900, scaled from non-default probability).
  - Rating: Poor (300–<500), Average (500–<650), Good (650–<750), Excellent (750–900).
- **Model Storage**: Saved as `model_data.joblib` with model, scaler, features, and columns to scale.

## Contributing
Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add your feature description"
   ```
4. Push to the branch:
   ```bash
   git push origin feature/your-feature-name
   ```
5. Open a pull request.

Please follow PEP 8 standards and include tests for new features.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact
For questions or feedback, reach out to:
- Your Name: your.email@example.com
- GitHub: [your-username](https://github.com/your-username)
- Project Link: [https://github.com/your-username/credit-risk-model](https://github.com/your-username/credit-risk-model)

*Project from Codebasics ML Course. All rights reserved: Codebasics.io*
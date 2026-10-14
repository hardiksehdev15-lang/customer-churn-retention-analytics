**Customer Churn & Retention Analytics**

An end-to-end customer analytics project that uses historical retail transactions, machine learning, and Tableau to identify customers at risk of churning and support data-informed retention decisions.

**Project Overview**

Customer churn can reduce repeat purchases and long-term customer value. This project builds a customer-level churn prediction workflow and presents the results through interactive Tableau dashboards designed to support customer risk analysis and retention planning.
Business Questions
- Which customers have the highest predicted churn risk?
- How does customer value differ across churn-risk segments?
- Which customers may warrant priority retention outreach?
- How can churn probability and customer value inform retention actions?


**Dataset**

Dataset: Online Retail II
Periods: 2009–2010 and 2010–2011
The transaction data is used to study purchasing patterns and derive customer-level behavioral features.
The original dataset is not intended to be included in this repository. Check the dataset's source and licensing terms before redistributing it. To run the notebook, download the data from its original source and update the notebook's file path to your local copy.

**Tools & Technologies**
- Python — data analysis and preprocessing
- Pandas and NumPy — data manipulation and feature engineering
- Scikit-learn — machine learning and model evaluation
- XGBoost — alternative classification model
- Jupyter Notebook — analysis and model development
- Tableau Public — interactive dashboards
- Git and GitHub — version control and documentation


**Project Workflow**
1. Data Preparation
- Inspected transaction records for missing values and inconsistencies.
- Prepared transaction-level data for customer-level analysis.
- Derived customer behavioral features from historical purchasing activity.
2. Feature Engineering
The analysis includes customer-level features such as:
- Recency — time since the customer's last purchase
- Frequency / Total Orders — historical purchasing activity
- Monetary Value / Revenue — historical spending
- Orders 30D / 90D — recent purchasing activity
- Revenue 30D / 90D — recent revenue contribution
- Unique Products — variety of products purchased
- Customer Value — the value measure used in the analysis
3. Churn Target Definition
Churn is operationally defined as having no purchase during the following 90-day observation window. This creates a forward-looking target based on future purchasing activity.
The target is meaningful only when the full 90-day observation window is available. Results should therefore be interpreted in the context of the data cutoff and the target construction.
4. Model Development
The workflow evaluates Logistic Regression and XGBoost for churn prediction. It includes customer-level model preparation, candidate model comparison, validation-based threshold selection, and generation of churn probabilities and risk segments.
See the notebook for the actual model-selection process and reported evaluation results. Metrics should be interpreted alongside the target definition, validation design, and business cost of false positives and false negatives.
5. Customer Risk Segmentation
Customers are grouped into three risk categories:
- High Risk — prioritize for review and suitable retention outreach
- Medium Risk — consider targeted engagement
- Low Risk — continue relationship-building and loyalty initiatives
Risk categories support prioritization; they should not be treated as a guarantee that a customer will or will not churn.


**Tableau Dashboards**

Dashboard 1: Customer Churn & Retention Analytics
The overview dashboard presents:
- Total customers
- High-risk customers
- Average churn probability
- Customer risk distribution
- Median customer value by risk
- Customer value versus churn probability

Dashboard 2: Retention Action Center
The retention dashboard connects customer risk analysis to action priorities through:
- Customers by retention priority
- Priority customer list
- Risk levels and churn probabilities
- Customer value
- Retention action categories

Explore the interactive dashboards:

View Customer Churn & Retention Analytics on Tableau Public

**Key Insights**
- Risk segmentation helps organize customers into groups that can be reviewed for different retention approaches.
- Looking at customer value alongside predicted churn probability can help surface potentially valuable customers who may need attention.
- Churn probability alone should not determine retention spending; customer value and the likely effectiveness of an intervention also matter.
- Retention action categories provide a practical framework for organizing outreach and engagement efforts.
These are analytical observations and proposed actions, not evidence that a retention campaign has already improved outcomes. Campaign effectiveness would need to be measured using real outcomes or controlled experiments.

**Business Recommendations**
1. Review high-risk customers with meaningful customer value for personalized retention outreach.
2. Test low-cost reactivation campaigns before committing to more expensive interventions.
3. Use targeted engagement for customers showing signs of declining purchasing activity.
4. Maintain suitable loyalty and relationship-building initiatives for low-risk customers.
5. Track campaign results and refine priorities based on observed customer responses.

**Model Evaluation**

The notebook should be used as the source of truth for the model selected and the metrics obtained. Relevant evaluation measures include:
- ROC-AUC
- Precision and recall
- F1-score
- Average Precision
- Brier Score, where probability calibration is assessed
Model performance should be considered alongside the business costs of missed churners and unnecessary retention outreach.


**Repository Structure**
RICCE/
├── README.md
├── requirements.txt
├── .gitignore
├── Dashboard/
│   ├── dashboard-1-overview.png
│   └── dashboard-2-retention-action-center.png
└── Notebooks/
    ├── Churn_Analysis.ipynb
    └── outputs/
        ├── customer_churn_evaluation_output.csv
        ├── customer_churn_model_metrics.csv
        └── customer_churn_scoring_output.csv
The structure above describes the files intended for the public repository. Keep the local virtual environment and original dataset out of GitHub unless there is a clear reason and permission to include them.


**How to Run**

Prerequisites
- Python 3.10 or a compatible version
- Jupyter Notebook or JupyterLab
- The Online Retail II dataset downloaded separately

1. Clone the repository
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd RICCE

2. Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate

3. Install dependencies
pip install -r requirements.txt

4. Configure the dataset path
Download the dataset from its original source and update the file path in the notebook to match where you saved it. Do not commit the original dataset unless its licence explicitly permits redistribution.

5. Run the notebook
jupyter notebook
Open Notebooks/Churn_Analysis.ipynb and run the cells in order.


**Limitations & Future Improvements**
- Evaluate the model with a more extensive time-based backtesting strategy.
- Confirm that every training and evaluation label has a complete future observation window.
- Validate probability calibration and decision thresholds on later data.
- Measure retention campaign effectiveness with controlled experiments.
- Estimate expected incremental retention value rather than relying only on customer value and churn probability.
- Build a repeatable scoring workflow for new customer snapshots.

**Conclusion**

This project demonstrates a workflow for transforming historical retail transactions into customer-level churn predictions, risk segments, and retention priorities. By combining Python-based analysis and machine learning with Tableau dashboards, it connects predictive outputs to practical business questions.
Project Focus: Customer Analytics · Churn Prediction · Machine Learning · Business Intelligence · Tableau
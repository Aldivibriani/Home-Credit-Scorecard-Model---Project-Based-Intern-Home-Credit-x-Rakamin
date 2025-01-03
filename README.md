# Home-Credit-Scorecard-Model-Project-Based-Intern-Home-Credit-x-Rakamin

This is a final project on virtual internship experience by Home Credit x Rakamin.

## Business Understanding

**Home Credit Overview:** Home Credit is a leading global financial services provider specializing in unsecured consumer loans. The company offers credit solutions without requiring collateral, making it accessible to a broader customer base. This approach facilitates quick and convenient access to funds but also increases the risk profile due to the lack of security.

**Credit Application Process:** The process involves evaluating customer creditworthiness using various data points, including income, employment status, and credit history. The goal is to balance accessibility with risk management.

**Challenges:** Home Credit faces a default rate of 8%, significantly higher than the global ideal of 0.39% as reported by S&P Global in 2023. This discrepancy underscores the need for improved risk assessment and management strategies.

![Default vs Non Default](https://github.com/user-attachments/assets/a1304604-d3b6-44b8-aa0d-a3885482c734)

**Machine Learning Implementation:** Machine learning models are employed to enhance predictive accuracy in assessing credit risk. These models can identify complex patterns and risk factors that traditional methods may overlook, enabling more precise targeting and risk mitigation.

## Objective

The primary objective is to develop a robust predictive model that can effectively reduce the default rate while maintaining the accessibility and convenience of unsecured loans. This will enhance financial stability and customer satisfaction.

## Exploratory Data Analysis

### Family Type Default Status

![Default Status by Family Type](https://github.com/user-attachments/assets/0508c401-4a81-41ac-8588-fc194b0e1271)

- **Insight**: Married individuals form the largest group, with civil marriages having the highest default rate.
- **Recommendation**: Target marketing efforts towards married couples with financial security messaging.

### Education Type Default Status

![Default Status by Last Education Type](https://github.com/user-attachments/assets/5edff3af-dfbb-412c-9a3e-983d7e404a47)

- **Insight**: Secondary education borrowers have the highest default rate.
- **Risk Assessment**: Lower education correlates with higher default risk due to lower income levels.

### Population Distribution

![Distribution of Population Where Client Lives By Status Default](https://github.com/user-attachments/assets/c7bdb967-f417-467c-89f2-81df825a14d7)

- **Insight**: Most clients live in rural and suburban areas, with rural areas having higher default numbers.
- **Analysis**: Aligns with lower economic class trends.

### Occupation Type Default Status

![Default Status by Occupation Type](https://github.com/user-attachments/assets/1e53ed5d-0a24-4ebf-aa03-a0951d571c36)

- **Insight**: Laborers, drivers, Security staff, and Cooking staff show higher default rates.
- **Risk Assessment**: Blue-collar occupations tend to have higher default risks than white-collar jobs.

### Age Distribution by Default Status

![Distribution Client's Age by Status Default](https://github.com/user-attachments/assets/eac2aad0-6a57-4a65-a6a1-3ecb0777f35e)

- **Insight**: Clients around 30 years old are more likely to default.
- **Analysis**: Age-related risk factors need to be considered in credit assessments.

### Credit Income Ratio Distribution

![Distribution Credit Income Ratio](https://github.com/user-attachments/assets/c422b5a0-58d0-4da9-b6a7-121a278f6b4f)

- **Insight**: Concentration on lower ratios suggests defaults occur with lower income and small loans.
- **Conclusion**: Insufficient income is a key factor in defaults.

## Data Preprocessing

There are 7 datasets but due to computer's performance, we only use 5 datasets, Application_train, bureau, bureau_balance, previous_application, and instalments_payments. The datasets are so messy and need a detail data cleaning.

- **handling Missing Data**: In application_train, there are many features that has missing value. Starting from 0% - 20% missing data to over 60% missing data. Because the feature is too many, we drop features with missing values over 60% because these data can not provide any much information. As for missing values under 60%, we considering to fill it with median for numerical data (because median is robust with outliers) and mode for categorical data. The handling missing data treatment also applied for the rest datasets.
  
- **Handling Duplicated Data**: There are no duplicated data in every datasets (also, we drop the primary key and no duplicated data found).

- **Handling Outliers**: As for outliers, every features should be analyzed carefully because some features have an outliers as anomaly and some of them are not. For example, there is a DAYS_EMPLOYED (How many days before the application the person started current employment) feature in application_train that has maximum value at 365.243 days or 1.000 years. There is no possible that this person had worked for 1.000 years, so we drop this outliers. Then, there is a feature name "OBS_60_CNT_SOCIAL_CIRCLE" (How many observation of client's social surroundings with observable 60 DPD (days past due) default) with median 0 (meaning no observation around client's social surroundings) and the maximum value is 344. We considering to not drop the outliers because there might be individual with approximately 300 people in their social circle who are late on payments for over 60 days.

As for features that has outliers but not to drop the outliers, we handling it with feature transformation to make the data normal distributed. 

- **Handling Categorical Data**: There are many categorical feature on application_train and previous_application. To reduced this features, we select them using chi-squred method. Almost all categorical features has p-value under 5% (meaning has correlation with the label), but some of them has over 20 unique values, so we drop some features that we think not give a good information in predicting default rate (for example WALLSMATERIAL_MODE because walls material not give a good information) and some of features we aggregate them.

- **Label Encoding**: For categorical features, we use two method, label encoding and one-hot-encoding. As for categorical features that are binary and ordinal type, we use label encoding (e.g. CODE_GENDER and NAME_EDUCATION_TYPE) and as for data that is not binary and ordinal, we use one-hot-encoding. But, some features such as NAME_GOODS_CATEGORY, we aggregate them first into some group (Electronics, Home and Living, Fashion and Accessories, etc) so we reduced from 26 unique values into 7 unique values.

## Model Machine Learning

After merge all datasets (application_train, bureau, bureau_balance, previous_application, and instalments_payments), we have 303.976 rows data and 179 features (join on SK_ID_CURR). The label with name "TARGET" (the label for prediction with value 0 and 1 or not default and default). 

The label has proportion 92:8 which is class imbalance extreme. So, to avoid the model bias to the majority data, we use Synthetic Minority Oversampling Technique (SMOTE) because SMOTE creates synthetic samples for the minority class by interpolating between existing minority instances, which helps to enrich the dataset without simply duplicating existing data.

There are six algorithms we use for modeling: Logistic Regression, Decision Tree, Random Forest, LightGBM, AdaBoost, and XGBoost. When using Logistic Regression, we apply standardization to ensure that the features are on a similar scale, which improves the model's convergence and performance. We utilize the ROC AUC as our evaluation metric due to the significant class imbalance in the dataset; ROC AUC effectively differentiates between the positive and negative classes and provides a robust measure of model performance across various threshold settings.

The best result is Light GBM with the best hypeparameter: class_weight': 'balanced', 'max_depth': 7, 'min_child_samples': 21, 'n_estimators': 202, 'num_leaves': 94. **ROC AUC score** in **Light GBM Model** is **0.76**, so we choose Light GBM as our model.

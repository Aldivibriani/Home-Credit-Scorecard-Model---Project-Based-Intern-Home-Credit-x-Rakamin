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

Outline the steps for data cleaning, handling missing values, and preparing data for modeling.

## Model Machine Learning

Describe the approach for selecting and training machine learning models, including feature selection, model evaluation, and optimization strategies.

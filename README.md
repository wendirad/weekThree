# Insurance Data Analysis and Insights

This repository contains the analysis of historical car insurance claims data for **AlphaCare Insurance Solutions** (ACIS). The goal is to help optimize marketing strategies, discover low-risk targets for premium reduction, and provide insights that can be used to tailor insurance products effectively. The analysis covers multiple aspects, including data cleaning, univariate and bivariate analysis, and geographical comparison.

## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Preprocessing](#data-preprocessing)
3. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
   - [Univariate Analysis](#univariate-analysis)
   - [Bivariate Analysis](#bivariate-analysis)
4. [Geographical Data Comparison](#geographical-data-comparison)
5. [Key Insights and Recommendations](#key-insights-and-recommendations)
6. [Technologies Used](#technologies-used)
7. [How to Run the Analysis](#how-to-run-the-analysis)
8. [Contributing](#contributing)
9. [License](#license)

## Project Overview
This project analyzes car insurance claims data to:
- **Identify low-risk targets** for premium reduction.
- **Understand trends** across different geographic areas (e.g., Province, PostalCode).
- **Optimize the marketing strategy** by analyzing relationships between different variables such as premiums, claims, insurance cover types, and car details.

The data is cleaned, visualized, and analyzed using various statistical and machine learning techniques.

## Data Preprocessing
The dataset contains the following features:
- **Policy Information**: e.g., `PolicyID`, `TransactionMonth`, `CoverType`.
- **Vehicle Details**: e.g., `make`, `model`, `VehicleType`.
- **Claims Data**: e.g., `TotalPremium`, `TotalClaims`, `SumInsured`.
- **Geographic Information**: e.g., `Province`, `PostalCode`, `CrestaZone`.

### Steps Taken:
1. **Data Cleaning**: Identified and handled missing values, corrected data types, and removed any duplicates.
2. **Feature Engineering**: Created new variables like monthly changes in premiums and claims.

## Exploratory Data Analysis (EDA)

### Univariate Analysis
To understand the distribution of variables, we:
- Plotted histograms for numerical columns (`TotalPremium`, `TotalClaims`, `SumInsured`).
- Plotted bar charts for categorical columns (e.g., `CoverType`, `VehicleType`, `Province`).

#### Code Example:
```python
sns.histplot(data['TotalPremium'], kde=True)
sns.countplot(x='CoverType', data=data)
```

### Bivariate Analysis
Explored relationships between the variables:
- **Correlation Analysis**: Used correlation matrices to examine relationships between numerical variables like `TotalPremium` and `TotalClaims`.
- **Scatter Plots**: Visualized the relationship between **monthly changes in premiums and claims** with respect to **PostalCode**.

#### Example Insights:
- `TotalPremium` and `TotalClaims` have a **0.09 correlation**, indicating a weak positive relationship.
- Different postal codes show distinct trends in premiums and claims, helping identify regions with higher or lower risk.

#### Code Example:
```python
sns.heatmap(data.corr(), annot=True, cmap='coolwarm')
sns.scatterplot(x='TotalPremium', y='TotalClaims', data=data)
```

## Geographical Data Comparison

### Comparing Trends by Province/PostalCode
We aggregated data by **PostalCode** and **Province** to compare:
- **Average Premiums and Claims** across regions.
- The **most common CoverType** and **Vehicle Make** in each region.

#### Code Example:
```python
grouped_by_zip = data.groupby('PostalCode').agg({
    'TotalPremium': 'mean',
    'TotalClaims': 'mean',
    'make': lambda x: x.mode()[0],
}).reset_index()
```

### Visualizations:
- **Bar plots** comparing `TotalPremium` and `TotalClaims` across geographic areas.
- **Count plots** for `CoverType` and `Vehicle Make` distribution by geographic area.

#### Example Insights:
- **Premium and Claims**: Some regions have significantly higher claims, indicating a higher-risk area.
- **CoverType and Vehicle Make**: Common cover types and vehicle makes vary by region, which can help tailor marketing strategies.

## Key Insights and Recommendations
- **Premium Optimization**: Identify regions with higher-than-expected claims and suggest premium increases or targeted marketing strategies.
- **Risk Assessment**: Use the analysis to identify low-risk areas where premiums could be reduced to attract more customers.
- **Product Customization**: Develop customized insurance products based on geographic trends in car types, claims, and customer preferences.

## Technologies Used
- **Python**: For data cleaning, analysis, and visualization.
- **Pandas**: For data manipulation and aggregation.
- **Seaborn/Matplotlib**: For visualizations.
- **Scikit-learn**: For machine learning models (if applicable).
- **Jupyter Notebooks**: For an interactive analysis environment.

## How to Run the Analysis
1. **Clone the repository**:
   ```bash
   git clone https://github.com/wendirad/weekThree.git
   cd weekThree
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the analysis**:
   - Open the Jupyter notebook `insurance_analysis.ipynb` and execute each cell to perform the data preprocessing, EDA, and geographic analysis.

## Contributing
We welcome contributions to enhance the analysis and model. Feel free to fork the repository, make changes, and submit a pull request. Please ensure that your contributions align with the project goals and follow best practices for code quality.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

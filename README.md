# 🧬 Final Project - Statistical Theory

## 📝 Abstract

Our research addresses the question: How do the characteristics of the cell nuclei of a breast mass affect its diagnosis (Malignant/Benign)?

In this project, we employed a range of statistical tools to analyze our dataset and draw conclusions. Additionally, we extended our research to another dataset, creating a function that predicts the diagnosis based on these characteristics.

## 📊 Project Steps

#### 1️⃣ Preprocessing

- **Dropping Unnecessary Columns:** We began by eliminating irrelevant columns to optimize our dataset.

#### 2️⃣ Feature Separation

- **2.1 Correlation and Clustering:**
  - **Correlation Map:** We examined the correlations between the 31 features and identified those with correlations above 0.8.
  - **Clustering:** Highly correlated features were grouped into clusters, with a representative feature chosen from each using the VIF (Variance Inflation Factor) method. The diagnosis feature was treated as its own cluster.
- **2.2 Hierarchical Clustering:**
  - **Spearman Correlation Matrix:** We applied Spearman correlation to cluster the features.
  - **Representative Selection:** We selected representatives from each cluster, retaining all features highly correlated with the diagnosis feature for further analysis.

#### 3️⃣ Choosing a Method

- **Cross-Validation:** We performed cross-validation using an SVM with a linear kernel to evaluate model performance.
- **Shapiro-Wilk Normality Test:** The Shapiro-Wilk test was conducted on the cross-validation scores to check for normality.
- **Sign Test:** We used the sign test to determine the better feature selection method, opting to proceed with the first method based on the results.

#### 4️⃣ Statistical Analysis

- **4.1 Normality Test:** Normality tests were conducted on the features to assess their distributions.
- **4.2 Hypothesis Testing:** For normally distributed features, hypothesis tests were conducted to assess their value in distinguishing between malignant and benign diagnoses.
- **4.3 Distribution Fitting for Non-Normal Features:**
  - We attempted to fit several distributions (`norm`, `expon`, `gamma`, `lognorm`, `beta`) to non-normal features using the Goodness-of-Fit method.
  - Fit assessments were conducted using the Kolmogorov-Smirnov test for normal distributions and the Anderson-Darling test for others.
  - Only two features were successfully fitted with non-normal distributions.
- **4.4 Non-Parametric Tests:** We used the Mann-Whitney U test to evaluate the non-normal features’ effectiveness in differentiating between malignant and benign diagnoses.

#### 5️⃣ Data Analysis

- **Histogram Plotting:** Histograms were plotted for the remaining data after feature reduction.
- **Pairwise Feature Analysis:** We analyzed all pairs of features in relation to cancer type, using the reduced correlation matrix and the Mann-Whitney U test to identify the most suitable pairs for cancer type separation.

#### 6️⃣ Model Evaluation

- **SVC Linear Model:** We tested the accuracy of feature pairs using an SVM with a linear kernel. The model was trained to identify the most indicative features for cancer type, and we visualized the best separations.

#### 7️⃣ Combining Datasets

- **Socioeconomic Analysis:**
  - We explored the impact of socioeconomic status on breast cancer mortality by combining our main dataset (breast cancer in Wisconsin, 1992) with data from other states in 1992.
  - We added GDP data and population statistics to our dataset.
- **Proportion Calculation:** We calculated the proportion of breast cancer deaths relative to the total population for each state.
- **Chi-Square Test:**
  - We used the Chi-square test on population proportions categorized as ‘Low,’ ‘Medium,’ and ‘High’ GDP.
  - The results indicated no significant relationship between a state’s GDP and the percentage of breast cancer deaths, suggesting that Wisconsin’s economic status in 1992 did not affect its breast cancer mortality rate.

## 💻 Installation

To run this project, you’ll need Python and the following libraries installed:

- `pip install numpy matplotlib pandas seaborn scipy scikit-learn statsmodels`

The project specifically uses the following modules:

- `import numpy as np`
- `import matplotlib.pyplot as plt`
- `import pandas as pd`
- `import seaborn as sns`
- `from scipy import stats`
- `from sklearn.model_selection import train_test_split`
- `from sklearn.metrics import accuracy_score`
- `from statsmodels.stats.outliers_influence import variance_inflation_factor`
- `from statsmodels.tools.tools import add_constant`
- `from scipy.cluster.hierarchy import linkage, dendrogram, fcluster`
- `from scipy.spatial.distance import squareform`
- `from scipy.stats import binomtest, expon, gamma, lognorm, beta, norm, kstest, anderson, mannwhitneyu, chi2_contingency`

## 🚀 Usage

1. **Preprocess the data:** Follow the steps outlined in the code to clean and prepare your dataset.
2. **Feature Selection:** Use the provided methods to separate and select the most relevant features.
3. **Model Evaluation:** Perform cross-validation and statistical tests to evaluate the selected models.
4. **Diagnosis Prediction:** Apply the developed function to predict the diagnosis based on the selected features.
5. **Socioeconomic Analysis:** Combine datasets to analyze the relationship between socioeconomic factors and breast cancer mortality.
6. **Each decision in the project is supported by rigorous statistical analysis** to ensure the validity and reliability of the results.

## 📌 Notes

- The project emphasizes reducing data bias by carefully selecting representative features from highly correlated clusters.
- The function created can be applied to other datasets for diagnosis prediction.
- The socioeconomic analysis adds additional insight into the factors affecting breast cancer mortality.

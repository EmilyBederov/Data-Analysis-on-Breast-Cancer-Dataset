Final Project - Statistical Theory

Abstract

Our research investigates the question: How do the characteristics of the cell nuclei of a breast mass affect its diagnosis (Malignant/Benign)?

In this project, we utilized various statistical tools to analyze our dataset and derive insights that answer this question. Furthermore, we extended our research to another dataset and developed a function that determines the diagnosis based on specific characteristics.

Project Steps

1. Preprocessing

	•	Dropping Unnecessary Columns: Initially, we removed columns that were not essential for our analysis to streamline the dataset.

2. Feature Separation

	•	2.1 Correlation and Clustering:
	•	Correlation Map: We analyzed the correlation between the 31 features and identified those with correlations greater than 0.8.
	•	Clustering: Features with high correlation were clustered, and we selected a representative feature from each cluster using the VIF (Variance Inflation Factor) method. The diagnosis feature formed its own cluster.
	•	2.2 Hierarchical Clustering:
	•	Spearman Correlation Matrix: We used Spearman correlation to group the features into clusters.
	•	Representative Selection: We selected representatives from each cluster, except the one containing the diagnosis feature. From that cluster, we retained all features highly correlated with the diagnosis, as these are critical to our analysis.

3. Choosing a Method

	•	Cross-Validation: We performed cross-validation using an SVM with a linear kernel to evaluate model performance.
	•	Shapiro-Wilk Normality Test: To validate the results, we applied the Shapiro-Wilk test on the cross-validation scores.
	•	Sign Test: We used the sign test to determine which feature selection method yielded better results. Both methods showed promise, but we chose to proceed with the first method for further analysis.

4. Statistical Analysis

	•	4.1 Normality Test: We performed normality tests on our features to assess their distribution.
	•	4.2 Hypothesis Testing: For features that followed a normal distribution, we conducted hypothesis tests to evaluate their significance in distinguishing between malignant and benign diagnoses.
	•	4.3 Distribution Fitting for Non-Normal Features: For non-normal features, we attempted to fit several distributions (norm, expon, gamma, lognorm, beta) using the Goodness-of-Fit method. The fit was assessed using the Kolmogorov-Smirnov test for normality and the Anderson-Darling test for other distributions. Only two features were successfully fitted with non-normal distributions.
	•	4.4 Non-Parametric Tests: We used the Mann-Whitney U test to determine if the non-normal features could effectively differentiate between malignant and benign diagnoses.

5. Data Analysis

	•	Histogram Plotting: We plotted histograms of our remaining data after feature reduction.
	•	Pairwise Feature Analysis: We plotted all pairs of features in relation to cancer type, analyzed the correlations using the reduced correlation matrix, and identified the pairs most suitable for distinguishing between cancer types using the Mann-Whitney U test.

6. Model Evaluation

	•	SVC Linear Model: We tested the accuracy of our feature pairs using an SVM with a linear kernel. The model was trained to identify features that are most indicative of cancer type, and we visualized the most accurate separations.

7. Combining Datasets

	•	Socioeconomic Analysis: We explored the impact of socioeconomic status on breast cancer mortality by combining our main dataset (breast cancer in Wisconsin, 1992) with data from other states in 1992. We added GDP data and population statistics to our dataset.
	•	Proportion Calculation: We calculated the proportion of breast cancer deaths relative to the total population for each state.
	•	Chi-Square Test: We used the Chi-square test on population proportions categorized as ‘Low,’ ‘Medium,’ and ‘High’ GDP. The results indicated no significant relationship between a state’s GDP and the percentage of breast cancer deaths, suggesting that Wisconsin’s economic status in 1992 did not affect its breast cancer mortality rate.

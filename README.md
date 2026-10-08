# Principal Component Analysis of Financial Ratios: Evidence from Motorola Solutions Quarterly Data

## Project Overview

This project applies **Principal Component Analysis (PCA)** to the quarterly financial performance of **Motorola Solutions, Inc.** The study examines 60 quarterly observations from **Q3 2011 to Q2 2026** using financial ratios representing liquidity, solvency, activity, and profitability.

The main purpose is to examine the relationships among multiple financial ratios and reduce them into a smaller number of principal components while retaining a substantial proportion of the information contained in the original variables.

The analysis was conducted using **Python in Google Colab**, with the financial data initially organised in Microsoft Excel.

---

## Objectives

The study aims to:

1. Describe the quarterly financial performance of Motorola Solutions, Inc. using selected financial ratios from Q3 2011 to Q2 2026.

2. Examine the relationships among the selected financial ratios using correlation analysis.

3. Determine the suitability of the selected financial ratios for Principal Component Analysis using the Kaiser-Meyer-Olkin (KMO) measure, individual Measures of Sampling Adequacy (MSA), and Bartlett's Test of Sphericity.

4. Identify the principal components that explain the major variation in the selected financial ratios using Principal Component Analysis.

---

## Dataset

### Data Source

The data were obtained from Motorola Solutions, Inc.'s publicly available quarterly financial statements through Macrotrends. The study uses consolidated financial data at the global corporate level and covers 60 quarterly observations from Q3 2011 to Q2 2026. Only the selected variables required for the 11 financial ratios were used in this analysis. Data were manually compiled into Microsoft Excel before being imported into Google Colab for data preparation and statistical analysis.

### Financial Ratios

| Category      | Financial Ratios                                            |
| ------------- | ----------------------------------------------------------- |
| Liquidity     | Current Ratio                                               |
| Solvency      | Debt-to-Equity Ratio, Long-term Debt-to-Capital             |
| Activity      | Asset Turnover, Inventory Turnover, Receivable Turnover     |
| Profitability | Gross Margin, Operating Margin, Net Profit Margin, ROA, ROE |

---

# Methodology

The analysis followed these main stages:

1. Data Cleaning and Preparation
2. Descriptive Statistics
3. Data Standardisation
4. Pearson Correlation Analysis
5. KMO and MSA Assessment
6. Bartlett's Test of Sphericity
7. Determinant of the Correlation Matrix
8. Iterative Variable Reduction
9. Principal Component Analysis
10. Eigenvalue and Variance Analysis
11. Scree Plot
12. Principal Component Loadings

Potential outliers were examined using the **Interquartile Range (IQR)** method and cross-checked against the original financial data. Valid observations were retained rather than being removed automatically.

---

# Results

## 1. Descriptive Statistics

The financial ratios showed different levels of variation across the 60 quarterly observations.

Some ratios were relatively stable, while others showed substantial fluctuations.

| Financial Ratio           |     Mean | Standard Deviation |    Minimum |   Maximum |
| ------------------------- | -------: | -----------------: | ---------: | --------: |
| Current Ratio             |   1.6135 |             0.5782 |     0.9516 |    3.0573 |
| Debt-to-Equity Ratio      |  -6.2161 |            34.0965 |  -247.5217 |   45.9084 |
| Long-term Debt-to-Capital |   0.8975 |             0.3560 |     0.1765 |    1.6415 |
| Asset Turnover            |  67.2179 |           364.2097 |     0.1046 | 2062.0000 |
| Inventory Turnover        |   1.9345 |             0.5584 |     1.0397 |    3.4945 |
| Receivable Turnover       |   1.3953 |             0.2420 |     0.7111 |    1.7833 |
| Gross Margin              |  48.9477 |             2.2651 |    42.0788 |   53.5589 |
| Operating Margin          |  16.8993 |            13.7749 |   -79.9342 |   27.9290 |
| Net Profit Margin         |  13.0523 |             9.6696 |   -29.3817 |   59.1529 |
| ROA                       |   1.9109 |             2.1416 |    -8.8842 |    4.6043 |
| ROE                       | -13.0639 |           281.4717 | -1752.1740 | 1106.2678 |

D/E and ROE showed particularly large variation, while Gross Margin and Receivable Turnover showed relatively smaller variation.

---

## 2. Pearson Correlation Analysis

Several meaningful relationships were identified among the financial ratios.

The strongest positive relationships were:

| Variable Pair                | Pearson *r* |
| ---------------------------- | ----------: |
| Debt-to-Equity Ratio and ROE |      0.8837 |
| Operating Margin and ROA     |      0.7240 |

Strong negative relationships included:

| Variable Pair                               | Pearson *r* |
| ------------------------------------------- | ----------: |
| Current Ratio and Long-term Debt-to-Capital |     -0.6748 |
| Current Ratio and Receivable Turnover       |     -0.6745 |

Other notable relationships included:

* LTDC and RT: *r* = 0.4616
* CR and OM: *r* = -0.4998
* NPM and ROA: *r* = 0.5007

These relationships provided an initial indication that several financial ratios shared common information, supporting further assessment using PCA suitability measures.

---

# 3. PCA Suitability Assessment

## Initial KMO and MSA

The initial assessment used all 11 financial ratios.

Initial KMO and MSA

The initial KMO value was 0.4471, which was below the commonly used threshold of 0.50, indicating that the original 11 variables were not sufficiently suitable for PCA. The individual MSA values were then examined to identify variables that contributed less to the correlation structure.

Seven variables had MSA values below 0.50. Variables were removed one at a time, starting with the variable having the lowest MSA value, and the KMO value was recalculated after each removal.

Iterative Variable Reduction
Stage	Variable Removed	MSA	KMO After Removal	Reason
1	Asset Turnover (AT)	0.2405	0.4761	Lowest MSA; weak suitability for PCA
2	Inventory Turnover (IT)	0.2646	0.5323	Low MSA; removal improved overall KMO
3	Gross Margin (GM)	0.2808	0.5502	Low MSA; limited contribution to the common structure
4	Net Profit Margin (NPM)	0.4298	0.5826	MSA remained below 0.50
5	Debt-to-Equity Ratio (D/E)	0.3887	0.6152	Low MSA after previous removals
6	Return on Equity (ROE)	0.4103	0.6229	Low MSA and removal further improved KMO

After each variable was removed, the KMO value increased, indicating improved suitability for PCA. The process stopped when the remaining five variables had acceptable individual MSA values and the overall KMO reached 0.6229.

After the iterative variable reduction, five financial ratios were retained:

* Current Ratio
* Long-term Debt-to-Capital
* Receivable Turnover
* Operating Margin
* ROA

---

# 4. Final PCA Suitability

The final five variables were assessed using KMO, MSA, Bartlett's Test of Sphericity, and the determinant.

### Final KMO and MSA

**Final KMO = 0.6229**

| Variable                  |    MSA |
| ------------------------- | -----: |
| Current Ratio             | 0.6677 |
| Long-term Debt-to-Capital | 0.6222 |
| Receivable Turnover       | 0.6703 |
| Operating Margin          | 0.5837 |
| ROA                       | 0.5614 |

All five variables had MSA values above 0.50, indicating acceptable sampling adequacy.

### Bartlett's Test and Determinant

| Test                  |  Result |
| --------------------- | ------: |
| KMO                   |  0.6229 |
| Bartlett's Chi-square | 140.903 |
| Degrees of Freedom    |      10 |
| Bartlett's p-value    | < 0.001 |
| Determinant           |  0.0826 |

Bartlett's Test of Sphericity was statistically significant, leading to rejection of the null hypothesis that the correlation matrix was an identity matrix.

The determinant of **0.0826** was not excessively close to zero, indicating that the final correlation matrix was not singular.

Overall, the final five financial ratios were considered suitable for PCA.

---

# 5. Principal Component Analysis

PCA was performed using the standardised values of the five retained financial ratios.

## Eigenvalues and Explained Variance

| Component | Eigenvalue | Variance Explained | Cumulative Variance |
| --------- | ---------: | -----------------: | ------------------: |
| PC1       |     2.8048 |           55.1619% |            55.1619% |
| PC2       |     1.2792 |           25.1577% |            80.3195% |
| PC3       |     0.5864 |           11.5324% |            91.8519% |
| PC4       |     0.2219 |            4.3636% |            96.2155% |
| PC5       |     0.1924 |            3.7845% |           100.0000% |

Using the **Kaiser criterion (eigenvalue > 1)**, two principal components were retained.

The two retained components explain:

**80.3195% of the total variance**

This means that the five original financial ratios can be represented by two principal components while retaining more than 80% of the total variation.

---

# 6. Principal Component Loadings

The loadings of the five retained financial ratios on the two principal components are shown below.

| Financial Ratio           |     PC1 |     PC2 |
| ------------------------- | ------: | ------: |
| Current Ratio             |  0.9068 |  0.2472 |
| Long-term Debt-to-Capital | -0.6536 | -0.6091 |
| Receivable Turnover       | -0.7552 | -0.3083 |
| Operating Margin          | -0.7240 |  0.5621 |
| ROA                       | -0.6788 |  0.6603 |

### PC1: Liquidity and Financial Performance Dimension

PC1 was dominated by the **Current Ratio**, which had a strong positive loading of **0.9068**.

Other variables showed strong negative loadings:

* Receivable Turnover: -0.7552
* Operating Margin: -0.7240
* ROA: -0.6788
* Long-term Debt-to-Capital: -0.6536

Therefore, PC1 was interpreted as a **Liquidity and Financial Performance Dimension**, reflecting variation involving liquidity together with other aspects of financial performance.

### PC2: Profitability and Leverage Dimension

PC2 was mainly associated with:

* ROA: 0.6603
* Operating Margin: 0.5621
* Long-term Debt-to-Capital: -0.6091

Therefore, PC2 was interpreted as a **Profitability and Leverage Dimension**, reflecting the relationship between profitability indicators and the company's long-term capital structure.

---

# Key Findings

The study produced the following main findings:

* The initial 11 financial ratios were not sufficiently suitable for PCA, with an overall KMO of **0.4471**.
* Six variables were removed through iterative MSA assessment.
* The final analysis retained **five financial ratios**: CR, LTDC, RT, OM, and ROA.
* The final KMO improved to **0.6229**.
* All final MSA values exceeded **0.50**.
* Bartlett's Test of Sphericity was statistically significant (*p* < 0.001).
* The determinant of the final correlation matrix was **0.0826**.
* Two principal components had eigenvalues greater than 1.
* PC1 explained **55.1619%** of the variance.
* PC2 explained **25.1577%** of the variance.
* Together, PC1 and PC2 explained **80.3195%** of the total variance.
* PC1 was interpreted as the **Liquidity and Financial Performance Dimension**.
* PC2 was interpreted as the **Profitability and Leverage Dimension**.

Overall, PCA reduced the original set of 11 financial ratios to five suitable variables and subsequently summarised them into two principal components while retaining more than 80% of the total variance.

---

# Tools and Technologies

| Tool / Library  | Purpose                                   |
| --------------- | ----------------------------------------- |
| Python          | Statistical analysis and data processing  |
| Google Colab    | Python development environment            |
| Microsoft Excel | Data organisation                         |
| Pandas          | Data cleaning and manipulation            |
| NumPy           | Numerical calculations                    |
| Scikit-learn    | Standardisation and PCA                   |
| Factor Analyzer | KMO, MSA and Bartlett's Test              |
| Matplotlib      | Data visualisation                        |
| Seaborn         | Correlation visualisation                 |
| GitHub          | Project documentation and version control |

---

# Project Structure

```text
motorola-solutions-financial-ratio-pca/
│
├── README.md
│
└── Motorola_Solutions_Financial_Ratio_PCA.ipynb
```

The notebook contains the complete analysis, including:

* Data loading
* Data cleaning
* Outlier checking
* Descriptive statistics
* Data standardisation
* Pearson correlation analysis
* KMO and MSA analysis
* Bartlett's Test of Sphericity
* Determinant analysis
* Iterative variable reduction
* Principal Component Analysis
* Eigenvalues and explained variance
* Scree plot
* Principal component loadings

---

# Conclusion

The study demonstrated that PCA can be used to simplify the interpretation of multiple financial performance indicators.

The original 11 financial ratios were reduced to five variables that met the PCA suitability requirements. These five variables were subsequently represented by two principal components explaining **80.3195% of the total variance**.

The results provide a more concise representation of Motorola Solutions' quarterly financial performance and highlight two underlying dimensions: **Liquidity and Financial Performance** and **Profitability and Leverage**.

---
Disclaimer

This project was created for educational and portfolio purposes. The analysis is based on publicly available financial data and is intended to demonstrate the application of statistical methods, data analysis, and PCA. The findings should not be considered professional financial or investment advice.

---
# Author

**Janice Kek Kai Lin**

Bachelor of Science with Honours (Industrial Statistics)
Northern University of Malaysia (UUM)

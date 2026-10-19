# ADS 505 - Final Project

## Exploring Flood Insurance Claim Patterns and Severity

This project examines historical flood insurance claims from FEMA's National Flood Insurance Program (NFIP) to identify patterns associated with higher-cost claims. The main goal was to determine whether information available within the claims data could be used to identify claims that are more likely to result in severe losses.

### Data

The analysis uses the FEMA OpenFEMA NFIP Redacted Claims v3 dataset. The full dataset contains more than 2.7 million claim records. A 30,000 record sample was used for the initial analysis, with the final modeling dataset limited to claims from 2010 through 2024.

A high-severity claim was defined as a claim with at least $50,000 in total payments. Total payment was calculated using building, contents, and Increased Cost of Compliance (ICC) payments.

### Analysis

The project included data cleaning, exploratory analysis, feature preparation, and predictive modeling. Several classification approaches were evaluated, with the final model using a tuned Random Forest.

To better reflect how the model could perform on future claims, the data was separated chronologically:

- 2010–2020: Training
- 2021–2022: Validation
- 2023–2024: Testing

### Results

The final Random Forest model produced a test ROC AUC of 0.833 and PR AUC of 0.827. When the highest-risk 30% of claims were prioritized, the model identified 321 of the 643 high-cost claims in the test data. A random selection of the same size would be expected to identify about 193.

These results suggest that claim data can provide useful information for identifying higher severity flood losses and may help support earlier claim prioritization.

### Repository

`ADS_505_Final_Project.ipynb` contains the complete analysis, including data preparation, exploratory analysis, modeling, model evaluation, and visualizations.

### Reproducibility

The notebook is designed to run in Google Colab from top to bottom. Data is retrieved directly from the FEMA OpenFEMA NFIP Redacted Claims v3 API.

To create the 30,000 record sample, the full dataset was divided into 60 sections and 500 records were sampled from each section using a fixed random seed of 12345. Records were retrieved in ID order using the FEMA API. This approach was used to create a reproducible sample that was distributed across the full dataset rather than relying on the first available records.

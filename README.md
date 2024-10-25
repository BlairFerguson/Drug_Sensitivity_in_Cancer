# Drug_Sensitivity_in_Cancer

This notebook aims to predict **IC50 effect size** using drug and biological feature data. I will explore the data, perform feature engineering, and compare model performances, including Random Forest, XGBoost, and Gradient Boosting.

Applications of this data and analysis include:
1. Precision Oncology: By identifying which genomic features are associated with drug sensitivity, this dataset can help develop more personalized cancer therapies.
2. Drug Repurposing: It can help identify existing drugs that might be effective for cancers with specific genetic profiles.
3. Biomarker Discovery: It assists in discovering new biomarkers for drug response that could be used to stratify patients in clinical trials.

For medical models, especially in Drug Development and Precision Medicine, it is important to be able to explain the results of ML models. 

**Ensemble methods**, like those used here, are among the most powerful predictive models together with deep learning. The drawback being their interpretability. **eXplainable AI (XAI)** is the set of techniques that allow to understand, interpret and rely on the emerging results from complex AI models.

In this notebook, I have used **SHAP** to explain which variables are influencing the models most.

I also checked for **multicollinearity** (correlation between independent variables) and ran a **Principal Components Analysis (PCA)** for **Dimensionality Reduction**, and compared these results to the original models. 

DATA

The dataset used in this analysis can be found at: Genomics of Drug Sensitivity in Cancer (GDSC) project, a large public resource that provides data on how different cancer cell lines respond to various drugs. www.cancerrxgene.org

The dataset contains: 
* Drug Sensitivity Data: This includes IC50 values, which measure the concentration of a drug needed to inhibit 50% of a target biological process in cancer cell lines.
* Lower IC50 values indicate higher drug potency.

Genomic Features: The dataset includes various genomic alterations or markers for each cancer cell line, such as:
* Mutations in key cancer-associated genes.
* Copy number alterations (gene amplifications or deletions).
* Gene expression profiles.

Important Columns in the Dataset
1. Drug Information:
* Drug name: The name of the drug tested.
* Drug ID: An identifier for the drug in the dataset.
* Drug target: The biological target of the drug (e.g., a specific protein or pathway).

  
2. Feature Information:
* Feature Name: A genetic or genomic feature, like a mutation (e.g., TP53_mut), whose presence or absence is tested for association with drug response.
* n_feature_pos / n_feature_neg: The number of cell lines positive or negative for the feature.
* log_ic50_mean_pos / log_ic50_mean_neg: The log-transformed IC50 values for cell lines with the feature (positive) or without the feature (negative).
  
3. Statistical Information:
* ic50_effect_size: A measure of the difference in drug response between cell lines with and without a specific genomic feature.
* feature_ic50_t_pval / feature_pval: P-values indicating whether the differences in drug response between groups are statistically significant.
  
4. Other Features:
* Tissue Type: The type of cancer associated with the cell line.
* Screening Set: Identifies whether the data comes from GDSC1 or GDSC2.

 

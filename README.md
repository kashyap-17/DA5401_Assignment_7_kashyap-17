### **Assignment: DA5401 A7: Multi-Class Model Selection using ROC and Precision-Recall Curves**

**Student Information**

  * **Name:** Kashyap Shankar Iyer
  * **Roll Number:** DA25C012

-----

**Documentation**

This submission consists of a single Jupyter Notebook. Its purpose is to perform a comprehensive comparison of diverse classification models on a multi-class satellite image dataset. The core of the analysis involves implementing and interpreting advanced evaluation metrics, specifically the **Receiver Operating Characteristic (ROC) curve** and the **Precision-Recall Curve (PRC)**, both adapted for a multi-class "One-vs-Rest" (OvR) setting. The notebook identifies the best-performing models, as well as intentionally implementing and analyzing a "worse-than-random" (AUC \< 0.5) classifier to demonstrate a full understanding of these metrics.

-----

**Folder Structure**

```
.
└── Kashyap_DA25C012_A7_Model_Selection.ipynb
```

-----

**Dataset Information**

The analysis is based on the **UCI Landsat Satellite Dataset**. This dataset, provided in `sat.trn` and `sat.tst` files, contains multi-spectral values from a satellite image. The task is to classify the land cover type for a central pixel based on its 3x3 neighborhood.

  * **Features:** 36 numerical attributes (4 spectral bands for 9 pixels).
  * **Target:** A single multi-class variable with 6 distinct classes (labeled 1, 2, 3, 4, 5, and 7).
  * **Data:** The provided training and test files are merged into a single dataset, which is then re-split to ensure a randomized 80/20 train-test distribution for robust evaluation.

-----

**Notebook Structure and Content**

The notebook is organized into the following sections to guide the reader through the complete analytical process:

  * **Part A: Data Preparation & Initial Modeling**
    This section covers loading and pre-processing the data. Key steps include:

    1.  **Data Merging:** Combining `sat.trn` and `sat.tst` into a single dataframe.
    2.  **Label Encoding:** Transforming the non-contiguous class labels `[1, 2, 3, 4, 5, 7]` into a zero-indexed, contiguous array `[0, 1, 2, 3, 4, 5]` to be compatible with all models.
    3.  **Feature Scaling:** Applying `StandardScaler` to all 36 features.
    4.  **Data Splitting:** Splitting the data into stratified 80% training and 20% test sets.
    5.  **Model Training:** Training a total of **nine** classifiers on the training data, including all required models (Logistic Regression, k-NN, GaussianNB, Decision Tree, SVC) and all "Brownie Point" models (Random Forest, XGBoost, a `Dummy (Prior)` baseline, and a custom `BadClassifier`).

  * **Part B: Multi-Class ROC Analysis**
    This section evaluates all models based on their ROC-AUC scores.

    1.  **OvR Preparation:** Binarizing the test labels for One-vs-Rest (OvR) analysis.
    2.  **Macro-Average Plot:** Generating a *single* plot that displays the Macro-Average ROC curve for all nine classifiers, providing a direct comparison of their overall discriminative power.
    3.  **Interpretation:** A detailed analysis identifying the model with the highest Macro-AUC and explaining the conceptual meaning of the `BadClassifier`'s score (AUC \< 0.5).

  * **Part C: Multi-Class PRC Analysis**
    This section provides a deeper, alternative evaluation using Precision-Recall Curves, which are more sensitive to class imbalance.

    1.  **Macro-Average Plot:** Generating a *single* plot showing the Macro-Average PRC curve for all nine classifiers.
    2.  **Interpretation:** A written analysis identifying the model with the highest Macro-Average Precision (AP) and explaining the precision-recall trade-off, particularly why poor models' curves collapse.

  * **Part D: Synthesis & Final Recommendation**
    This final section consolidates all findings to make a conclusive recommendation.

    1.  **Synthesis:** A summary table comparing all models across their Macro F1-Score, Macro-Avg ROC-AUC, and Macro-Avg PRC-AP scores, discussing the consistent alignment of the rankings.
    2.  **Recommendation:** A final, justified recommendation for the best overall model, also noting the top performer from the original required list.
    3.  **Brownie Points:** A concluding cell that explicitly confirms how the optional "Brownie Point" tasks were implemented and integrated into the main analysis.
# Preprocessing Pipeline

The following steps were applied to the data before training.

::: tabular
l L12cm **Step** & **Description**\
Feature Engineering & Created **BMI** feature:
$\text{Weight} / \text{Height}^2$.\
Target Encoding & `LabelEncoder`: 7 classes $\rightarrow$ integers
(0-6).\
Ordinal Encoding & `OrdinalEncoder` for 'CAEC', 'CALC' (e.g., 'no'
$\rightarrow$ 0, 'Always' $\rightarrow$ 3).\
Nominal Encoding & `OneHotEncoder` (drop='first') for 'Gender',
'MTRANS', etc.\
Feature Scaling & `StandardScaler` applied to all 9 numerical features.\
:::

# Hyperparameter Tuning

Models were optimized using cross-validation.

# Final Results

Models were evaluated on a 20% validation set. XGBoost achieved the
highest performance.

::: {#tab:results}
  **Model**        **Validation Accuracy**   **Weighted F1-Score**   **Macro F1-Score**
  --------------- ------------------------- ----------------------- --------------------
  Naive Bayes              78.24%                    0.78                   0.76
  AdaBoost                 88.19%                    0.88                   0.87
  Random Forest            89.96%                    0.90                   0.89
  **XGBoost**            **90.63%**                **0.91**               **0.90**

  : Final model performance on the validation set.
:::

![Comparison of Validation Accuracy and Weighted
F1-Score.](model_comparison_barplot.png){#fig:model_comp width="100%"}

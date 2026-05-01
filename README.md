![](UTA-DataScience-Logo.png)

# Mushroom Classification Kaggle Project

* **One Sentence Summary**: This repository attempts to classify mushrooms as edible or poisonous using various machine learning models based on their physical characteristics using data from the "Mushroom Classification" Kaggle challenge (https://www.kaggle.com/datasets/uciml/mushroom-classification). 

## Overview

  * **Definition of the tasks / challenge**:  The task, as defined by the Kaggle challenge is to build a machine learning model that can accurately predict if a mushroom is edible or poisonous based on its physical characteristics. The dataset stems from 23 species of gilled mushrooms.
  * **Your approach**: The approach in this repository formulates the problem as a binary classification task. I began with data loading, initial inspection, and exploratory data analysis to understand feature distributions and potential class imbalances. Data cleaning involved handling missing values ('?') and removing irrelevent features. The categorical features were then one-hot encoded for machine learning compatibility. I trained and evaluated 3 different classification models: Decision Tree, Random Forest, and Logistic Regression. The purpose of this is to compare their performance and interpretability on the mushroom classification dataset.
  * **Summary of the performance achieved**: Decision Tree and Random Forest models achieved a perfect 100% accuracy on both the validation and test sets. The Logistic Regression model also performed exceptionally well, achieving approximately 99.9% accuracy on both validation and test sets. This indicates that the dataset is highly separable and easily classifiable with these methods.

## Summary of Workdone


### Data

* Data:
  * **Type**: CSV file containing entirely categorical features (letters and '?'). The target is a binary categorical class ('e' for edible, 'p' for poisonous).
  * **Size**: The original dataset contains 8124 instances (rows) and 23 features (columns). After one-hot encoding and cleaning, the dataset used for modeling has 8124 instances and 95 features.
  * **Instances (Train, Test, Validation Split)**: The dataset was split into 70% for training (5686 instances), 15% for validation (1219 instances), and 15% for testing (1219 instances).

#### Preprocessing / Clean up

* **Missing Values**: The '?' character in the stalk-root feature was identified as a missing value indicator and was replaced with the string 'missing' to treat it as another category.
* **Feature Removal**: The veil-type feature was dropped because it contained only one unique value, making it not imformative for classification.
* **One-Hot Encoding**: All remaining categorical features were converted into numerical format using one-hot encoding. This created binary columns for each unique category, suitable for machine learning algorithms. No rescaling was required as all features became binary (0 or 1) after encoding.

#### Data Visualization

<img width="630" height="470" alt="Image" src="https://github.com/user-attachments/assets/39a674ff-b9d1-4139-9fcd-05ae63a4d835" />

<img width="630" height="470" alt="Image" src="https://github.com/user-attachments/assets/dd4aa589-beaa-4a13-83c1-254180bcd85f" />

<img width="630" height="470" alt="Image" src="https://github.com/user-attachments/assets/a48e25eb-74f5-47c6-8120-580153ceea07" />

<img width="630" height="470" alt="Image" src="https://github.com/user-attachments/assets/df42cf0c-4067-401a-9829-9f23cf747f80" />

<img width="630" height="470" alt="Image" src="https://github.com/user-attachments/assets/eea9f4dd-7c9f-42b4-bb0e-c9a7068005ef" />


* Bar plots were generated for each feature, showing the distribution of categories for both edible and poisonous mushrooms. These visualizations highlighted several promising features for classification due to clear separation in their distributions, notably odor, spore-print-color, gill-size, gill-color, and ring-type.
* **Odor (odor)**: The odor feature shows a strong distinction between edible and poisonous mushrooms. Certain odor types appear in one class, making it a highly indicative feature. For instance, 'a' (almond) and 'l' (anise) odors are only found in edible mushrooms, while 'p' (pungent), 'f' (foul), 'c' (creosote) odors are found in poisonous ones. 'n' (none) odor also shows a clear distribution.
* **Spore Print Color (spore-print-color)**: Similar to odor, different spore print colors are predominantly associated with either edible or poisonous mushrooms, suggesting it's a powerful discriminator.
* **Gill Size (gill-size)**: While not as distinct as odor or spore print color, the distribution of gill size (broad vs. narrow) also shows some differences between the two classes.
* **Gill Color (gill-color)**: Several gill colors are strongly associated with one class over the other, making this a useful feature.
* **Ring Type (ring-type)**: Some ring types are present in one class but absent or very rare in the other, indicating its potential for classification.
* These features, where there is clear separation or strong associations between their categories and the 'class' (edible/poisonous), are likely to be most useful for a machine learning model.

### Problem Formulation

* Define:
  * Input: The input to the models consists of 95 one-hot encoded binary features representing the physical characteristics of the mushrooms.
  * Output: The output is a binary class label: 0 for edible mushrooms and 1 for poisonous mushrooms.
  * Models
    * **Decision Tree Classifier**: Chosen for its simplicity, interpretability, and ability to handle categorical data directly. It serves as an excellent baseline.
    * **Random Forest Classifier**: Selected as an ensemble method to improve robustness, reduce overfitting compared to single decision trees, and potentially provide more stable feature importances.
    * **Logistic Regression**: Implemented as a linear classification model to assess the linearity of the dataset's separability and provide a contrast to the tree-based models.
  * Loss, Optimizer, other Hyperparameters.
    * For all models, random_state=42 was set for reproducibility.
    * For Logistic Regression, solver='liblinear' and max_iter=200 were specified to ensure convergence and handle the dataset effectively.

### Training

* Describe the training:
  * How you trained: Models were trained using their respective fit() methods from the sklearn library, with the one-hot encoded training features (X_train) and the encoded target variable (y_train).
  * How long did training take: Training for all models was fast, taking a few seconds due to the small size and high separability of the dataset.
  * Training curves (loss vs epoch for test/train): Training curves were not plotted as the models achieved perfect or near-perfect performance quickly.
  * How did you decide to stop training: Training stopped upon convergence for each algorithm, as indicated by the high validation accuracies achieved.
  * Any difficulties? How did you resolve them?: No significant difficulties were encountered during the training process for this dataset because the problem was highly separable.

### Performance Comparison

* Clearly define the key performance metric(s): The primary performance metric used for evaluation was Accuracy, which measures the proportion of correctly classified instances.
* Show/compare results in one table:
  
| Model  | Validation Accuracy | Test Accuracy |
| ------------- | ------------- | ------------- |
| Decision Tree | 1.000 | 1.000 |
| Random Forest | 1.000 | 1.000 |
| Logistic Regression | 0.999 | 0.999 |

* Visualization(s) of results for **Decision Tree**:

<img width="807" height="590" alt="Image" src="https://github.com/user-attachments/assets/6fc65b4b-a9ec-4084-9ff5-6c62fbb7da01" />

<img width="1570" height="812" alt="Image" src="https://github.com/user-attachments/assets/8e96a903-3535-4428-bf1d-24383f5d02c9" />

<img width="1162" height="547" alt="image" src="https://github.com/user-attachments/assets/83e5a1b2-c097-4ce0-85da-e7fa56a7ac86" />


   * **Confusion Matrix**: A Confusion Matrix was generated for the Decision Tree model on the validation set, visually confirming the perfect classification with 636 True Negatives and 583 True Positives, and 0 False Positives or False Negatives.
   * **Decision Tree**: The Decision Tree was visualized (with max_depth=3) to illustrate its decision-making process, showing how key features like odor_n and stalk-root lead to classifications.
   * **Feature Importance**: Based on the lengths of the bars, odor (odor_n) is displayed as the most important feature. This aligns with our initial data exploration which suggested 'odor' as a strong discriminator. Features like stalk-root_c, stalk-root_r, spore-print-color_r, and spore-print-color_u also show significant importance. This suggests that the characteristics related to the mushroom's stalk root and spore print color are also highly predictive of whether a mushroom is edible or poisonous.

### Conclusions

* The mushroom classification dataset is clean and highly separable. All 3 machine learning models (Decision Tree, Random Forest, and Logistic Regression) demonstrated outstanding performance, with Decision Tree and Random Forest achieving perfect accuracy on both validation and test sets. This suggests that relatively simple models can distinguish between edible and poisonous mushrooms based on the provided features. The odor feature, in particular, was identified as the most crucial predictor.

### Future Work

* **Hyperparameter Tuning**: Although performance is already perfect/near-perfect, further hyperparameter tuning for each model could be explored.
* **Other Classification Algorithms**: Experiment with other algorithms like Support Vector Machines (SVMs) or Gradient Boosting Machines (GBMs) for broader comparison.

## How to reproduce results

1. **Environment**: The Mushroom Classification analysis was performed in JupyterLab.
2. **Data**: Download the mushrooms.csv dataset from the Kaggle Mushroom Classification page and upload it to your environment or ensure it's accessible in the same directory as the notebook.
3. **Run Notebook**: Execute all cells in the provided Jupyter notebook in order. The notebook does all of the data loading, preprocessing, model training, evaluation, and visualization steps.

### Overview of files in repository

* (FINAL) Mushroom Classification Kaggle Tabular Project.ipynb: This project is contained in this Jupyter notebook file. All data loading, cleaning, preprocessing, model training, evaluation, and visualization steps are executed in order within this notebook.

### Software Setup
* The following Python packages are required:
   * pandas (for data manipulation)
   * matplotlib (for plotting)
   * scikit-learn (for machine learning models and utilities)
* These packages can be installed using pip if not already available in your environment:
   * pip install pandas scikit-learn matplotlib

### Data

* The dataset mushrooms.csv was sourced from the UCI Machine Learning Repository via Kaggle.

### Training

* Follow the code cells under the 'Machine Learning' section of the Jupyter notebook to train the Decision Tree, Random Forest, and Logistic Regression models.

#### Performance Evaluation

* The performance evaluation, including accuracy scores and confusion matrices, is demonstrated in the 'Evaluate Performance on Validation Sample' and 'Apply ML to the challenge test set' sections of the notebook.


## Citations

* Mushroom [Dataset]. (1981). UCI Machine Learning Repository. https://doi.org/10.24432/C5959T.

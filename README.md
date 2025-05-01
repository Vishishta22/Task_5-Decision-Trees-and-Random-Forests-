# Task_5-Decision-Trees-and-Random-Forests-
# Income Classification Using Decision Trees and Random Forests

##  Project Overview

This project explores **tree-based classification algorithms** using the [Adult Income dataset](https://archive.ics.uci.edu/ml/datasets/adult). The goal is to predict whether a person's income exceeds $50K/year based on features such as education, occupation, age, etc.

We apply both **Decision Tree** and **Random Forest** models, visualize trees, analyze overfitting, tune hyperparameters, and evaluate performance using cross-validation.

---

## Concepts Explained

###  Decision Tree Classifier

A **Decision Tree** is a supervised learning model that uses a tree-like structure to make decisions. Each internal node tests a feature, each branch represents an outcome, and each leaf node represents a predicted class label.  
> Pros: Easy to interpret, fast  
> Cons: Prone to overfitting

### Random Forest Classifier

A **Random Forest** is an ensemble method that builds multiple decision trees and combines their outputs (majority vote) to improve accuracy and reduce overfitting.  
> Pros: High accuracy, robust  
> Cons: Less interpretable, slower than single trees

---

## Tools & Libraries

- Python
- pandas, numpy
- scikit-learn
- matplotlib, seaborn
- Graphviz (for tree visualization)

---

##  Dataset Description

The dataset includes demographic and employment-related attributes. The key features used:

- `age`: Age of the person
- `education.num`: Number of years of education
- `hours.per.week`: Work hours per week
- `capital.gain` and `capital.loss`: Income from investment or business loss
- `sex`, `occupation`, `race`, etc.
- `income` (Target): `<=50K` or `>50K`

### Note:
- `fnlwgt`: Represents the number of people the census believes the entry applies to. It is kept for completeness but is often ignored in modeling.

---

##  Task Breakdown

### 🔹 1. Train a Decision Tree Classifier and Visualize the Tree

- Built using `DecisionTreeClassifier` from Scikit-learn.
- Visualized with Graphviz to understand splitting logic.
- Resulting model showed an accuracy of **~81.1%** on the test set.

> Tree was very large — indicating potential overfitting.

---

### 🔹 2. Analyze Overfitting and Control Tree Depth

- Limited `max_depth` to prune the tree.
- Post-pruning, the **pruned tree's accuracy** increased to **~84.5%**.
- This confirms overfitting in the unpruned model.

---

### 🔹 3. Train a Random Forest and Compare Accuracy

- Trained a `RandomForestClassifier` with multiple decision trees.
- Achieved higher accuracy of **~86.3%**.
- Random Forest reduces overfitting through bagging and averaging.

---

### 🔹 4. Interpret Feature Importances

- The top features contributing to predictions:
  - `education.num`
  - `capital.gain`
  - `hours.per.week`
  - `age`

Feature importance was extracted using `model.feature_importances_` from the trained random forest.

---

### 🔹 5. Evaluate Using Cross-Validation

- Applied 5-fold cross-validation.
- Cross-validation scores:
- [0.7666, 0.7570, 0.8169, 0.8255, 0.8194]
- Average CV Accuracy: 0.7971


This ensures the model's performance is stable and not due to random data splits.

---

##  Final Results Summary

| Model              | Accuracy     |
|-------------------|--------------|
| Decision Tree      | 81.1%        |
| Pruned Tree        | 84.5%        |
| Random Forest      | 86.3%        |
| CV Average (RF)    | 79.7%        |

---

## Key Takeaways

- Decision trees are powerful but can **overfit** easily without depth control.
- Random forests outperform individual trees due to **ensemble averaging**.
- **Cross-validation** is essential to measure model generalizability.
- **Feature importance** helps in understanding model decisions.

---

##  Graphviz Installation Guide (Windows)

To visualize decision trees using `graphviz`, follow these steps:

1. **Download EXE Installer:**
   - Go to: https://graphviz.org/download/
   - Download **Graphviz (64-bit) EXE installer**.

2. **Install Graphviz:**
   - Run the downloaded `.exe` file.
   - Install it to a known location like `C:\Program Files\Graphviz`.

3. **Add Graphviz to System PATH:**
   - Open **System Environment Variables** → Edit `PATH`.
   - Add:
     ```
     C:\Program Files\Graphviz\bin
     ```
   - Click OK and restart your system (or terminal).

4. **Verify Installation:**
   - Run this command in a terminal: dot -V
   - It should return the Graphviz version.

---

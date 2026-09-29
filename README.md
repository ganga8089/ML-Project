# Machine Learning Course Project – Model Comparison

## Team 15 – Model Comparison

**Course:** 24SJPCCST503 – Machine Learning  
**Institution:** St. Joseph's College of Engineering and Technology, Palai (Autonomous)  
**Academic Year:** 2026–2027

## Team Members

- Ganga V-SJC24CS115
- Judit Jeby-SJC24CS143
- Kenaz Mathukutty-SJC24CS148
- Savio Bijo Thomas-SJC24CS197

---

## Research Question

> **When should a simpler model be preferred to a more complex model?**

This investigation compares different regression models to understand how predictive performance, model complexity, generalization, interpretability, and computational cost affect model selection.

The project follows the investigation approach:

**Question → Hypothesis → Experiment → Evidence → Analysis → Conclusion**

---

## Models Studied

Three regression models were investigated:

1. Linear Regression
2. Decision Tree Regression
3. Random Forest Regression

The Decision Tree and Random Forest models were also evaluated under different complexity conditions.

### Decision Tree Conditions

- Depth 3
- Depth 5
- Depth 10

### Random Forest Conditions

- 10 trees
- 50 trees
- 100 trees

---

## Dataset

The project uses the **Auto MPG dataset**.

The dataset contains automobile characteristics that can be used to predict fuel efficiency.

### Target Variable

`mpg`

### Features Used

- cylinders
- displacement
- horsepower
- weight
- acceleration
- year
- origin

The `name` column was removed because it identifies individual cars rather than serving as a numerical predictor.

After preprocessing, the dataset contained:

- **392 observations**
- **313 training samples**
- **79 testing samples**
- **8 input features**

---

## Experimental Design

The same training and testing data were used for the different model configurations.

The models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Test R²
- Training R²
- 5-fold Cross-Validation R²
- Cross-Validation Standard Deviation
- Training Time

Model complexity was investigated by changing:

- Decision Tree depth
- Number of trees in Random Forest

Feature coefficients and feature importance were also examined to provide information about model interpretability.

---

## Key Results

### Baseline Model Comparison

| Model | Test R² | Train R² | MAE | RMSE | CV Mean R² |
|---|---:|---:|---:|---:|---:|
| Linear Regression | 0.7923 | 0.8287 | 2.4620 | 3.2561 | 0.8103 |
| Decision Tree | 0.7857 | 0.9307 | 2.3032 | 3.3072 | 0.7994 |
| Random Forest | 0.8844 | 0.9799 | 1.7333 | 2.4288 | 0.8543 |

Random Forest achieved the highest test R² and the lowest RMSE among the baseline models in this experiment.

However, the investigation does not consider predictive performance alone. Model complexity, interpretability, computational cost, and generalization are also considered.

---

## Decision Tree Complexity

| Depth | Test R² | Train R² | CV Mean R² |
|---:|---:|---:|---:|
| 3 | 0.7326 | 0.8401 | 0.7652 |
| 5 | 0.7857 | 0.9307 | 0.7994 |
| 10 | 0.7984 | 0.9948 | 0.7808 |

Increasing the tree depth substantially increased training performance.

However, the cross-validation score decreased from **0.7994 at depth 5** to **0.7808 at depth 10**, providing evidence that excessive complexity can reduce generalization.

---

## Random Forest Complexity

| Number of Trees | Test R² | Train R² | CV Mean R² |
|---:|---:|---:|---:|
| 10 | 0.8358 | 0.9703 | 0.8340 |
| 50 | 0.8814 | 0.9788 | 0.8530 |
| 100 | 0.8844 | 0.9799 | 0.8543 |

Increasing the number of trees improved performance initially.

However, the improvement from 50 to 100 trees was relatively small:

**Test R²: 0.8814 → 0.8844**

while training time increased.

This provides evidence of diminishing returns as the ensemble becomes larger.

---

## Main Finding

The investigation shows that increasing model complexity does not always produce a proportional improvement in generalization.

A complex model can achieve stronger predictive performance, but the additional complexity should be considered alongside:

- Generalization
- Interpretability
- Computational cost
- Model structure
- Application requirements

Therefore, model selection should not be based only on the highest accuracy or R² value.

---

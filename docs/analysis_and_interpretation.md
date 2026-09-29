
# Analysis and Interpretation

## Team 15 – Model Comparison

### Research Question

> **When should a simpler model be preferred to a more complex model?**

The investigation compares Linear Regression, Decision Tree Regression, and Random Forest Regression using the Auto MPG dataset.

The analysis considers:

- Predictive performance
- Generalization
- Model complexity
- Interpretability
- Computational cost

---

## 1. Baseline Model Comparison

The baseline experiment compared Linear Regression, Decision Tree Regression, and Random Forest Regression using the same training and testing data.

| Model | Test R² | Train R² | MAE | RMSE | CV Mean R² | Training Time (sec) |
|---|---:|---:|---:|---:|---:|---:|
| Linear Regression | 0.7923 | 0.8287 | 2.4620 | 3.2561 | 0.8103 | 0.0344 |
| Decision Tree | 0.7857 | 0.9307 | 2.3032 | 3.3072 | 0.7994 | 0.0043 |
| Random Forest | 0.8844 | 0.9799 | 1.7333 | 2.4288 | 0.8543 | 0.3666 |

Random Forest achieved the highest test R² of **0.8844** and the lowest RMSE of **2.4288** among the baseline models.

This indicates that Random Forest captured useful patterns in the dataset that the simpler models did not capture as effectively.

Random Forest combines predictions from multiple decision trees. This ensemble structure allows the model to represent nonlinear relationships and reduces dependence on a single tree.

However, its higher predictive performance comes with greater structural complexity and higher training time.

---

## 2. Linear Regression

Linear Regression achieved:

- Test R²: **0.7923**
- Train R²: **0.8287**
- MAE: **2.4620**
- RMSE: **3.2561**
- CV Mean R²: **0.8103**

The difference between training and testing R² is relatively small compared with the Decision Tree.

This suggests that the model has relatively stable generalization on this dataset.

Linear Regression is also relatively simple to interpret because the model uses learned coefficients for the input features.

Therefore, even though it did not achieve the highest predictive performance, it provides a useful simple baseline for comparison.

---

## 3. Decision Tree Analysis

The Decision Tree experiment investigated three maximum depths.

| Depth | Test R² | Train R² | CV Mean R² |
|---:|---:|---:|---:|
| 3 | 0.7326 | 0.8401 | 0.7652 |
| 5 | 0.7857 | 0.9307 | 0.7994 |
| 10 | 0.7984 | 0.9948 | 0.7808 |

### Effect of Increasing Depth

Increasing the tree depth increased training performance:

**0.8401 → 0.9307 → 0.9948**

However, the improvement in test performance was much smaller:

**0.7326 → 0.7857 → 0.7984**

This difference is important.

At depth 10, the training R² reached **0.9948**, meaning the tree fitted the training data extremely closely.

However, the cross-validation R² decreased from **0.7994 at depth 5** to **0.7808 at depth 10**.

This indicates that the additional complexity at depth 10 did not generalize equally well to unseen data.

### Interpretation

The deeper tree has greater capacity to create detailed decision rules. This allows it to model more specific patterns in the training data.

However, some of these patterns may be specific to the training samples rather than being general patterns in the underlying data.

Therefore, the results provide evidence of increased overfitting as Decision Tree complexity increases.

---

## 4. Random Forest Complexity Analysis

The Random Forest experiment investigated the effect of changing the number of trees.

| Number of Trees | Test R² | Train R² | CV Mean R² | Training Time (sec) |
|---:|---:|---:|---:|---:|
| 10 | 0.8358 | 0.9703 | 0.8340 | 0.0299 |
| 50 | 0.8814 | 0.9788 | 0.8530 | 0.1286 |
| 100 | 0.8844 | 0.9799 | 0.8543 | 0.2288 |

### Initial Improvement

Increasing the number of trees from 10 to 50 increased test R²:

**0.8358 → 0.8814**

This is a substantial improvement.

The additional trees allow the ensemble to combine more individual decision trees, producing a more stable prediction.

### Diminishing Returns

Increasing the number of trees from 50 to 100 produced only a small improvement:

**0.8814 → 0.8844**

The cross-validation score also changed only slightly:

**0.8530 → 0.8543**

At the same time, training time increased:

**0.1286 sec → 0.2288 sec**

Therefore, the results provide evidence of diminishing returns.

After a certain number of trees, adding more trees increases computational cost without producing a proportionally large improvement in predictive performance.

---

## 5. Generalization

Generalization refers to how well a trained model performs on unseen data.

The difference between training and test performance provides useful evidence about this behaviour.

### Linear Regression

Training R²:

**0.8287**

Test R²:

**0.7923**

The difference is relatively small.

### Decision Tree

Training R²:

**0.9307**

Test R²:

**0.7857**

The larger difference indicates a greater tendency to fit the training data more closely.

### Random Forest

Training R²:

**0.9799**

Test R²:

**0.8844**

Although Random Forest has a high training R², its test and cross-validation performance are also strong.

Therefore, high training performance alone cannot be used to determine whether a model generalizes well. Unseen-data performance and cross-validation results must also be considered.

---

## 6. Interpretability

Interpretability is an important part of the Team 15 investigation.

### Linear Regression

Linear Regression is relatively easy to interpret because each feature has a learned coefficient.

For example, the trained model produced coefficients for:

- weight
- year
- displacement
- horsepower
- cylinders
- acceleration
- origin

Because the features were scaled, the absolute coefficient values provide information about their relative contribution within the linear model.

### Decision Tree

A Decision Tree can be inspected through its decision rules.

However, interpretation becomes more difficult as the tree becomes deeper because the number of branches and decision rules increases.

### Random Forest

Random Forest is less directly interpretable because predictions are produced using an ensemble of many decision trees.

Feature importance can provide information about which features are heavily used by the ensemble, but feature importance does not completely explain an individual prediction.

Therefore, model interpretability decreases as the model structure becomes more complex.

---

## 7. Feature Importance

The trained models identified several important features.

For the Decision Tree, the largest feature importance was associated with:

**displacement: 0.6672**

followed by:

**horsepower: 0.1771**

For the Random Forest:

**displacement: 0.4165**

was the largest feature importance, followed by:

**horsepower: 0.1692**

and

**weight: 0.1433**

These values describe how the trained models used the features during prediction.

They should not be interpreted as proof that a feature causes changes in MPG.

---

## 8. Computational Cost

Training time provides an approximate indication of computational cost within the execution environment used for the experiment.

For the baseline models:

- Linear Regression: **0.0344 seconds**
- Decision Tree: **0.0043 seconds**
- Random Forest: **0.3666 seconds**

The Random Forest required substantially more training time than the other baseline models.

The Random Forest complexity experiment also showed increasing training time as the number of trees increased.

However, training time depends on hardware, software environment, and system load. Therefore, these measurements should be interpreted as observations from this experiment rather than universal benchmarks.

---

## 9. When Should a Simpler Model Be Preferred?

The results demonstrate that model selection should not be based only on predictive performance.

Random Forest achieved the highest predictive performance in this experiment, but it also had greater structural complexity and computational cost and was less directly interpretable than Linear Regression.

Linear Regression produced lower predictive performance but provided a simpler and more interpretable model with relatively stable generalization.

A simpler model may therefore be appropriate when:

- Its predictive performance is sufficient for the application.
- Interpretability is important.
- Computational resources are limited.
- The additional performance of a complex model is small.
- The simpler model provides more stable or understandable behaviour.

A more complex model may be appropriate when the improvement in predictive performance is important enough to justify the additional computational cost and reduced interpretability.

The choice therefore depends on the requirements of the application rather than predictive performance alone.

---

## 10. Critical Evaluation and Limitations

### 10.1 Dataset Size

The Auto MPG dataset contains 392 usable observations after preprocessing.

A relatively small dataset may produce results that vary when a different dataset or sample is used.

### 10.2 Single Train/Test Split

The main test results are based on one 80/20 train/test split.

Although 5-fold cross-validation was also used, repeated train/test splits could provide additional information about performance variability.

### 10.3 Dataset Characteristics

The Auto MPG dataset represents automobiles from a particular historical period.

Therefore, the conclusions may not directly generalize to modern vehicles or other domains.

### 10.4 Training Time

Training time depends on the execution environment.

The measured times should therefore be treated as relative observations within this experiment rather than universal computational benchmarks.

### 10.5 Different Complexity Measures

Complexity is represented differently for different model families.

Linear Regression uses coefficients, while tree-based models use measures such as depth, nodes, and number of trees.

Therefore, these quantities should not be treated as directly equivalent numerical units of complexity.

---

## 11. Overall Finding

The investigation provides evidence that increasing model complexity can improve predictive performance, but the improvement is not always proportional to the increase in complexity.

For Decision Trees, increasing depth produced very high training performance but also increased the difference between training and unseen-data performance.

For Random Forest, increasing the number of trees improved performance initially, but the improvement became small after 50 trees while computational cost continued to increase.

The results therefore demonstrate that a model should not be selected solely because it achieves the highest predictive score.

Model complexity, generalization, interpretability, computational requirements, and the requirements of the application should all be considered.

---

## 12. Conclusion

The investigation examined when a simpler model should be preferred to a more complex model.

The experiments showed that more complex models can improve predictive performance, but increasing complexity does not always produce a proportional improvement in generalization.

The Decision Tree experiment demonstrated that increasing depth can increase training performance substantially while increasing the risk of overfitting.

The Random Forest experiment demonstrated that increasing the number of trees can improve performance initially, but additional trees eventually provide diminishing returns while increasing computational cost.

Therefore, a more complex model is not automatically preferable simply because it produces a higher predictive score. A simpler model can be appropriate when its performance is sufficient and its advantages in interpretability, computational efficiency, and simplicity are important.

These conclusions are limited to the Auto MPG dataset and the experimental conditions used in this investigation. Further experiments using other datasets and repeated experimental settings would be required to determine whether the same behaviour occurs more generally.

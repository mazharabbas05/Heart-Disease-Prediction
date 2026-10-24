# Heart Disease Prediction

Team project (4 members): predict whether a patient has heart disease from clinical measurements and compare five classification models.

## Dataset

- UCI Heart Disease (Cleveland) data, 303 patients, 13 features plus the `target` column.
- No missing values; 1 duplicate row. Class split: 165 with target = 1, 138 with target = 0.
- Features include age, sex, chest pain type (`cp`), resting blood pressure, cholesterol, resting ECG, maximum heart rate (`thalach`), exercise-induced angina (`exang`), ST depression (`oldpeak`), slope, number of major vessels (`ca`) and `thal`.

The notebook loads the CSV straight from a public GitHub copy of the dataset.

## Method

1. Checked data quality and looked at how strongly each feature is correlated with the target.
2. Split the data 75% train / 25% test (stratified).
3. Trained five models: Logistic Regression, Decision Tree, Random Forest, SVM and KNN. Scaling is done inside a pipeline, so it is fitted on the training data only.
4. Compared them with test accuracy, 5-fold cross-validation, 30 repeated random splits and a confusion matrix.

## Results

Single 75/25 split (test set of 76 patients):

| Model | Test accuracy |
|---|---|
| Random Forest | 78.9% |
| Logistic Regression | 76.3% |
| SVM | 76.3% |
| KNN | 76.3% |
| Decision Tree | 72.4% |

5-fold cross-validation:

| Model | Mean accuracy | Std |
|---|---|---|
| Logistic Regression | 84.2% | 4.5 |
| SVM | 82.2% | 5.3 |
| Random Forest | 81.9% | 4.4 |
| KNN | 79.8% | 7.1 |
| Decision Tree | 72.9% | 6.5 |

Mean over 30 repeated 75/25 splits: SVM 83.7%, Logistic Regression 83.5%, Random Forest 83.4%, KNN 83.0%, Decision Tree 75.0%.

### What this shows

- With only 303 patients, a single split changes the ranking of the top models. Logistic Regression, SVM, Random Forest and KNN are all close, at roughly 80 to 84% accuracy; the Decision Tree is clearly weaker.
- The features most strongly correlated with the target are exercise-induced angina (0.44), chest pain type (0.43), ST depression (0.43) and maximum heart rate (0.42).
- This is a small dataset and a learning project, not a clinical tool.

## How to run

```bash
pip install pandas numpy matplotlib scikit-learn jupyter
jupyter notebook Heart_Disease_Prediction.ipynb
```

The notebook needs an internet connection to read the dataset.

## Tools

Python, Pandas, NumPy, Scikit-learn, Matplotlib, Jupyter Notebook

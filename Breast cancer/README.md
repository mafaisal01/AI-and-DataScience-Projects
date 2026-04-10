
````markdown
# 🎗️ Breast Cancer Prediction using Logistic Regression

This project builds a **machine learning model** to predict whether breast cancer is **malignant (0)** or **benign (1)** using the **Breast Cancer Wisconsin Dataset** available in `sklearn.datasets`.

The model uses **Logistic Regression** for binary classification and achieves over **92% accuracy** on test data.

---

## 🧩 Project Workflow

1. Importing Dependencies  
2. Data Collection, Exploration and Analysis
3. Separating Features and Target
4. Data Preprocessing (Standardization)  
5. Splitting the Data (Train-Test Split)
6. Model Training (Logistic Regression)
7. Model Evaluation
8. Making Predictions
9. Data Source

  
---

## ⚙️ 1. Importing the Dependencies

```python
# Importing required libraries
import numpy as np                         # For numerical computations
import pandas as pd                        # For handling tabular data
import sklearn.datasets                    # For loading built-in datasets
from sklearn.model_selection import train_test_split  # For splitting data
from sklearn.linear_model import LogisticRegression    # Logistic Regression algorithm
from sklearn.metrics import accuracy_score             # For evaluating model performance
````

---

## 📊 2. Data Collection, Exploration and Analysis

```python
# Loading the dataset from sklearn
breast_cancer_dataset = sklearn.datasets.load_breast_cancer()

# Displaying dataset structure
print(breast_cancer_dataset)

# The dataset includes: 569 samples and 30 numerical features | Target:  0 = Malignant, 1 = Benign
# Source: UCI Machine Learning Repository

# Loading the Data into a DataFrame : Creating a pandas DataFrame with feature names
data_frame = pd.DataFrame(
    breast_cancer_dataset.data, 
    columns=breast_cancer_dataset.feature_names
)

# Then, we add the target column: Adding the 'label' column (Target)
data_frame['label'] = breast_cancer_dataset.target


# Displaying first 5 rows with coloums of the dataset summary : Helps understand datasets summary format and features
data_frame.head()

# Displaying last 5 rows with coloums of the dataset summary : Helps understand datasets summary format and features
data_frame.tail()


# Displaying dimensions: Returns (rows, columns) of the dataset summary : Helps understand datasets summary format and features
data_frame.shape
# Output: (569, 31)


# Displaying all information of the dataset summary : Helps understand datasets summary format and features
data_frame.info()

# Displaying No missing values detected of the dataset summary : Helps understand datasets summary format and features
data_frame.isnull().sum()


# Displaying statistical (Provides mean, std, min, max, etc. for each feature) of the dataset summary : Helps understand datasets summary format and features
data_frame.describe()


# Displaying class distribution (Benign vs Malignant cases | 0 = Malignant, 1 = Benign) of the dataset summary : Helps understand datasets summary format and features
data_frame['label'].value_counts()

# Output:
# 1 (Benign)    357
# 0 (Malignant) 212

 # So, about 63% benign and 37% malignant cases.


# Displaying mean values for each class distribution of the dataset summary : Helps understand datasets summary format and features
data_frame.groupby('label').mean()


```


---

## 3. Separating Features and Target

```python
# Independent variables (features)
X = data_frame.drop(columns='label', axis=1)

# Dependent variable (target)
Y = data_frame['label']

print(X.shape)  # (569, 30)
print(Y.shape)  # (569,)
```

---

## 4. Data Preprocessing (Standardization)  
-- Not Use in this 



## 5. Splitting the Data (Train-Test Split)  

```python
# Splitting into training and testing datasets
X_train, X_test, Y_train, Y_test = train_test_split(
    X, Y, test_size=0.2, random_state=2
)

print(X.shape, X_train.shape, X_test.shape)
# Output: (569, 30) (455, 30) (114, 30)
```

---

## 6. Model Training — Logistic Regression

```python
# Initializing the Logistic Regression model
model = LogisticRegression()

# Training the model using training data
model.fit(X_train, Y_train)
```

> ⚠️ You may see a **ConvergenceWarning**.
> This can be resolved by scaling data or increasing `max_iter`.

---

## 7. Model Evaluation

```python
# Accuracy on training data
X_train_prediction = model.predict(X_train)
training_data_accuracy = accuracy_score(Y_train, X_train_prediction)

print('Accuracy on training data =', training_data_accuracy)
```

**Output:**

```
Accuracy on training data = 0.949
```

```python
# Accuracy on test data
X_test_prediction = model.predict(X_test)
test_data_accuracy = accuracy_score(Y_test, X_test_prediction)

print('Accuracy on test data =', test_data_accuracy)
```

**Output:**

```
Accuracy on test data = 0.93
```

✅ The model performs very well — ~95% training accuracy and ~93% test accuracy.

---

## 8. Making a Predictive System

```python
# Example input data for prediction
input_data = (
    13.54,14.36,87.46,566.3,0.09779,0.08129,0.06664,0.04781,
    0.1885,0.05766,0.2699,0.7886,2.058,23.56,0.008462,0.0146,
    0.02387,0.01315,0.0198,0.0023,15.11,19.26,99.7,711.2,
    0.144,0.1773,0.239,0.1288,0.2977,0.07259
)

# Converting input data to numpy array
input_data_as_numpy_array = np.asarray(input_data)

# Reshaping since we’re predicting for a single instance
input_data_reshaped = input_data_as_numpy_array.reshape(1, -1)

# Making prediction
prediction = model.predict(input_data_reshaped)
print(prediction)

# Output result
if prediction[0] == 0:
    print('The Breast Cancer is Malignant')
else:
    print('The Breast Cancer is Benign')
```

**Output Example:**

```
[1] The Breast Cancer is Benign
```

---


## 9. Dataset Source

**Breast Cancer Wisconsin (Diagnostic) Dataset**
Available in `sklearn.datasets`
Originally from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+%28diagnostic%29)

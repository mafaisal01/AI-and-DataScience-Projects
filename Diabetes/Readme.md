
````markdown
# 🩺 Diabetes Prediction using Support Vector Machine (SVM)

This project uses the **PIMA Indians Diabetes Dataset** to build a machine learning model that predicts whether a person is diabetic or not based on various health parameters.
The model uses **Support Vector Machine (SVM)** with a linear kernel for classification.

---

## 🧩 Project Structure

1. Import Dependencies  
2. Data Collection & Analysis
3. Separating Features and Target  
4. Data Preprocessing (Standardization)  
5. Splitting the Data (Train-Test Split)  
6. Model Training (SVM Classifier)  
7. Model Evaluation  
8. Making Predictions
9. Model Summary (Result)
10. Key insights
11. Data Source

---

## ⚙️ Step-by-Step Implementation

### 1. Importing the Dependencies
```python
# Importing necessary libraries
import numpy as np                   # For numerical operations
import pandas as pd                  # For handling datasets in DataFrame format
from sklearn.preprocessing import StandardScaler  # For feature standardization
from sklearn.model_selection import train_test_split  # For splitting data into train and test sets
from sklearn import svm              # For Support Vector Machine algorithm
from sklearn.metrics import accuracy_score  # For evaluating model performance
````

---

### 2. Data Collection and Analysis

```python
# Loading the PIMA Diabetes Dataset
diabetes_dataset = pd.read_csv('/content/diabetes.csv')  # Reads the CSV file into a pandas DataFrame

# Displaying first 5 rows of the dataset
diabetes_dataset.head()  # Helps understand data format and features

# Checking dataset dimensions
diabetes_dataset.shape   # Returns (rows, columns)

# Statistical summary of dataset
diabetes_dataset.describe()  # Provides mean, std, min, max, etc. for each feature

# Checking distribution of diabetic vs non-diabetic cases
diabetes_dataset['Outcome'].value_counts()  # 0 = Non-diabetic, 1 = Diabetic

# Comparing mean values of features based on Outcome
diabetes_dataset.groupby('Outcome').mean()  # Helps find feature differences between classes
```

---

### 3. Separating Features and Target

```python
# Separating input features (X) and output label (Y)
X = diabetes_dataset.drop(columns='Outcome', axis=1)  # All columns except 'Outcome'
Y = diabetes_dataset['Outcome']                      # Target variable
```

---

### 4. Data Preprocessing (Standardization)  

Machine learning models work better when data is standardized (mean = 0, std = 1).

```python
# Standardizing the data
scaler = StandardScaler()     # Creates a StandardScaler object
scaler.fit(X)                 # Fits the scaler on the feature data

standardized_data = scaler.transform(X)  # Transforms X into standardized format

# Updating X with standardized values
X = standardized_data
Y = diabetes_dataset['Outcome']
```

---

### 5. Splitting the Data (Train-Test Split)

Split data into training and testing sets to evaluate model performance.

```python
# Splitting the dataset into training and testing data
X_train, X_test, Y_train, Y_test = train_test_split(
    X, Y, test_size=0.2, stratify=Y, random_state=2
)

# Checking the size of each split
print(X.shape, X_train.shape, X_test.shape)
# Output Example: (768, 8) (614, 8) (154, 8)
```

---

### 6. Training the Model

```python
# Initializing the Support Vector Machine Classifier
classifier = svm.SVC(kernel='linear')  # Linear kernel is used for binary classification

# Training the SVM model with training data
classifier.fit(X_train, Y_train)
```

---

### 7. Model Evaluation

```python
# Predicting the training data
X_train_prediction = classifier.predict(X_train)
training_data_accuracy = accuracy_score(X_train_prediction, Y_train)

print('Accuracy score of the training data:', training_data_accuracy)

# Predicting the test data
X_test_prediction = classifier.predict(X_test)
test_data_accuracy = accuracy_score(X_test_prediction, Y_test)

print('Accuracy score of the test data:', test_data_accuracy)
```

**Example Output:**

```
Accuracy score of the training data :  0.7866
Accuracy score of the test data :  0.7727
```

---

### 8. Making a Predictive System

This allows the user to input new data and predict whether the person is diabetic.

```python
# Example input data for prediction
input_data = (5,166,72,19,175,25.8,0.587,51)  # Feature values for one person

# Converting input data to a NumPy array
input_data_as_numpy_array = np.asarray(input_data)

# Reshaping array as model expects 2D input (1 sample, n features)
input_data_reshaped = input_data_as_numpy_array.reshape(1, -1)

# Standardizing the new input data using the same scaler
std_data = scaler.transform(input_data_reshaped)

# Making prediction
prediction = classifier.predict(std_data)

# Outputting result
if (prediction[0] == 0):
    print('The person is not diabetic')
else:
    print('The person is diabetic')
```

**Example Output:**

```
The person is diabetic
```

---

## 📊 Model Summary (Result)

| Dataset       | Accuracy |
| ------------- | -------- |
| Training Data | ~78.6%   |
| Test Data     | ~77.2%   |

---

## 🧠 Key Insights

* **Data Standardization** improves model convergence.
* **Linear SVM** performs well on linearly separable data.
* The dataset shows moderate accuracy, meaning there’s potential for improvement with:

  * Feature engineering
  * Non-linear kernels (e.g., `rbf`)
  * Hyperparameter tuning

---

## 🧾 Dataset Source

[PIMA Indians Diabetes Database - Kaggle](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)

---



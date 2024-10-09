# Loading Datasets
### Built-in Datasets
```
from sklearn.datasets import load_iris

iris = load_iris()
X = iris.data
y = iris.target
```

# Train-Test Split
```
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
```
- __`X` and `y`:__ The feature matrix and target vector.
- `test_size:` The proportion of the dataset to include in the test split. It can be a float (0.2 for 20%) or an integer (20 for 20 samples).
- `train_size:` The proportion of the dataset to include in the training split. Typically, you set either test_size or train_size, but not both.
- `random_state:` Controls the shuffling applied to the data before splitting. Setting this to a fixed number ensures reproducibility.
- `shuffle:` Whether or not to shuffle the data __before splitting.__ The __default__ is __True__.

# Supervised Learning Algorithms
- Regression
    - Linear Regression
    - Polynomial Regression
    - Ridge and Lasso Regression
    - Decision Tree Regression
    - Random Forest Regression
    - Support Vector Regression (SVR)
- Classification
    - Logistic Regression
    - k-Nearest Neighbors (KNN)
    - Support Vector Machines (SVM)
    - Decision Tree Classifier
    - Random Forest Classifier
    - Gradient Boosting Classifier (including XGBoost)
    - Naive Bayes
    - Neural Networks (Basic implementation using MLPClassifier)

# Unsupervised Learning Algorithms
- Clustering
    - k-Means Clustering
    - Hierarchical Clustering
    - DBSCAN
- Dimensionality Reduction
    - Principal Component Analysis (PCA)
    - t-Distributed Stochastic Neighbor Embedding (t-SNE)
- Anomaly Detection
    - Isolation Forest
    - One-Class SVM

# Model
- `model = LinearRegression()` - is used to create model
- `model.fit(X_train, y_train)` - is used to train the model
- `y_pred = model.predict(X_test)` - is used to make the predection
- `joblib.dump(model, "file_name.pkl")` - is used to save the train model
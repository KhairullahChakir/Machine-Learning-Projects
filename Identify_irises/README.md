# Iris Classification with K-Nearest Neighbors (KNN)

This is a **machine learning project** that classifies iris flowers into three species: **Setosa, Versicolor, and Virginica**, using the classic **Iris dataset** from UCI.

## Project Overview

- Dataset: Iris dataset (150 samples, 4 features, 3 classes)
- Features used:
  - Sepal length (cm)
  - Sepal width (cm)
  - Petal length (cm)
  - Petal width (cm)
- Model: K-Nearest Neighbors (KNN)
- Tools: Python, Jupyter Notebook, pandas, seaborn, matplotlib, scikit-learn

## Features

1. Load and explore the Iris dataset.
2. Visualize feature relationships using scatter plots.
3. Split the data into training and testing sets.
4. Train a KNN model.
5. Evaluate the model’s accuracy.
6. Predict new iris flowers interactively using a custom function.

## Usage

1. Open the Jupyter Notebook `Identify irises.ipynb`.
2. Run each cell step by step.
3. To predict a new flower, use the `predict_iris(sepal_length, sepal_width, petal_length, petal_width)` function.

Example:

```python
predict_iris(5.1, 3.5, 1.4, 0.2)
# Output: The model predicts this iris is: setosa

## Project Summary: House Price Prediction (Linear Regression)

### 1. Project Goal

Predict house prices based *only* on house size (square feet) using a simple linear regression model built from scratch.

### 2. Dataset Creation

* We created a dataset with **one feature**: `Size_sqft` (house size in square feet).
* The target variable is `Price_USD` (house price in dollars).
* Generated 200 rows of data to give the model some room to learn.
* Example:

  ```
  Size_sqft, Price_USD
  3674, 718427
  1360, 277939
  … (200 total rows)
  ```
* Checked basic statistics: mean size ≈ 2334 sqft, mean price ≈ $465,557. No missing values.
* Verified roughly linear upward trend between size and price.

### 3. Data Splitting

* We split the dataset into **training** and **testing** sets so the model can be evaluated on unseen data.
* Without external libraries, we shuffled the data and used an **80/20 split**: 80% for training, 20% for testing.

### 4. Model Definition

* We defined the hypothesis (model) as:
  [
  f_{w,b}(x) = w \times x + b
  ]
  where:

  * `w` is the **weight** (slope)
  * `b` is the **bias** (intercept)
  * `x` is the input feature (Size_sqft)
  * `ŷ = f_{w,b}(x)` is the predicted price
* The objective: find `w` and `b` so that predictions are as close as possible to real prices.

### 5. Cost Function

* To measure how good (or bad) the model is, we used the *Squared Error Cost Function*:
  [
  J(w,b) = \frac{1}{2m} \sum_{i=1}^{m} \big(f_{w,b}(x^{(i)}) - y^{(i)}\big)^2
  ]
  where:

  * `m` = number of training examples
  * `x^{(i)}` = size of house for example i
  * `y^{(i)}` = actual price for example i
  * `f_{w,b}(x^{(i)})` = predicted price
* Why `1/(2m)`?

  * `1/m` gives the *average* squared error (so cost doesn’t scale unfairly with number of examples)
  * Extra `½` makes mathematics (gradient calculations) cleaner.

### 6. Gradient Descent (Training)

* We computed gradients:
  [
  \frac{\partial J}{\partial w} = \frac{1}{m} \sum (f_{w,b}(x^{(i)}) - y^{(i)}) \cdot x^{(i)}
  ]
  [
  \frac{\partial J}{\partial b} = \frac{1}{m} \sum (f_{w,b}(x^{(i)}) - y^{(i)})
  ]
* Update rules:

  ```
  w = w − α * (∂J/∂w)
  b = b − α * (∂J/∂b)
  ```

  where `α` is the learning rate.
* After training: final `w ≈ 199.5661`, `b ≈ 0.0597`. Model learned that *approximately $200 per additional square foot* influences the price.

### 7. Model Evaluation

* On training data:

  * **MAE (Mean Absolute Error) ≈ $10,495** → on average, the model’s prediction is off by about $10.5K.
  * **RMSE (Root Mean Squared Error) ≈ $11,983** → typical error magnitude (with larger errors weighted more) is around $12K.
* On test data:

  * **MAE ≈ $9,717** → generalizes well: average error under $10K.
  * **RMSE ≈ $11,337** → still around $11K.
* Interpretation: For houses priced in the hundreds of thousands, an error around $10-12K is acceptable for a single-feature baseline model.

### 8. Visualization & Saving the Model

* We plotted a scatter of `Size_sqft` vs `Price_USD` with the fitted line overlaid — visually confirmed the linear relationship and fit.
* We saved the model parameters (`w`, `b`) to a file (e.g., `house_price_model.pkl`) so we can load later without retraining.

### 9. Summary of Results

* Model learned a **clear linear trend** between house size and price.
* Model generalizes reasonably well (train/test errors close).
* Because only one feature is used, there’s still room for improvement (multiple features, non-linear models, regularization).
* Good baseline project: clean, from scratch, no library black-boxes (except for basic I/O), tracked all steps.


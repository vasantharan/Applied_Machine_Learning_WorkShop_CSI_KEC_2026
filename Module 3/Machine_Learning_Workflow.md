# Module 3 - Machine Learning Workflow

## Key stages in the workflow

### 1. Problem Definition
   This is the most important step.

- Clearly define what you want to predict.
- Identify:
  - Input features (X)
  - Output/Target (y)
- Decide problem type:
  - Regression → Predict numbers
  - Classification → Predict categories

**Example:**
Predict house price using size and number of rooms.
   
### 2. Data Collection
Data can come from:

- CSV files
- Databases
- APIs
- Sensors
- Surveys

Important checks:
- Is the data relevant?
- Is it sufficient?
- Is it clean?

Example dataset:

```python
import pandas as pd

data = {
    "size": [1000, 1500, 1200, 1800, 2000],
    "rooms": [2, 3, 2, 4, 4],
    "price": [50, 75, 60, 90, 100]
}

df = pd.DataFrame(data)
print(df)
```

### 3. Data Preprocessing
Raw data is usually messy and cannot be directly used for training.
Common tasks include:
- Handling missing values (fill or remove)
- Removing duplicates
- Detecting and treating outliers
- Encoding categorical variables (Label Encoding / One-Hot Encoding)
- Feature scaling (Normalization or Standardization)

Separate features (X) and target (y):

```python
X = df[["size", "rooms"]]
y = df["price"]
```
At this stage, machine sees only numbers.

### 4. Exploratory Data Analysis (EDA)

**Goal:** Understand patterns in the data before training the model.

EDA helps us explore and analyze the dataset so we can make better decisions during model building.

**What We Do in EDA:**
- Visualize data
- Identify trends
- Detect anomalies (outliers or unusual values)
- Understand relationships between features

Example: Visualizing Relationship Between Size and Price

```python
import matplotlib.pyplot as plt

plt.scatter(df["size"], df["price"])
plt.xlabel("Size")
plt.ylabel("Price")
plt.show()
```
**Humans:**
- Understand increasing or decreasing trends visually
- Identify whether the relationship looks linear or non-linear
- Spot unusual points (outliers)

We use graphs to build intuition.

**Machines:**
- Do not see graphs
- Do not understand visuals
- Only process numerical values

Graphs are created for human understanding, not for the machine.
The model learns only from numbers, not from visualizations.

### 5. Train-Test Split
We split data to evaluate performance on unseen samples.
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```
**Purpose:**
- Training data → Used to learn patterns
- Testing data → Used to evaluate generalization

**Without splitting:**
- Model may memorize instead of learning.

### 6. Model Selection
Choose algorithm based on problem type.

**For regression problems:** we use Linear Regression, or any other regressor algorithm

**For classification problmes:** we use Logistic Regression, Naive Bayes, Decision tree or any other classifier algorithm

Model choice depends on:
- Dataset size
- Feature complexity
- Linear or non-linear relationship
- Regression vs Classification problem

**Examples:**
- Linear Regression → Continuous values
- Logistic Regression → Binary classification
- Decision Trees → Non-linear problems

### 7. Model Training
Training means learning mathematical relationships from data. Internally, the model learns an equation like,
```
Price = w1*(size) + w2*(rooms) + b
```
Where:
- w1, w2 → weights
- b → bias/intercept
The model adjusts these values to minimize error using optimization techniques.

### 8. Model Evaluation
- Measure model performance on unseen data (test data)
- Use metrics appropriate to problem type:
  - Regression → Mean Squared Error (MSE), Root Mean Squared Error (RMSE), R² score
  - Classification → Accuracy, Precision, Recall, F1-score
- Detect overfitting:
  - High training accuracy, low test accuracy
- Detect underfitting:
  - Low accuracy on both training and test sets
- Ensure the model generalizes well to new data

#### Classification Report
Provides a summary of precision, recall, and F1-score for each class.

<table>
  <tr>
    <th>Class</th>
    <th>Precision</th>
    <th>Recall</th>
    <th>F1-Score</th>
    <th>Support</th>
  </tr>
  <tr>
    <td>0</td>
    <td>0.90</td>
    <td>0.85</td>
    <td>0.87</td>
    <td>100</td>
  </tr>
  <tr>
    <td>1</td>
    <td>0.88</td>
    <td>0.92</td>
    <td>0.90</td>
    <td>120</td>
  </tr>
</table>

**Explanation:**
- **Precision:** Fraction of correct positive predictions among all predicted positives
- **Recall:** Fraction of correct positive predictions among all actual positives
- **F1-Score:** Harmonic mean of precision and recall
- **Support:** Number of actual instances of the class

#### Confusion Matrix

Shows actual vs predicted class counts.

<table>
  <tr>
    <th>Actual \ Predicted</th>
    <th>0</th>
    <th>1</th>
  </tr>
  <tr>
    <td>0</td>
    <td>85</td>
    <td>15</td>
  </tr>
  <tr>
    <td>1</td>
    <td>10</td>
    <td>110</td>
  </tr>
</table>

**Explanation:**
- Diagonal cells → Correct predictions
- Off-diagonal → Misclassifications
- Helps identify which class is being confused with another
- Essential for improving classification models
  
### 9.  Model Saving
- Save trained models for reuse without retraining
- Common formats:
  - `pickle`
  - `joblib` and so on
- Load saved model later for predictions or deployment
- Helps in versioning and reproducibility

### 10. Deployment and Monitoring
- Deployment exposes the model to real users via API or web service
- Can use frameworks like Flask, FastAPI, or cloud platforms
- Accepts input and returns predictions
- Monitoring ensures model continues to perform well:
  - Track accuracy over time
  - Detect data drift or concept drift
  - Retrain model when performance drops
- Maintains reliability and relevance in production environments

---

## How humans see the data vs How machines see the data

### 1. Numerical Data
**Human View:**
<table>
  <tr>
    <th>Size (sqft)</th>
    <th>Rooms</th>
    <th>Price (Lakhs)</th>
  </tr>
  <tr>
    <td>1000</td>
    <td>2</td>
    <td>50</td>
  </tr>
  <tr>
    <td>1500</td>
    <td>3</td>
    <td>75</td>
  </tr>
</table>

**Machine View:**
```
X = [[1000, 2],
[1500, 3]]
y = [50, 75]
```
- Machine sees only numbers
- Learns relationships mathematically: `Price = w1*Size + w2*Rooms + b`
  
### 2. Text Data

**Human View:**

| Review Text             | Sentiment |
|-------------------------|-----------|
| "I loved this movie"    | Positive  |
| "It was boring and bad" | Negative  |

**Machine View after Feature Extraction (EDA):**

- Convert words into numerical features (e.g., Bag-of-Words, TF-IDF):

<table>
  <tr>
    <th>loved</th>
    <th>movie</th>
    <th>boring</th>
    <th>bad</th>
  </tr>
  <tr>
    <td>1</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>1</td>
  </tr>
</table>

- Each review becomes a numeric vector
- Model sees only the vector, not the sentence meaning

### 3. Image Data

**Human View:**

<div style="font-size: 100px;">
😀
</div>

- Humans see a **smiley face**
- Recognize patterns, features like eyes, mouth, expression

**Machine View (Pixel Matrix):**
<table>
  <tr>
    <td>0</td><td>0</td><td>1</td><td>1</td><td>0</td>
  </tr>
  <tr>
    <td>0</td><td>1</td><td>0</td><td>0</td><td>1</td>
  </tr>
  <tr>
    <td>1</td><td>0</td><td>0</td><td>0</td><td>1</td>
  </tr>
  <tr>
    <td>0</td><td>1</td><td>0</td><td>0</td><td>1</td>
  </tr>
  <tr>
    <td>0</td><td>0</td><td>1</td><td>1</td><td>0</td>
  </tr>
</table>

- Machine interprets the image as **pixel intensity values**
- Learning happens from these numerical patterns, not visual recognition

---

## Let's have a hands on

Refer the [`main.ipynb`](./main.ipynb) file
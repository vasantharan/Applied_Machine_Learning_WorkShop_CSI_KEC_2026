# Module 4 - Hands on Model Development

## Datasets

**Regression:** https://www.kaggle.com/datasets/zafarali27/house-price-prediction-dataset
**Classification:** https://www.kaggle.com/datasets/taweilo/loan-approval-classification-data

---

## Pickle vs Joblib
Both **Pickle** and **Joblib** are used to save and load trained models in Python. However, they have practical differences — especially important for ML workshops and real-world deployment.

### What is Pickle?
Pickle is a built-in Python module used for serializing and de-serializing Python objects.

**Advantages**
- Built into Python (no installation needed)
- Can serialize almost any Python object
- Simple to use

**Limitations**
- Slower for large NumPy arrays
- Not optimized for large ML models
- Entire object stored as one file (no compression optimization by default)

## What is Joblib?
Joblib is a Python library optimized for storing large NumPy arrays efficiently.

It is commonly used with *scikit-learn models*.

**Advantages**
- Faster for large datasets
- Efficient for NumPy arrays
- Supports compression
- Better performance for ML models

**Limitations**
- External library (needs installation)
- Mostly used for ML objects

---

## Let's have a hands on
Refer the [`main.ipynb`](./main.ipynb) and [`main.py`](./main.py) files.
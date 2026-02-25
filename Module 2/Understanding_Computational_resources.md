# Module 2 - Understanding Computational Resources

## What is Computation?

- Computation is the process of performing calculations on data
- In ML, computation means processing large datasets using mathematical operations
- It involves matrix operations, multiplications, and optimization steps
- More data and complex models require more computational power

---

## Why ML Needs More Computation Than Normal Programs?

- ML processes large volumes of data
- Training involves repeated calculations (iterations)
- Models perform heavy mathematical operations
- Optimization algorithms run multiple times to reduce error
- Deep learning models require millions of parameter updates

---

## CPU vs GPU

- **CPU:** Handles general-purpose tasks and sequential processing
- **GPU:** Designed for parallel processing and performs many calculations simultaneously
- GPUs are faster for large matrix operations and deep learning models
- GPUs are highly effective for image and video processing because these tasks involve heavy parallel computations
- For most basic text processing tasks, CPUs are more suitable
- Traditional text models (TF-IDF, Naive Bayes, Logistic Regression) do not require massive parallel computation
- GPUs are mainly beneficial for large-scale deep learning models such as Transformer-based NLP systems
- CPUs are sufficient for small datasets and simpler machine learning models

---

## Role of RAM

- Stores data during model training
- Larger datasets require more memory
- Insufficient RAM can slow down or crash training
- Helps load and process datasets efficiently

---

## Local System vs Cloud

- **Local System:** Uses personal laptop or desktop resources
- **Cloud:** Uses remote servers with scalable hardware
- Cloud allows access to powerful GPUs and larger memory
- Cloud systems are suitable for large-scale training

---

## When to Use: Laptop / Cloud Platform

- Use **Laptop** for:
  - Small datasets
  - Learning and experimentation
  - Basic ML models

- Use **Cloud Platform** for:
  - Large datasets
  - Deep learning models
  - Production-level applications
  - High computational requirements
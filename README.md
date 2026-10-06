<h1 align="center">PerceptronX-Lib</h1>

<p align="center">
  <strong>From-scratch-oriented perceptron learning library for studying regression and classification mechanics.</strong><br>
  Implements custom gradient-descent training, scaling helpers, binary classification, linear regression, experimental multiclass handling, prediction, and metric-based scoring.
</p>

<p align="center">
  <img alt="Status" src="https://img.shields.io/badge/status-learning%20library-blue">
  <img alt="Language" src="https://img.shields.io/badge/language-Python-3776AB">
  <img alt="Core" src="https://img.shields.io/badge/core-NumPy-orange">
  <img alt="Metrics" src="https://img.shields.io/badge/metrics-scikit--learn-informational">
  <img alt="License" src="https://img.shields.io/badge/license-MIT-green">
</p>

<p align="center">
  <a href="#overview">Overview</a> ·
  <a href="#what-this-repo-contains">Contents</a> ·
  <a href="#implemented-api">API</a> ·
  <a href="#learning-flow">Learning Flow</a> ·
  <a href="#current-limitations">Limitations</a>
</p>

---

## Overview

**PerceptronX-Lib** is a compact educational machine-learning library implemented in Python.

Its purpose is to expose training mechanics that higher-level libraries normally hide: weight initialization, gradient updates, activation functions, scaling, validation splitting, prediction, and metric calculation.

The implementation automatically categorizes the target into a linear/regression, binary, or experimental multiclass path.

> Multiclass support is explicitly experimental in the source. The code warns that the learning path is for demonstration and may perform poorly on multiclass tasks.

---

## What This Repo Contains

| File | Purpose |
|---|---|
| <code>PerceptronX/Perceptron.py</code> | Complete <code>Perceptron</code> implementation and helper functions. |
| <code>README.md</code> | Project documentation. |
| <code>LICENSE</code> | MIT License. |

The repository does not currently contain packaging metadata, automated tests, notebooks, or a published package build.

---

## Implemented API

### Constructor

~~~python
Perceptron(
    learning_rate=0.001,
    validation_split=0.2,
    scaling="none",
    is_scaled=False,
    tolerance=1e-6
)
~~~

### <code>fit(X, y)</code>

The implementation selects a task path, optionally creates a validation split, performs scaling checks/transforms, runs gradient-descent updates, reports validation information, and stores learned weights/bias.

### <code>predict(X)</code>

- linear path → continuous values;
- binary path → sigmoid + 0.5 threshold;
- multiclass path → softmax + <code>argmax</code>.

<code>fit()</code> must be called before prediction.

### <code>score(X, y, metrics)</code>

The live implementation requires an explicit **third argument**: <code>metrics</code>.

| Task | Supported metric strings |
|---|---|
| Linear / regression | <code>mse</code>, <code>rmse</code>, <code>rmsle</code> |
| Binary classification | <code>accuracy</code>, <code>precision</code>, <code>recall</code>, <code>f1</code> |
| Multiclass classification | <code>accuracy</code>, <code>precision</code>, <code>recall</code>, <code>f1</code> |

Multiclass precision/recall/F1 use weighted averaging in the current source.

---

## Learning Flow

~~~text
pandas feature matrix + target
   ↓
Task-type detection
   ↓
Optional validation split
   ↓
Scaling checks / scaling transform
   ↓
Weight + bias initialization
   ↓
Gradient-descent loop
   ↓
Validation output
   ↓
predict(...)
   ↓
score(..., metrics)
~~~

---

## Dependencies

The implementation uses NumPy, pandas, scikit-learn utilities, and colorama.

~~~bash
pip install numpy pandas scikit-learn colorama
~~~

---

## Example

~~~python
from PerceptronX.Perceptron import Perceptron

model = Perceptron(
    learning_rate=0.001,
    validation_split=0.2,
    scaling="standard",
    tolerance=1e-6,
)

model.fit(X_train, y_train)
predictions = model.predict(X_test)
accuracy = model.score(X_test, y_test, "accuracy")
~~~

Choose a metric that matches the detected task type.

---

## Architecture

~~~text
Perceptron.py
├── Perceptron
│   ├── fit
│   ├── predict
│   └── score
├── gradient_descent_optimisation
├── prediction helpers
├── sigmoid / softmax helpers
├── scaling helpers
├── validation helper
├── one-hot encoding helper
└── loss / metric support
~~~

---

## Current Limitations

PerceptronX-Lib is a **learning library**, not a production ML framework.

Current boundaries include:

- no <code>pyproject.toml</code> / <code>setup.py</code>;
- no automated tests;
- no API stability contract;
- no serialized model format;
- potentially long training loops for strict tolerances;
- in-place dataframe scaling behavior in parts of the implementation;
- experimental multiclass logic;
- dependence on scikit-learn for metrics and train/validation splitting.

Strong code quality or a successful example run should not be presented as a general benchmark of model accuracy.

---

## License

Released under the **MIT License**. See <code>LICENSE</code>.

<h1 align="center">PerceptronX-Lib</h1>

<p align="center">
  <strong>Custom Python perceptron learning library.</strong><br>
  Implements regression, binary classification, experimental multiclass support, scaling helpers, gradient descent, prediction, and scoring.
</p>


<p align="center">
  <img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/AjaySoni-Dev/PerceptronX-Lib?style=social">
  <img alt="GitHub forks" src="https://img.shields.io/github/forks/AjaySoni-Dev/PerceptronX-Lib?style=social">
</p>


<p align="center">
  <img alt="status: learning library" src="https://img.shields.io/badge/status-learning%20library-blue">
  <img alt="stack: Python" src="https://img.shields.io/badge/stack-Python-informational">
  <img alt="license: MIT" src="https://img.shields.io/badge/license-MIT-green">
</p>

<p align="center">
  <a href="#overview">Overview</a> ·
  <a href="#implemented-api">Implemented API</a> ·
  <a href="#repository-structure">Repository Structure</a> ·
  <a href="#usage">Usage</a> ·
  <a href="#limitations">Limitations</a>
</p>

---

## Overview

**PerceptronX-Lib** is a small custom machine-learning library focused on perceptron-based learning. The project is useful for understanding how model training, scaling, gradient descent, prediction, and evaluation work internally.

The uploaded repository contains the implementation file and README, but it does not include packaging files such as `pyproject.toml`, `setup.py`, examples, tests, or notebooks. Because of that, this README describes it as a local learning library rather than claiming it is a complete production Python package.

## Implemented API

The main class is:

```python
Perceptron(
    learning_rate=0.001,
    validation_split=0.2,
    scaling="none",
    is_scaled=False,
    tolerance=1e-6
)
```

Implemented methods:

| Method | Purpose |
|---|---|
| `fit(X, y)` | Trains the perceptron and automatically detects binary, multiclass, or regression-style targets. |
| `predict(X)` | Generates predictions using learned weights and bias. |
| `score(X, y)` | Evaluates predictions using task-specific metrics. |

Helper functions include:

- gradient descent optimization,
- sigmoid activation,
- softmax helper,
- cost function,
- one-hot encoding,
- standard scaling,
- min-max scaling,
- scaled-data validation,
- regression and classification metrics.

## Repository Structure

| File | Purpose |
|---|---|
| `PerceptronX/Perceptron.py` | Main implementation containing the `Perceptron` class and helper functions. |
| `README.md` | Original documentation. |
| `LICENSE` | MIT license. |

## Dependencies

Install the likely required libraries:

```bash
pip install numpy pandas scikit-learn colorama
```

## Usage

Example local usage:

```python
from PerceptronX.Perceptron import Perceptron

model = Perceptron(
    learning_rate=0.001,
    validation_split=0.2,
    scaling="standard",
    is_scaled=False,
    tolerance=1e-6
)

model.fit(X_train, y_train)
predictions = model.predict(X_test)
score = model.score(X_test, y_test)
```

## Limitations

- The repo currently has no packaging configuration.
- The README previously mixed `IntelliNeuro` and `PerceptronX` naming, so this version uses the repository name consistently.
- The training loop can be expensive because it allows very high iteration counts.
- Multiclass support is experimental and should be tested carefully.
- There are no automated tests yet.
- The library depends on scikit-learn metrics and preprocessing utilities, so it is not a pure NumPy-only implementation.

## Recommended Improvements

- Add `pyproject.toml` or `setup.py`.
- Add example notebooks.
- Add unit tests.
- Add benchmark results on small datasets.
- Add clearer error messages.
- Add documentation for input shapes and supported target types.

## License

This project is licensed under the MIT License.

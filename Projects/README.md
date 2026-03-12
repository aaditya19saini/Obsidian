# Obsidian Knowledge Vault

A personal knowledge management system built with [Obsidian](https://obsidian.md), containing machine learning study notes, project documentation, and research materials.

---

## Table of Contents

- [Overview](#overview)
- [Getting Started](#getting-started)
- [Vault Structure](#vault-structure)
- [Contents](#contents)
  - [Machine Learning Notes](#machine-learning-notes)
  - [Projects](#projects)
  - [Personal](#personal)
- [Navigation Tips](#navigation-tips)

---

## Overview

This vault serves as an interconnected knowledge base covering:

- **Machine Learning** — Comprehensive study notes on algorithms, optimization, and model evaluation
- **Projects** — Technical documentation for a stock price prediction model built with LSTM neural networks
- **Personal** — Notes on bioprocess and downstream engineering topics

All content is written in Markdown and designed to be explored through Obsidian's graph view, backlinks, and full-text search.

---

## Getting Started

### Prerequisites

- [Obsidian](https://obsidian.md) (v1.5 or later)

### Opening the Vault

1. Install Obsidian from [obsidian.md](https://obsidian.md)
2. Launch Obsidian and click **Open folder as vault**
3. Select the root directory of this repository
4. Obsidian will load all settings, themes, and plugins automatically

### Enabled Core Plugins

The vault comes pre-configured with the following core plugins enabled:

| Plugin | Purpose |
|---|---|
| File Explorer | Browse notes by folder |
| Global Search | Full-text search across all notes |
| Graph View | Visualize connections between notes |
| Backlinks | See which notes reference the current note |
| Canvas | Create visual diagrams and mind maps |
| Quick Switcher | Jump to any note quickly (Ctrl+O) |
| Tags | Organize and filter notes by topic |
| Daily Notes | Time-based journaling |
| Templates | Reusable note templates |
| Command Palette | Access all commands (Ctrl+P) |
| Outline | Navigate headings within a note |
| Word Count | Track note length |
| Bookmarks | Save frequently visited notes |

---

## Vault Structure

```
Obsidian/
├── ML/              # Machine learning study notes (50+ files)
├── Projects/        # Project documentation and walkthroughs
├── Personal/        # Personal research and engineering notes
├── images/          # Embedded images referenced by notes
└── README.md        # This file
```

---

## Contents

### Machine Learning Notes

Located in the `ML/` folder — 50+ interconnected notes covering the full ML pipeline from fundamentals to advanced topics.

#### Linear Models & Regression
| Note | Topic |
|---|---|
| `Linear Regression.md` | OLS regression, cost function minimization |
| `normal equation.md` | Closed-form solution for linear regression |
| `pseduinverse of matrix.md` | Moore-Penrose pseudoinverse |
| `Ridge Regression.md` | L2 regularization to reduce overfitting |
| `Lasso Regression.md` | L1 regularization for sparse feature selection |
| `Elastic Net.md` | Combined L1 + L2 regularization |
| `Polynomial regression.md` | Extending linear models to non-linear data |

#### Classification
| Note | Topic |
|---|---|
| `Logistic Regression.md` | Binary classification with sigmoid function |
| `Logistic Regression 1.md` | Decision boundaries and probability thresholds |
| `Softmax Regression.md` | Multi-class classification |
| `softmax regression 1.md` | Softmax function derivation |
| `Support Vector Machines.md` | Hard and soft margin classifiers |
| `Dual problem.md` | SVM dual formulation |
| `Polynomial Kernel.md` | Kernel trick for non-linear boundaries |

#### Optimization
| Note | Topic |
|---|---|
| `Gradient decent.md` | Gradient descent fundamentals |
| `GRADIENT VECTOR.md` | Partial derivatives and gradient computation |
| `Batch Gradient Descent.md` | Full-dataset gradient updates |
| `Stochastic Gradient Descent.md` | Single-sample gradient updates |
| `Mini-batch Gradient Descent.md` | Mini-batch trade-offs |
| `Learning Rate.md` | Choosing and scheduling learning rates |
| `Sensitivity to learning rate--- Gradient Descent.md` | Effects of learning rate magnitude |
| `Convergence Rate.md` | How fast gradient descent converges |
| `Slow Convergence.md` | Diagnosing and fixing slow training |
| `Issues during Gradient descent.md` | Saddle points, plateaus, oscillations |
| `size of the downhill step.md` | Step size and momentum |
| `Early stopping.md` | Regularization via training termination |

#### Neural Networks
| Note | Topic |
|---|---|
| `Activation functions.md` | ReLU, sigmoid, tanh, and their properties |
| `Vanishing and Exploding Gradients.md` | Gradient flow problems in deep networks |
| `Regression MLP.md` | Multi-layer perceptron for regression tasks |

#### Ensemble Methods
| Note | Topic |
|---|---|
| `Ensemble Learning.md` | Motivation and types of ensemble methods |
| `Bagging and Pasting.md` | Bootstrap aggregating and subset sampling |
| `Out of bag Evaluation.md` | OOB score as a free validation metric |
| `Random Forests.md` | Feature randomness and tree aggregation |
| `Base estimators and transformer Mixin.md` | Scikit-learn estimator API |

#### Dimensionality Reduction
| Note | Topic |
|---|---|
| `PCA.md` | Principal Component Analysis |
| `Singular Value Decomposition (SVD).md` | SVD and its relationship to PCA |
| `Kernel PCA (kPCA).md` | Non-linear dimensionality reduction |
| `Manifold learning.md` | Locally Linear Embedding and t-SNE |

#### Model Evaluation & Tuning
| Note | Topic |
|---|---|
| `Bias-Variance Tradeoff.md` | Underfitting vs overfitting |
| `Generalization.md` | Generalization error and model capacity |
| `Cross Validation.md` | k-fold and stratified cross-validation |
| `Holdout Validation.md` | Train/validation/test splitting |
| `GRID SEARCH.md` | Exhaustive hyperparameter search |
| `Selecting Kernel and Tuning hyperparams.md` | SVM kernel selection strategies |
| `Root Mean Squared Error (RMSE).md` | RMSE as an evaluation metric |
| `cost function.md` | Loss functions overview |
| `Computational Complexity.md` | Big-O analysis of ML algorithms |

#### Feature Engineering
| Note | Topic |
|---|---|
| `Feature Scaling.md` | Why and when to scale features |
| `Min-max scaling.md` | Normalization to a fixed range |

---

### Projects

Located in the `Projects/` folder — technical documentation for a stock price prediction project.

#### Stock Price Prediction Model

An end-to-end LSTM-based model to forecast IBM's closing stock price using technical indicators and market index data.

**Files:**
- `project- stock price prediction model.md` — Feature engineering overview (technical indicators, index funds)
- `LSTM and lagged features (project).md` — Detailed notebook walkthrough (cell-by-cell)
- `Prompts.md` — Architecture planning for an AI Regulatory Compliance Platform

**Model Architecture:**

```
Input (60-day window × N features)
    │
    ▼
LSTM(50 units, return_sequences=True)
    │
    ▼
LSTM(50 units)
    │
    ▼
Dense(1)  →  Predicted closing price
```

Total parameters: ~30,651

**Data Pipeline:**

```
IBM.csv (5,350 rows × 63 columns)
    │
    ├── Technical Indicators: Bollinger Bands, RSI, ADX, CCI, ATR, ROC, Williams %R, Stochastic %K
    ├── Moving Averages: SMA (10, 20, 50-day), EMA
    └── Market Indices: QQQ, S&P 500 (INX), DJIA — with 1, 2, and 5-day lags
    │
    ▼
Train/Test Split  →  340 training / 81 test samples
    │
    ▼
MinMaxScaler (range: 0–1)
    │
    ▼
Reshape to LSTM format: (samples, 60 timesteps, features)
    │
    ▼
Train LSTM  →  Evaluate
```

**Model Performance:**

| Metric | Value |
|---|---|
| R² Score | 0.88 |
| MAPE | 3.27% |
| RMSE | 0.42 |
| MAE | 0.34 |

**Dependencies (for running the notebook):**

```
pandas
numpy
scikit-learn
keras / tensorflow
```

---

### Personal

Located in the `Personal/` folder — research notes on bioprocess engineering.

| Note | Topic |
|---|---|
| `Downstream Processing.md` | Filtration techniques and separation in bioprocessing |

---

## Navigation Tips

- **Graph View** (`Ctrl+G`) — See how notes link to each other visually
- **Quick Switcher** (`Ctrl+O`) — Jump to any note by typing its name
- **Search** (`Ctrl+Shift+F`) — Full-text search across all notes
- **Backlinks panel** — See which notes reference the note you are reading
- **Outline panel** — Navigate headings within a long note
- **Bookmarks** — Pin frequently visited notes to the sidebar

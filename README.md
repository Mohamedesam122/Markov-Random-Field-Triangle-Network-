# 🧠 Markov Random Field (MRF) Implementation

## 📌 Overview

This project implements a simple **Markov Random Field (MRF)** with three binary variables:

* **A, B, C ∈ {0,1}**

The goal is to compute:

* Joint distribution (unnormalized)
* Partition function (Z)
* Normalized probabilities
* Query probabilities
* Marginal probabilities

---

## 🔗 Model Structure

The variables form a circular graph:

```
A — B
|   |
C ——
```

### Maximal Cliques:

* {A, B}
* {B, C}
* {C, A}

---

## ⚙️ Clique Potentials (Factors)

Each pair of variables has a factor:

* **φ1(A, B)**

  * 4 if A == B
  * 2 otherwise

* **φ2(B, C)**

  * 5 if B == C
  * 1 otherwise

* **φ3(C, A)**

  * 3 if C == A
  * 1 otherwise

---

## 🧮 Mathematical Formulation

### Unnormalized Joint Distribution:

```
P̃(A, B, C) = φ1(A, B) × φ2(B, C) × φ3(C, A)
```

### Partition Function:

```
Z = Σ P̃(A, B, C)
```

### Normalized Probability:

```
P(A, B, C) = P̃(A, B, C) / Z
```

---

## 🚀 Features Implemented

### ✅ 1. Factor Functions

* Computes clique potentials using conditional logic

### ✅ 2. Joint Distribution

* Generates all 8 combinations of (A, B, C)
* Computes unnormalized scores

### ✅ 3. Partition Function (Z)

* Sums all scores manually (no built-in shortcuts)

### ✅ 4. Normalization

* Converts scores into valid probabilities

### ✅ 5. Query Function

* Returns probability of a specific configuration

### ✅ 6. Marginal Function

* Computes probability of a variable (e.g., P(A=1))

---

## 📂 Functions Overview

| Function               | Description                   |
| ---------------------- | ----------------------------- |
| `phi1(a, b)`           | Factor between A and B        |
| `phi2(b, c)`           | Factor between B and C        |
| `phi3(c, a)`           | Factor between C and A        |
| `all_comp()`           | Generates all configurations  |
| `partition_function()` | Computes Z                    |
| `normalize()`          | Normalizes probabilities      |
| `query(a,b,c)`         | Returns P(A,B,C)              |
| `marginal(var,val)`    | Computes marginal probability |

---

## ▶️ Example Usage

```python
joint = all_comp()
print(joint)

print(query(1,1,1))
print(marginal('A', 1))
```

---

## ⚠️ Constraints Followed

* ❌ No built-in probability libraries
* ❌ No hardcoded results
* ❌ No automatic normalization tools
* ✅ All computations done manually
* ✅ Explicit loops and calculations

---

## 🎯 Key Idea

This project demonstrates how to compute probabilities in an MRF using:

```
Local dependencies → Factor multiplication → Normalization
```

---

## 🧠 Takeaway

Instead of defining probabilities directly, we:

* Define relationships (factors)
* Compute scores
* Normalize using Z

---

## 👨‍💻 Authors
Ahmed Tarek
Ahmed Ibrahim
Mohammed Essam
Abdelrahman Emad
Esam Mamdouh

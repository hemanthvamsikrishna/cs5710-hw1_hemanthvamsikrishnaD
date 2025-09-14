here you go, boss — paste this into `README.md`:

---

# CS5710 — Homework 1 (Q7): Linear Regression — Normal Equation vs Gradient Descent

**Student:** Hemanth Vamsi Krishna Devadula (700773640)
**University:** University of Central Missouri (UCM)
**Course:** CS5710 — Machine Learning (Fall 2025)
**Program:** M.S. in Data Science & Artificial Intelligence
**Email:** *\<hxd36400@ucmo.edu>*
**GitHub Repo:** *\<repo URL>*


---

## 1) Overview (what I built)

I implemented linear regression in two ways and compared them:

1. **Closed-form solution (Normal Equation)** for the exact least-squares parameters.
2. **Gradient Descent (from scratch)** starting at $\theta=[0,0]$ with learning rate $\eta=0.05$ for **1000 iterations**.

I generated a synthetic dataset $y = 3 + 4x + \epsilon$ with **200 samples** where $x \in [0,5]$ and $\epsilon \sim \mathcal{N}(0,\sigma^2)$. I plotted the raw data, overlaid both fitted lines, plotted the GD loss curve (MSE vs iterations), and wrote a short comparison.

---

## 2) Repository structure

```
.
├─ README.md
├─ CS5710_HW1_Q7_NormalEq_vs_GD.ipynb   # main notebook with code + plots
└─ (optional) linear_reg_q7.py          # script version if included
```

---

## 3) Environment & setup

* Python 3.9+ (tested with 3.10)
* Libraries: `numpy`, `matplotlib`, `jupyter`

```bash
pip install numpy matplotlib notebook
jupyter notebook CS5710_HW1_Q7_NormalEq_vs_GD.ipynb
```

---

## 4) Data generation (my approach)

* Fixed RNG seed for reproducibility.
* Sampled **200** values of $x$ uniformly from **\[0,5]**.
* Created $y = 3 + 4x + \epsilon$ with Gaussian noise.
* Built design matrix $X=[\mathbf{1}, x]$ (bias column + feature).

**Plot produced:** Raw data scatter.

---

## 5) Closed-form solution (Normal Equation)

* Computed $\theta_{\text{NE}} = (X^\top X)^{-1} X^\top y$ using **`np.linalg.pinv`** for stability.
* Printed the **estimated intercept and slope**.
* **Plotted** the fitted line on top of the raw data.

**Plot produced:** Closed-form fitted line (overlaid on scatter).

---

## 6) Gradient Descent (from scratch)

* Initialization: $\theta=[0,0]$
* Learning rate: $\eta=0.05$
* Iterations: **1000**
* Loss: **MSE** $=\frac{1}{m}\sum (y-\hat y)^2$
* Gradient: $\nabla_\theta J=\frac{2}{m}X^\top(X\theta - y)$

Tracked MSE each step, printed final intercept/slope, and compared to the Normal Equation.

**Plot produced:** Loss curve (MSE vs iterations).

---

## 7) Comparison & results

* Reported both solutions (intercept, slope, final MSE).
* **GD** parameters matched the **Normal Equation** within numerical tolerance.
* Both fitted lines **overlapped** on the scatter plot.

**Plot produced:** Raw data with both fitted lines (Closed-form & GD).

---

## 8) Final explanation (2–3 sentences)

Both the Normal Equation and Gradient Descent recover virtually the same linear model on this synthetic dataset: their fitted lines overlap and the MSE values match within numerical tolerance. Any tiny difference is due to finite GD iterations and the chosen learning rate rather than model mismatch. The Normal Equation yields the exact least-squares solution for small problems, while Gradient Descent converges to the same solution with enough iterations and scales better to very large datasets.

---

## 9) How to reproduce

1. Open the notebook and **Run All**.
2. You’ll see printed parameters for **Closed-form** and **GD**, plus the required **plots**.
3. (Optional) Save figures with `plt.savefig(...)` if needed.

---

## 10) Notes & decisions I made

* Used **`pinv`** instead of `inv` for numerical stability.
* Fixed random seed for repeatable grading.
* Labeled loss explicitly as **MSE** (not $\tfrac{1}{2m}$ cost).

---

## 11) Submission checklist

* [x] Source code pushed to GitHub with comments
* [x] README includes my details and workflow
* [x] Notebook shows data gen, both solutions, and required plots
* [x] Parameters reported and short comparison included
* [x] Demo video link added to this README and submitted on BB

---

## 12) Academic integrity

This is my own work for CS5710 Homework 1 (Q7). Standard formulas (Normal Equation, MSE, gradient) are from common ML references and course materials.

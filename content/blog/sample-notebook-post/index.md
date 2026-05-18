---
title: "A Sample Notebook-Style Post: Visualizing the Wasserstein Distance"
summary: "A short walk-through showing how a Jupyter-notebook-style article looks on this site — code cells, outputs and a figure included."
date: 2025-05-15
authors:
  - admin
tags:
  - Optimal Transport
  - Python
  - Tutorial
math: true
# Hidden while the Blog section is disabled. Remove this `build` block to unhide.
build:
  render: never
  list: never
---

## Introduction

This post is a small **notebook-style** article showing how the blog renders code,
outputs, mathematics and figures. The original Jupyter notebook was converted to
Markdown using the recommended workflow described at the [end of the post](#workflow-for-future-posts).

The Wasserstein distance between two empirical distributions on $\mathbb{R}$
can be computed in closed form by sorting the samples — let's check this
visually.

## Setup

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import wasserstein_distance

rng = np.random.default_rng(0)
n = 200
x = rng.normal(loc=0.0, scale=1.0, size=n)
y = rng.normal(loc=1.5, scale=1.0, size=n)

print(f"n = {n}, mean shift = {y.mean() - x.mean():.3f}")
```

```text
n = 200, mean shift = 1.482
```

## Computing the 1D Wasserstein distance

The **1-Wasserstein** distance between two empirical measures
$\hat\mu_n$ and $\hat\nu_n$ on $\mathbb{R}$ is

$$
W_1(\hat\mu_n,\hat\nu_n) \;=\; \frac{1}{n}\sum_{i=1}^{n} \left| x_{(i)} - y_{(i)} \right|,
$$

where $x_{(i)}, y_{(i)}$ denote the order statistics.

```python
w_scipy = wasserstein_distance(x, y)
w_manual = np.mean(np.abs(np.sort(x) - np.sort(y)))

print(f"scipy : {w_scipy:.4f}")
print(f"manual: {w_manual:.4f}")
```

```text
scipy : 1.4937
manual: 1.4937
```

The two values match — the sorted-pairing formula recovers $W_1$ exactly.

## Visualizing the optimal transport plan

In 1D, the optimal transport plan is the *monotone rearrangement*: the smallest
$x$ is mapped to the smallest $y$, the second smallest to the second smallest,
and so on.

```python
fig, ax = plt.subplots(figsize=(7, 4))
xs, ys = np.sort(x), np.sort(y)
for xi, yi in zip(xs, ys):
    ax.plot([0, 1], [xi, yi], color="steelblue", alpha=0.25)
ax.scatter(np.zeros_like(xs), xs, s=12, color="black", label=r"$\mu$")
ax.scatter(np.ones_like(ys), ys, s=12, color="firebrick", label=r"$\nu$")
ax.set_xticks([0, 1]); ax.set_xticklabels(["source", "target"])
ax.set_title("Monotone OT plan (sorted pairing)")
ax.legend()
plt.tight_layout()
plt.show()
```

![Optimal transport plan](plot.svg)

## Takeaways

- In 1D, the Wasserstein distance is essentially **free** to compute — just sort.
- The optimal transport plan is the monotone rearrangement.
- In higher dimensions this trick no longer works and we need solvers; that's
  where the algorithms discussed on the [Research page](/research/) come in.

---

## Workflow for future posts

Recommended workflow for adding a new notebook-style post:

1. Write the post as a `.ipynb` in `content/blog/<your-post-slug>/`.
2. Convert it to Markdown next to the notebook. Either tool works:
   - `jupyter nbconvert --to markdown your_notebook.ipynb --output index`
   - `academic` (from
     [academic-file-converter](https://github.com/GetRD/academic-file-converter)):
     `academic import your_notebook.ipynb`
3. Add YAML front matter at the top of `index.md` with `title`, `date`,
   `summary`, `authors: [admin]`, and any `tags`.
4. Place referenced figures (e.g. `plot.svg`, `output_5_0.png`) next to
   `index.md` — they are picked up as page resources by Hugo.
5. Commit the `index.md` (the raw `.ipynb` is ignored by Hugo — see
   `ignoreFiles` in `config/_default/hugo.yaml`).

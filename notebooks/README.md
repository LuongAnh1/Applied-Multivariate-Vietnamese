# Jupyter notebooks

Run these notebooks from the repository root.

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m ipykernel install --user --name applied-multivariate-vietnamese --display-name "Applied Multivariate Vietnamese"
jupyter lab
```

The notebook for Exercise 5.4(b) rebuilds the Q-Q and scatter plots used in the
translated solution.

Included notebooks:

- `chapter5_exercise_5_4a.ipynb`: eigenvalues, normalized eigenvectors, and confidence ellipsoid axes.
- `chapter5_exercise_5_4b.ipynb`: Q-Q plotting positions, theoretical quantiles, and diagnostic plots.
- `chapter5_exercise_5_5.ipynb`: Hotelling's \(T^2\) test for the microwave radiation data.

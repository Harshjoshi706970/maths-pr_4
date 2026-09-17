 # Calculative Foundation: Linear Algebra & Matrix Analysis

## Project Documentation & Guide (`pr_4.ipynb`)
## 1. Executive Summary

This project implements fundamental and applied concepts of **Linear Algebra** on academic evaluation datasets using Python, **NumPy**, and **pandas**. By framing student score distributions across multiple subjects as vectors and matrices, the system explores vector norms, angular similarities, 3D cross products, orthogonal projections, matrix transformations, determinants, matrix inversions, and covariance eigendecomposition (spectral analysis).

## 2. Dataset Specification (`student_scores_200.csv`)

The dataset comprises score profiles for 200 individual students evaluated across 4 core academic disciplines.
### 2.1 Schema Overview

| Field Name | Type | Description |
| :--- | :--- | :--- |
| `Student_ID` | String | Unique identifier (`STU_001` through `STU_200`) |
| `First_Name` | String | First name of the student |
| `Last_Name` | String | Last name / surname |
| `Full_Name` | String | Concatenated full name |
| `Math` | Float / Int | Score achieved in Mathematics (0–100) |
| `Science` | Float / Int | Score achieved in Science (0–100) |
| `English` | Float / Int | Score achieved in English (0–100) |
| `History` | Float / Int | Score achieved in History (0–100) |
| `Total_Score` | Float / Int | Aggregate sum across all 4 subjects |
| `Average_Score` | Float | Arithmetic mean across all 4 subjects |
| `Grade` | String | Assigned letter grade (`A`, `B`, `C`, `D`, `Pass`) |
| `Status` | String | Academic result status (`Pass` / `Fail`) |


## 3. Module & Calculation Breakdown

### Task 1: Vector Representation
Each student's score across `["Math", "Science", "English", "History"]` forms a 4D row vector:
$$\mathbf{v}_i = [\text{Math}_i, \text{Science}_i, \text{English}_i, \text{History}_i] \in \mathbb{R}^4$$

### Task 2: Norms, Dot Product, Angle, and Cross Product
- **L1 Norm (Manhattan):** $\|\mathbf{v}\|_1 = \sum_{j=1}^4 |v_j|$ (identical to student total score).
- **L2 Norm (Euclidean):** $\|\mathbf{v}\|_2 = \sqrt{\sum_{j=1}^4 v_j^2}$.
- **Dot Product:** $\mathbf{u} \cdot \mathbf{w} = \sum_{j=1}^4 u_j w_j$.
- **Angle (Cosine Distance):** $\theta = \arccos\left(\frac{\mathbf{u} \cdot \mathbf{w}}{\|\mathbf{u}\|_2 \|\mathbf{w}\|_2}\right)$ in degrees.
- **Cross Product (3D Subspace):** Computed over `['Math', 'Science', 'English']`:
  $$\mathbf{a} \times \mathbf{b} = (a_2 b_3 - a_3 b_2)\mathbf{i} - (a_1 b_3 - a_3 b_1)\mathbf{j} + (a_1 b_2 - a_2 b_1)\mathbf{k}$$

### Task 3: Vector Projection
Orthogonal projection of vector $\mathbf{u}$ onto vector $\mathbf{w}$:
$$\text{proj}_{\mathbf{w}}(\mathbf{u}) = \left(\frac{\mathbf{u} \cdot \mathbf{w}}{\|\mathbf{w}\|_2^2}\right)\mathbf{w}$$

### Task 4: Matrix Operations
- **Matrix Formation:** $M \in \mathbb{R}^{200 \times 4}$.
- **Matrix Addition:** $M + M = 2M$.
- **Gram Matrix Multiplication:** $M \cdot M^T \in \mathbb{R}^{200 \times 200}$.
- **Transpose:** $M^T \in \mathbb{R}^{4 \times 200}$.
- **Submatrix Inversion & Determinant:** Using the $4 \times 4$ submatrix $M_{[0:4, :]}$:
  $$\det(M_{4\times 4}) \approx 79476.00 \neq 0 \implies M^{-1} \text{ exists}.$$

### Task 5: Spectral Decomposition (Eigenvalues & Eigenvectors)
The subject covariance matrix $\Sigma \in \mathbb{R}^{4 \times 4}$ is factored via eigendecomposition:
$$\Sigma \mathbf{e}_k = \lambda_k \mathbf{e}_k$$
yielding principal variance components and directions across the academic disciplines.

---

## 4. Setup, Installation & Execution Guide

### 4.1 Prerequisites
- Python 3.9+
- Jupyter Notebook / JupyterLab / VS Code / Google Colab
- Libraries: `numpy`, `pandas`

```bash
pip install numpy pandas notebook
```

### 4.2 Running the Project
1. Clone or place `pr_4.ipynb` and `student_scores_200.csv` in the same directory.
2. Launch Jupyter Notebook:
   ```bash
   jupyter notebook pr_4.ipynb
   ```
3. Execute cells sequentially. When prompted with interactive input requests (`input()`), input any valid student index between `0` and `199`.

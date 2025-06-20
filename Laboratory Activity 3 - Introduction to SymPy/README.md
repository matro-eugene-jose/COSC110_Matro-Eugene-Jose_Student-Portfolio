# Laboratory Activity 3: Introduction to SymPy

### 1. Introduction

This activity teaches the basics of symbolic computation in Python using the SymPy library. You will:

1. Import SymPy modules.
2. Perform exact symbolic calculations and obtain numeric approximations.
3. Define symbolic variables and form equations.
4. Simplify algebraic expressions.
5. Expand polynomial expressions.

---

### 2. Materials & Environment

* **Platform**: Google Colab or local Jupyter Notebook
* **Python version**: 3.x
* **Library**:

  * `sympy`

Before running, ensure SymPy is installed:

`
pip install sympy
`

---

### 3. Methods

#### 3.1 Task 1: Import SymPy Modules

**Goal**: Load core SymPy functions and classes so future Tasks can use symbols, equations, simplification, expansion, etc.
Code:

`
from sympy import *
`

Pseudocode:

* Import everything from the `sympy` package to access `symbols`, `Rational`, `sqrt`, `Eq`, `simplify`, `expand`, and other utilities .

#### 3.2 Task 2: Basic Calculation

**Goal**: Compute the following expressions exactly, then show numeric approximation.

* Expression A: 5/3 + √10 / 2
* Expression B: √50 × √(5/9)
  Code:

`
# Expression A
result1 = Rational(5, 3) + sqrt(10)/2
print(f"5/3 + sqrt(10)/2 = {result1}  (approx ≈ {result1.evalf()})")

# Expression B
result2 = sqrt(50) * sqrt(Rational(5, 9))
print(f"sqrt(50) * sqrt(5/9) = {result2}  (approx ≈ {result2.evalf()})")
`

Pseudocode:

* Define `Rational(5, 3)` for exact 5/3, add `sqrt(10)/2`; print symbolic result and `evalf()`.
* Define `sqrt(50) * sqrt(Rational(5, 9))`; print symbolic and numeric form .

#### 3.3 Task 3: Define Symbols & Form Equations

**Goal**: Create symbolic variables `x`, `y` and represent linear equations.

* Equations: 2x + 3y = 12, and x − y = 4.
  Code:

`
x, y = symbols('x y')
equation1 = Eq(2*x + 3*y, 12)
print("Equation1:", equation1)
equation2 = Eq(x - y, 4)
print("Equation2:", equation2)
`

Pseudocode:

* Call `symbols('x y')` to create symbolic variables `x`, `y`.
* Build `Eq(2*x + 3*y, 12)` and `Eq(x - y, 4)`, then display them .

#### 3.4 Task 4: Simplification

**Goal**: Simplify given rational expressions using SymPy’s `simplify`.

* Expression 1: (x² + 2x + 1) / (x + 1)
* Expression 2: (1 − 1/(1 + 1/x)) / (1 + 1/x)
  Code:

`
x = symbols('x')

expr1 = (x**2 + 2*x + 1) / (x + 1)
simplified_expr1 = simplify(expr1)
print(f"Simplified (x^2 + 2x + 1)/(x + 1) = {simplified_expr1}")

expr2 = (1 - 1/(1 + 1/x)) / (1 + 1/x)
simplified_expr2 = simplify(expr2)
print(f"Simplified (1 - 1/(1 + 1/x)) / (1 + 1/x) = {simplified_expr2}")
`

Pseudocode:

* Ensure `x` is declared as a symbol.
* Apply `simplify(...)` to each expression and print the simplified form .

#### 3.5 Task 5: Expansion

**Goal**: Expand polynomial expressions using SymPy’s `expand`.

* Expression A: (2x + 2)²
* Expression B: (2x + y)(x − 2y)
  Code:

`
x, y = symbols('x y')

exprA = (2*x + 2)**2
expandedA = expand(exprA)
print(f"Expanded (2x + 2)^2 = {expandedA}")

exprB = (2*x + y)*(x - 2*y)
expandedB = expand(exprB)
print(f"Expanded (2x + y)*(x - 2y) = {expandedB}")
`

Pseudocode:

* Declare symbols `x, y`.
* Use `expand(...)` on each expression; print the expanded polynomial .

---

### 4. Results & Outputs

After running each code cell in the notebook:

* **Task 1**: No errors; SymPy functions available.
* **Task 2**:

  * 5/3 + √10/2 prints as symbolic sum and numeric approximation.
  * √50 × √(5/9) simplifies symbolically (e.g., to √(250/9) or equivalent) and shows decimal.
* **Task 3**: Printed Eq objects `Eq(2*x + 3*y, 12)` and `Eq(x - y, 4)`.
* **Task 4**:

  * (x² + 2x + 1)/(x + 1) simplifies to x + 1.
  * Nested fraction simplifies to a simpler rational expression in x.
* **Task 5**:

  * (2x + 2)² expands to 4*x² + 8*x + 4.
  * (2x + y)*(x - 2y) expands to 2*x² - 3*x*y - 2\*y² (or equivalent ordering).

These outputs appear inline in the notebook cells and confirm correct use of SymPy methods .

---

### 5. Summary & Insights

*Symbolic vs. Numeric Computation*: Using `Rational` and symbolic `sqrt` preserves exactness until `evalf()` is called.
*Equation Representation*: `Eq()` encapsulates relations for later solving or analysis.
*Algebraic Transformations*:

* `simplify` reduces expressions automatically, illustrating algorithmic manipulation of symbolic forms.
* `expand` distributes and combines like terms, useful for polynomial handling.
  *Generalization*: The same patterns extend to solving equations, differentiation/integration, factoring, series expansions, etc.
  This structured approach reinforces computational thinking: break tasks into “what” (operation), “why” (benefit of symbolic form), and “how it generalizes” (applicability to broader symbolic problems).

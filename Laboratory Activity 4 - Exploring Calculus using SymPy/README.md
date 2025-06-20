 Laboratory Activity 4: Exploring Calculus with SymPy

### 1. Introduction

This activity demonstrates how to use SymPy for basic calculus operations: treating symbols algebraically, computing limits, derivatives, series expansions, and solving simple equations. You will run Python/SymPy code snippets and answer questions that probe your understanding of each concept. All Tasks correspond to cells in `lab4_exploring_calculus_sympy_Matro,Eugene_Jose.ipynb`, based on the provided lab instructions :contentReference[oaicite:0]{index=0}.

---

### 2. Materials & Environment

* **Platform**: Google Colab or local Jupyter Notebook  
* **Python**: 3.x  
* **Library**:  
  * `sympy`  

Ensure SymPy is installed before running:  
```
pip install sympy
```

---

### 3. Methods

#### 3.1 Playing with Symbols

**Goal**: Observe how SymPy represents and manipulates symbolic variables.

Code:

```
from sympy import symbols

x = symbols('x')
print(x + x)   # expected: 2*x
print(x * x)   # expected: x**2
```

Pseudocode:

```
Import symbols from sympy
Declare a symbolic variable x
Evaluate x + x  → prints 2*x
Evaluate x * x  → prints x**2
```

Questions:

1. What does `x + x` mean?
2. What does `x * x` represent?&#x20;

---

#### 3.2 Exploring Limits

**Goal**: Compute a limit of a symbolic expression as a variable approaches a point.

Code:

```
from sympy import symbols, sin, limit

x = symbols('x')
expr = sin(x) / x
lim_val = limit(expr, x, 0)
print("limit(sin(x)/x, x→0) =", lim_val)   # expected: 1
```

Pseudocode:

```
Import symbols, sin, limit from sympy
Declare x as symbol
Define expr = sin(x)/x
Compute limit(expr, x, 0)
Print the result
```

Question:

* What result do you get, and how do you interpret “as x approaches 0, sin(x)/x”?&#x20;

---

#### 3.3 Playing with Derivatives

**Goal**: Use SymPy to compute the derivative of a simple function.

Code:

```
from sympy import symbols, diff

x = symbols('x')
result = diff(x**2, x)
print("diff(x**2, x) =", result)   # expected: 2*x
```

Pseudocode:

```
Import symbols, diff from sympy
Declare symbol x
Call diff(x**2, x)
Print derivative 2*x
```

Question:

* What does the output tell you about the rate of change of x²?&#x20;

---

#### 3.4 Series Expansion

**Goal**: Generate the Taylor (Maclaurin) series of exp(x) around x=0 up to a given order.

Code:

```
from sympy import symbols, exp

x = symbols('x')
series_expansion = exp(x).series(x, 0, 4)
print("exp(x) series up to x^3:", series_expansion)
```

Pseudocode:

```
Import symbols, exp from sympy
Declare symbol x
Compute exp(x).series(x, 0, 4)  # terms up to x^3 plus O(x^4)
Print series: 1 + x + x^2/2! + x^3/3! + O(x^4)
```

Questions:

1. How many terms are shown?
2. What does the “O(x^4)” indicate?&#x20;

---

#### 3.5 Solving Equations

**Goal**: Solve a simple polynomial equation symbolically.

Code:

```
from sympy import symbols, Eq, solve

x = symbols('x')
solutions = solve(Eq(x**2 - 4, 0), x)
print("Solutions to x^2 - 4 = 0:", solutions)  # expected: [-2, 2]
```

Pseudocode:

```
Import symbols, Eq, solve from sympy
Declare symbol x
Construct Eq(x**2 - 4, 0)
Call solve(...) to get roots [-2, 2]
Print the solutions
```

Questions:

1. What are the solutions?
2. What type of problem is this?&#x20;

---

#### 3.6 Final Thoughts

**Goal**: Reflect on which parts of the activity you found most interesting or surprising.

In the notebook, you will write brief answers:

* Favorite part (e.g., series expansion unveiling the Taylor series pattern).
* Something new or surprising learned (e.g., how SymPy simplifies nested expressions automatically).&#x20;

---

### 4. Summary & Insights

* **Symbolic representation**: Declaring `x = symbols('x')` allows algebraic manipulation.
* **Limits**: `limit(sin(x)/x, x, 0)` returns 1, illustrating how SymPy handles analytic limits.
* **Derivatives**: `diff(x**2, x)` yields `2*x`, confirming the power rule.
* **Series**: `exp(x).series(x, 0, 4)` shows the first four terms and big-O notation for omitted higher terms.
* **Equation solving**: `solve(Eq(x**2 - 4, 0), x)` returns real roots \[-2, 2].
* **Reflection**: Highlights the power of symbolic computation for exploring calculus concepts without manual algebra.

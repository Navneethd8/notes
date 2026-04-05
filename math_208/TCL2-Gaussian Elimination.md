---
date: 2026-03-28
tags:
  - math208
  - linalg
  - carr
  - gaussian_elimination
title: Gaussian Elimination
---
Now that we know what an augmented matrix is and what it looks like, let's go deeper into
## Elementary Row Operations
There are 3 main operations that can be performed on matrices
1. Multiply any row by a non 0 constant.
2. Add/Subtract a multiple of any row from any other row.
3. Swap any two rows.
Our main goal is to end up with a matrix like this:
$$
\begin{pmatrix}
* & * & * & | & * \\
0 & * & * & | & * \\
0 & 0 & * & | & *
\end{pmatrix}
$$
```
Example 1. Eliminate the below matrix
```
$$
\begin{pmatrix}
1 & 0 & -3 & | & -2 \\
3 & 1 & -2 & | & 5 \\
2 & 2 & 1 & | & 4
\end{pmatrix}
$$
Lets start by performing two operations to eliminate $x_1$ in rows 2 and 3.
- $R_2 = R_2 - 3 \times R_1$ 
- $R_3 = R_3 - 2 \times R_1$
The resulting matrix you end up with is:
$$
\begin{pmatrix}
1 & 0 & -3 & | & -2 \\
0 & 1 & 7 & | & 11 \\
0 & 2 & 7 & | & 8
\end{pmatrix}
$$
Now in order to eliminate that $x_2$ in row 3, change $R_3$ to $R_3 - 2 \times R_2$
$$
\begin{pmatrix}
1 & 0 & -3 & | & -2 \\
0 & 1 & 7 & | & 11 \\
0 & 0 & -7 & | & -14
\end{pmatrix}
$$
This form has achieved that initial goal and is called **Echelon form** or **Row Echelon form**, and the process to reach here is called **Gaussian Elimination**.

In fact, we can keep on reducing the matrix as follows. Let's continue by simplifying the $R_3 = -\frac{1}{7} \times R_3$ and you end up with:
$$
\begin{pmatrix}
1 & 0 & -3 & | & -2 \\
0 & 1 & 7 & | & 11 \\
0 & 0 & 1 & | & 2
\end{pmatrix}
$$

Then, modify $R_2 = R_2 - 7 \times R_3$ 
$$
\begin{pmatrix}
1 & 0 & -3 & | & -2 \\
0 & 1 & 0 & | & -3 \\
0 & 0 & 1 & | & 2
\end{pmatrix}
$$
Finally, you modify $R_1$ to $R_1 = R_1 + 3 \times R_3$ 
$$
\begin{pmatrix}
1 & 0 & 0 & | & 4 \\
0 & 1 & 0 & | & -3 \\
0 & 0 & 1 & | & 2
\end{pmatrix}
$$
This resulting form is called the **Reduced Echelon Form**, and the process to get from row echelon form to reduced echelon form is called **Gauss-Jordan Elimination**.

The final solution set can be written as 
$$ (x_1,x_2,x_3) = (4,-3,2) $$
## How to tell if a solution is inconsistent
```
Example 2. Evaluate if the below system is inconsistent or not
```
$$
\begin{cases}
-3y + 6z = 2 \\
x + 4z = 1 \\
2x + y + 6z = 0
\end{cases}
$$
Let's write this as an adjacency matrix below:
$$
\begin{pmatrix}
0 & -3 & 6 & | & 2 \\
1 & 0 & 4 & | & 1 \\
2 & 1 & 6 & | & 0
\end{pmatrix}
$$
In order to make life easier, lets move $R_1$ and $R_2$ up one and $R_3$ to the bottom so that we have our top diagonal as 1.

$$
\begin{pmatrix}
1 & 0 & 4 & | & 1 \\
2 & 1 & 6 & | & 0 \\
0 & -3 & 6 & | & 2 
\end{pmatrix}
$$
$R_2 = R_2 - 2 \times R_1$

$$
\begin{pmatrix}
1 & 0 & 4 & | & 1 \\
0 & 1 & -2 & | & -2 \\
0 & -3 & 6 & | & 2 
\end{pmatrix}
$$
$R_3 = R_3 + 3 \times R_2$
$$
\begin{pmatrix}
1 & 0 & 4 & | & 1 \\
0 & 1 & -2 & | & -2 \\
0 & 0 & 0 & | & -4
\end{pmatrix}
$$
That last row tells us $0x + 0y + 0z = -4$ which does not make sense.

> [!tip] Inconsistent solutions
> If a matrix is reduced and you obtain a row of the form $\begin{pmatrix} 0 & 0 & 0 & ... & 0 & | & a  \end{pmatrix}$, when  $a \neq 0$, then the system is inconsistent


## Echelon Form

>[!tip] Definition: Row Echelon form
> A matrix is in row echelon form (staircase form) if:
> a) All 0 rows are at the bottom.
> b) The leading non 0 entry of each row (called the pivot), is strictly to the right of the leading non 0 entry of the row above.

### Are Echelon forms unique?
No they are not.
$$
\begin{pmatrix}
- & * & * & * & * & * & | * \\
0 & 0 & - & * & * & * & | * \\
0 & 0 & 0 & - & * & * & | * \\
0 & 0 & 0 & 0 & 0 & 0 & | 0 \\
\end{pmatrix}
$$
Here $-$ is any non 0 number and $*$ is any number. The variables associated with the pivot columns are called **leading variables**. The variables associated with the non pivot columns are called **free variables**.

Recall this example from the previous notes.
$$
\begin{cases}
2x_1 - x_2 + 5 x_3 - x_4 = -30 \\
x_3 + x_4 = -6
\end{cases}
$$
putting that in adjacency matrix form 
$$
\begin{pmatrix}
2 & -1 & 5 & -1 & | & -30 \\
0 & 0 & 1 & 1 & | & -6
\end{pmatrix}
$$
In the example above $x_1$ and $x_3$ are leading variables, and $x_2$ and $x_4$ are called free variables.


>[!tip] Definition: Reduced Row Echelon form
> A matrix is in reduced row echelon form (staircase form) if:
> a) It is in row echelon form
> b) All the pivots are '1's
> c) each pivot column has all 0s above it

```
Example 3. Take the below matrix in row echelon form and convert it to reduced row echelon form.
```
$$
\begin{pmatrix}
1 & -1 & 4 & -2 & 0 & | & 0 \\
0 & 0 & 2 & 0 & -4 & | & 2 \\
0 & 0 & 0 & 1 & 0 & | & 5 \\
0 & 0 & 0 & 0 & 0 & | & 0 \\
\end{pmatrix}
$$
Lets start with simplifying row 2. $R_2  = \frac{1}{2} \times R_2$
$$
\begin{pmatrix}
1 & -1 & 4 & -2 & 0 & | & 0 \\
0 & 0 & 1 & 0 & -2 & | & 1 \\
0 & 0 & 0 & 1 & 0 & | & 5 \\
0 & 0 & 0 & 0 & 0 & | & 0 \\
\end{pmatrix}
$$
$R_1 = R_1 + 2 \times R_3$
$$
\begin{pmatrix}
1 & -1 & 4 & 0 & 0 & | & 10 \\
0 & 0 & 1 & 0 & -2 & | & 1 \\
0 & 0 & 0 & 1 & 0 & | & 5 \\
0 & 0 & 0 & 0 & 0 & | & 0 \\
\end{pmatrix}
$$
$R_1 = R_1 - 4 \times R_2$
$$
\begin{pmatrix}
1 & -1 & 0 & 0 & 8 & | & 6 \\
0 & 0 & 1 & 0 & -2 & | & 1 \\
0 & 0 & 0 & 1 & 0 & | & 5 \\
0 & 0 & 0 & 0 & 0 & | & 0 \\
\end{pmatrix}
$$
This is now in reduced row echelon form. The system of equations that this augmented matrix gives is
$$
\begin{cases}
x_1 - x_2 + 8x_5 = 6 \\
x_3 - 2x_5 = 1 \\
x_4 = 5
\end{cases}
$$

Here the free variables are $x_2$ and $x_5$ and the leading variables are $x_1$, $x_3$ and $x_4$. In order to arrive at the final solution, you can parameterize the equations as follows.

Let $x_2$ = $s$ , $x_5$ = $t$
$x_1 - s + 8t = 6$
$x_1 = 6 -8t + s$

$x_3 - 2t = 1$
$x_3 = 1 + 2t$

The final solution is 
$$
\begin{gathered}
x_1 = 6 -8t + s \\
x_2 = s \\
x_3 = 1 + 2t \\
x_4 = 5 \\
x_5 = t \\
\end{gathered}
$$
``` 
Example 4. For what values of a and b does the below system have
a) One solution.
b) Infinitely many solutions.
c) No solutions.
```
$$
\begin{cases}
x + y + 2z = 4 \\
2x + 3y = a \\
-y + 4z = b
\end{cases}
$$
Lets start off by putting this in an augmented matrix:
$$
\begin{pmatrix}
1 & 1 & 2 & | & 4 \\
2 & 3 & 0 & | & a \\
0 & -1 & 4 & | & b \\
\end{pmatrix}
$$
$R_2 = R_2 - 2 \times R_1$
$$
\begin{pmatrix}
1 & 1 & 2 & | & 4 \\
0 & 1 & -4 & | & a - 8 \\
0 & -1 & 4 & | & b \\
\end{pmatrix}
$$

$R_3 = R_3 + R_2$

$$
\begin{pmatrix}
1 & 1 & 2 & | & 4 \\
0 & 1 & -4 & | & a - 8 \\
0 & 0 & 0 & | & a + b - 8 \\
\end{pmatrix}
$$

The solution is inconsistent if $a$ and $b$ are non 0 or if $a+b \neq 8$.

If $a+b = 8$, The matrix becomes

$$
\begin{pmatrix}
1 & 1 & 2 & | & 4 \\
0 & 1 & -4 & | & a - 8 \\
0 & 0 & 0 & | & 0 \\
\end{pmatrix}
$$
and $x_3$ becomes a free variable. Therefore there are infinitely many values of $x_3$ , and therefore infinite solutions to $a$ and $b$ .

As a result, the system will never have 1 solution.


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

In fact, we can keep on reducing the matrix as follows. Let's 
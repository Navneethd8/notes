---
title: Introduction to Linear Algebra
date: 2026-03-28
tags:
  - math208
  - linalg
  - carr
---
## What is Linear Algebra?
- Solving Systems of linear equations
- In general, the study of linear transformations of vector spaces

## Algebraic Representation

> 1. Solving Systems of Equations Through Simultaneous Addition/Subtraction

```
Example 1. Solve the System
	x - 2y = 4
	3x + y = 5
```

What I'm starting off with is multiplying the 1st equation by a multiple of the x variable of the second equation in order to eliminate the first variable.
$$
x - 2y = 4  => 3x-6y = 12
$$
The system of equations then becomes
$$
\begin{cases}
 3x + y = 5 \\
 3x - 6y = 12
\end{cases}
$$

You then subtract the second equation from the first to get
$$
\begin{cases}
3x + y = 5 \\
- 3x - (+) 6y = - 12
\end{cases}
$$
to get
$$
-7y = 7 => y = -1
$$
You can then substitute this back into the original system of equations to solve for x

$$
\begin{gathered}
x - 2y = 4 \\
x = 4 + 2y \\
x = 4 + 2 \times (-1)\\
x = 4 - 2 \\
x = 2 \\
\end{gathered}
$$
The **only and final solution** to this equation then becomes
$$(x,y) = (2,1) $$

```
Example 2. Infinitely Many Solutions
	-x + 2y = 2 (1)
	3x - 6y = -6 (2)
```

Using the same addition/subtraction method as above, you first multiply the eqn.(1) by 3
$$ -x + 2y = 2 => -3x + 6y = 6 $$
The System of equations then becomes
$$
\begin{cases}
-3x + 6y = 6 \\
 3x - 6y = 6
\end{cases}
$$
On adding the two equations to solve for y, you get
$$  0y = 0 $$
Which means that there are **infinitely many solutions**.

In order to get a solution to such equations you can *parameterize* the equation (Theres more about parameterization later on).
Lets assume $y = t$, or any number. That way:
$$
\begin{gathered}
-x + 2y = 2 \\
x = 2y - 2 \\
x = 2t - 2 \\
\end{gathered}
$$
Therefore the solution to this system of equations is 
$$ (x,y) = (2t - 2, t) $$
```
Example 3.No solutions
	2x - y = 4
	2x - y = 5

```
Lets just start with subtracting the two equations
$$
\begin{cases}
2x - y = 4 \\
 - 2x -(+) y  = -  5
\end{cases}
$$
You then end up with
$$ 0x - 0y = -1 $$
This system of equations has **no solutions**.

From these 3 examples we can end up with a set of guiding questions to approach problems: Given a set of equations:
- Are there any solutions to this set?
- If so, how many?
- How can we describe the solutions?
	- Algebraically
	- Geometrically

>[!tip] Definition: Consistent System
> A linear system is **consistent** if it has at least one solution, otherwise it is called **inconsistent**.

```
Example 4. 3 equations, 3 unknowns
	a + 0b - 3c = -2
	3a + b - 2c = 5
	2a + 2b + c = 4
```

Step 1. Lets start off by eliminating $a$ in the 2nd and 3rd equation by subtracting a multiple of the 1st equation.

Subtracting the 2nd from the multiple of the first
$$
\begin{gathered}
3a + b -2c = 5 \\
- 3a + 0b -(+) 9c =-(+)6 \\
= 0a + b + 7c = 11
\end{gathered}
$$
Subtracting the 3rd from the multiple of the first

$$
\begin{gathered}
2a + 2b + c = 4 \\
-2a + 0b -(+) 6c = -(+)4 \\
= 0a + 2b + 7c = -8
\end{gathered}
$$
This leaves the system at
$$
\begin{cases}
	a + 0b - 3c = -2 \\
	0a + b + 7c = 11 \\
	0a + 2b + 7c = -8
\end{cases}
$$
Step 2. Eliminate $b$ in the 3rd equation by subtracting a multiple of the second equation

$$
\begin{gathered}
	2b + 7c = 8 \\
	-2b +(-)14c = (-)22 \\
	-7c = -14
\end{gathered}
$$
This leaves the system at
$$
\begin{cases}
	a + 0b - 3c = -2 \\
	0a + b + 7c = 11 \\
	 -7c = -14
\end{cases}
$$
Note: The system at this point is called a ==triangular system==.

Step 3. Solve for all variables.

You can now take $c = 2$ from that last system
On substituting $c$ in equation 2
$$
\begin{gathered}
b + 7 \times 2 = 11 \\
b = 11 - 14
b = -3
\end{gathered}
$$
Then taking $b$ and $c$ to solve for $a$
$$
\begin{gathered}
a + 0 \times (-3) - 3 \times 2 = -2 \\
a - 6 = -2 \\
a = 4 \\
\end{gathered}
$$

Therefore the final solution to this system is
$$(a,b,c) = (4,-3,2)$$
## Geometric Representation

> 1. Geometrical representation of an equation $ax + by =c$ is a line in the 2D space

The solution to *system* of such equations is the intersections of the lines.
![[Pasted image 20260328200424.png]]Geometrical representation of a 2D system of equations [^1]

>2. Geometrical representation of $ax + by + cz = d$ is a plane in the 3D space

The solution to a *system* of such equations is the intersection of all the planes.
![[Pasted image 20260328200744.png|697]]
Geometrics representation fo a 3D system of equations [^1]

1. Intersection of 3 planes in 1 point.
2. Intersection of 3 planes at. 1line [Infinitely many solutions].
3. Parallel panes [no solution].
4. No solutions [no exact point where all 3 planes intersect].
5. Intersection of all 3 planes on each other [Infinitely many solutions that form a plane].
6. No solutions

>[!question] Question
> Suppose we have a system of 2 equations with 3 unknowns. Can such a system have exactly 1 solution?

The answer to this can be thought of from the perspective of 2 planes intersecting at 3 points which leads to the answer being **NO**.

## Parametric Representation

A parameter is an independent variable that acts as a substitute for the set of infinite solutions(In this situation).

```
Example 5. Find the solution to the given set of equations
	2a - b + 5c - d = -30
	0a + 0b + c + d = -6
```

Let's take $d = t$ in this scenario. This makes $c$
$$c = -6 -t$$
On substituting this into eqn 1.

$$
\begin{gathered}
	2a - b + 5(-6 - t - t = -30 \\
	2a - b - 6t - 30 = 30 \\
	2a - b - 6t = 0
\end{gathered}
$$

At this point, let's introduce another parameter $b = s$ so that we can solve for a in terms of s

$$
\begin{gathered}
2a - s - 6t = 0 \\
2a = s + 6t \\
a =\frac{1}{2}s + 3t
\end{gathered}
$$

Now the parametric solution to the solution with s and t as parameters can be represented as 

$$ (a,b,c,d) = (\frac{1}{2}s + 3t, s, -6 - t, t) $$
## Matrix Representation 

Let's try and take the same set of equations from Example 4 and try and solve them through matrices
$$
\begin{cases}
	a + 0b - 3c = -2 \\
	3a + b - 2c = 5 \\
	2a + 2b + c = 4
\end{cases}
$$
This system can be represented in a special matrix form called an **augmented matrix**.
$$
\begin{pmatrix}
1 & 0 & -3 & | & -2 \\
3 & 1 & -2 & | & 5 \\
2 & 2 & 1 & | & 4
\end{pmatrix}
$$
Let's start of by subtracting 3 times equation 1 from equation 2 and 2 times equation 3 from equation 2. The new matrix becomes

$$
\begin{pmatrix}
1 & 0 & -3 & | & -2 \\
0 & 1 & 7 & | & 11 \\
0 & 2 & 7 & | & 8
\end{pmatrix}
$$
Then Let's subtract 2 times the second row from the 3rd row.

$$
\begin{pmatrix}
1 & 0 & -3 & | & -2 \\
0 & 1 & 7 & | & 11 \\
0 & 0 & -7 & | & -14
\end{pmatrix}
$$
From this final matrix, you can then convert it back into equation form and solve for each of the variables. Refer back to example 4 for the exact solution.

[^1]: https://www.youtube.com/watch?v=4qimdBeqDRk&list=PLMod2FLe8bTMCJyUqoqlJEMHAXe06Hx6h



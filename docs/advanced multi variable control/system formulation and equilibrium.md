# System Formulation and Equilibrium 
## 1. System Formulation
The general continues time and time invarient systems have the following formulations:

$$
\dot{x}(t) = f(x(t), u(t)),
\left\{\begin{aligned}
&x(0) = x_0\\
&t_0 = 0
\end{aligned}\right.
$$

If the system $u(t) = 0$ for all the time, we called the system as autonomous system. The autonomous system have the following formulation:

$$
\dot{x}(t) = f(x(t))
$$

And if the system is a linear system, we can use a linear form to express this system:

$$
\dot{x}(t) = Ax(t) + Bu(t)
$$

## 2. Equilibrium
Give the defination of equilibrium of a system:
!!!note "Defination"
    Giving the equilibrium state $\bar x$, $\exists u = \bar u$, at $t \geq 0$, that makes $f(\bar x, \bar u) = 0$, such a point $(\bar x, \bar u)$ is called equibrium pair, and $\bar x$ is an isolated equilibrium.

For a general system, the system is equilibria if: $\exists \delta > 0$ that makes $\bar x$ is the only equilibrium contained in the region $B_\delta(\bar{x}) = \{x\in \mathbb{R}^n:||x-\bar{x}||\leq \delta\}$.

To find the equilibrium pairs, we can consider the following 2 conditions:

1. The system is a linear system,

    $$
    \begin{aligned}
    &u(t) = \bar u, t \geq 0\\
    &A\bar x + B\bar u = 0 \\
    \Rightarrow &A\bar x = -B \bar u
    \end{aligned}
    $$

    * if $det(A) \neq 0$, $\bar x = -A^{-1}B\bar u$
    * if $det(A) = 0$, depend on $\bar u$, $\bar x = 0$ or $\bar x = \infty$
  
    !!! abstract "Example"
        $$
        \begin{aligned}
        &\dot{x}(t) = \begin{bmatrix}
        0 & 1\\
        0 & 0
        \end{bmatrix}x(t) + \begin{bmatrix}
        0 \\ 1
        \end{bmatrix}u(t) \\
        &\Rightarrow \left\{\begin{aligned}
        \dot{x}_1(t) &= x_2(t)\\
        \dot{x}_2(t) &= u(t)\\
        \end{aligned}\right.
        \end{aligned}
        $$
        


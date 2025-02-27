## 5.1 Linear Quadratic Problem (LQ)
Considering a linear system: $\dot x = Ax + Bu$ is A.S. $\Leftrightarrow$ (is necessary and sufficient to (N&S) ) $\dot x = Ax$ is A.S. Thus, we can give the theorem:

A N&S condition for the A.S. of a linear system is :

* Given any $Q = Q^T \succ 0, \exists P = P^T \succ 0$, satisfying:

    $$
    A^TP + PA = -Q
    $$

To prove the sufficiency:

$$
\begin{aligned}
V(x) &= x^TPx \\
\dot V(x) &= \dot x^TPx + x^TP\dot x\\
&=x^TA^TPx + x^TPAx \\
&= x^T(A^TP + PA)x \\
&= -x^TQx
\end{aligned}
$$

$\bar x = 0$ is G.A.S.

!!!abstract "Example"
    $$
    \begin{aligned}
    \dot x_1 &= -x_2 \\
    \dot x_2 &= x_1 + (x_1^2 - 1)x_2
    \end{aligned}
    $$
    
    $\bar x = \begin{bmatrix} 0\\0 \end{bmatrix}$ is an equilibrium point, find the stability.

    $$
    \begin{aligned}
    A &= \begin{bmatrix} 0&-1\\1&-1 \end{bmatrix} \\
    & \Rightarrow x_A(\lambda) = \lambda^2 + \lambda + 1\\
    & \Rightarrow \lambda = \frac{-1 \pm \sqrt 3}{2}
    \end{aligned}
    $$
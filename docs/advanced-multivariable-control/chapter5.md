## 5.1 LQ Problem
Considering a linear system: $\dot x = Ax + Bu$ is A.S. $\Leftrightarrow$ (__is necessary and sufficient to__ (N&S) ) $\dot x = Ax$ is A.S. Thus, we can give the theorem:

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

!!! example
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
    & \Rightarrow \lambda = \frac{-1 \pm i\sqrt 3}{2}
    \end{aligned}
    $$

    The system is A.S. for $Q  = Q^T\succ 0$

    Let $A^TP+PA=-Q$, we can choose the value $Q = \mathbf I$, $P = \begin{bmatrix} P_{11} & P_{12} \\ P_{21} & P_{22}\end{bmatrix} = \begin{bmatrix} \frac32 & -\frac12 \\ -\frac12 & 1\end{bmatrix}$, the eigenvalue of $P$ is $\lambda = \frac54 \pm \frac{\sqrt 5}{4}$, $P \succ 0$. Let $V(x) = x^TPx$ is globally PD in $\bar x = 0$ and radially unbunded

    $$
    \dot V(x) = \dot x^TPx + x^TP\dot x
    $$

    !!! notes
        We consider the nonlinear and higher oder part of the system,

        $$
        \dot x = Ax + \underbrace{\varphi(x) - Ax}_{\Delta \varphi(x)}
        $$

        Where $\Delta \varphi(x)$ is the nonlinear and higher order part of the system, it should be $0$ near the linearization point,

        $$
        \lim_{||x||\to 0}\frac{\Delta \varphi(x)}{||x||} = 0
        $$

        Unless we will have,

        $$
        \begin{aligned}
        \dot V(x) &= x^T(A^TP + PA)x + \text{higher order terms} \\
        &= -x^TQx + \text{higher order terms}\\
        \end{aligned}
        $$

        $-x^TQx$ is ND but due to the effect of higher order terms, $\dot V(x)$ could be non ND.

    Back to our case,

    $$
    \begin{aligned}
    \dot V(x) &= -(x_1^2 + x_2^2) - x_1^3x_2 + 2x_1^2x_2^2
    \end{aligned}
    $$

    $- x_1^3x_2 + 2x_1^2x_2^2$ are higher order terms, the system is ND in $\bar x = 0$ but __not__ globally, $\bar x$ is A.S.

    To find the border of $V(x)$, we make some approximation:

    $$
    \begin{aligned}
    \dot V(x) &= -||x||^2 + x_1 x_1x_2 (-x_1 +2x_2) \\
    &\leq -||x||^2 + |x_1| |x_1x_2| |-x_1 +2x_2| \\
    \end{aligned}
    $$

    We can further approximate the Lyapunov function by using some approximation techniques,

    $$
    \begin{aligned}
    (|x_1|-|x_2|)^2 = x_1^2 +x_2^2 - 2|x_1||x_2| &\geq 0 \\
    \frac12 ||x||^2 &\geq |x_1x_2| \\
    \hfill \\
    |\begin{bmatrix} -1 \\ 2\end{bmatrix}^T x| &\leq \sqrt 5 ||x||
    \end{aligned}
    $$

    Now we can get 

    $$
    \dot V(x) \leq -||x||^2 + ||x|| \frac12 ||x||^2 \sqrt 5 ||x||  = -||x||^2 (1- \frac{\sqrt 5}{2}||x||^2)
    $$

    <figure markdown="span">
        ![](pics/chapter5/figure1.HEIC){ width="400" }
    </figure>
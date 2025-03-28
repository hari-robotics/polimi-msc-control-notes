## 1. Pole Placement (Pole Assignment) Method

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t) \\
\end{aligned}
$$

Assume that the state is measurable, given the control law:

$$
u(t) = -Kx(t) + \gamma(t)
$$

!!! bug 
    missing figure

$\dot x_e(t) = Ax_e(t) + Bu(t)$ can be the enlarged system description, $x_e = \begin{bmatrix} x \\ v \end{bmatrix}$

!!! bug
    missing figure
 
$u = -Kx_e = - \begin{bmatrix} K_x & K_v \end{bmatrix} \begin{bmatrix} x \\ v \end{bmatrix}$

Replace $u$ into $x$, we have:

$$
\begin{aligned}
\dot x(t) &= Ax(t) - BKx(t) + B\gamma(t) \\
&= (A-BK)x(t) + B\gamma(t)
\end{aligned}
$$

Our goal is to choose a suitable $K$ to set the eigen values of $A-BK$ in arbitraily selected positions.

An N&S condition for such a $K$ to exist is $(A,B)$ is reachable.

!!! info
    Proof (necessity):

    Assume that $(A,B)$ is not reachable

    $$
    \begin{aligned}
    \begin{bmatrix} \dot x_R \\ \dot x_{NR} \end{bmatrix} = 
    \begin{bmatrix} A_R&A_X \\ 0&A_{NR} \end{bmatrix}
    \begin{bmatrix} x_R \\ x_{NR} \end{bmatrix} + 
    \begin{bmatrix} B_R \\ 0 \end{bmatrix}u
    \end{aligned}
    $$

    And we can design the controller 
    $u = -\begin{bmatrix} K_R & K_{NR} \end{bmatrix} 
    \begin{bmatrix} x_R \\ x_{NR} \end{bmatrix}$
    , replace it to the system dynamics:

    $$
    \begin{aligned}
    \begin{bmatrix} \dot x_R \\ \dot x_{NR} \end{bmatrix} = 
    \begin{bmatrix} A_R-B_RK_R&A_X-B_RK_{NR} \\ 0&A_{NR} \end{bmatrix}
    \begin{bmatrix} x_R \\ x_{NR} \end{bmatrix}
    \end{aligned}
    $$

    And the eigenvalues of $A-BK$ are $\text{eig}(A_R-B_RK_R)\cup \text{eig}(A_X-B_RK_{NR})$

!!! info
    Proof (Sufficiency):

    $(A,B)$ is reachable, $m = 1$, $\exists T_{n\times n}$, that $\det(T) \neq 0$, such that $\tilde x = Tx$.

    $$
    \tilde A = TAT^{-1} = \begin{bmatrix} 0&1&0&\cdots&0\\ \vdots&0&\ddots&0&\vdots \\ 0&0&0&\ddots&0 \\ 0&0&\cdots&0&1\\ -a_0 & -a_1 & \cdots & &-a_{n-1}\end{bmatrix}
    $$

    $$
    p_A(\lambda) = p_{\tilde A}(\lambda) = \lambda^n + a_{n-1}\lambda^{n-1}+\dots+a_1\lambda + a_0
    $$

    $$
    \begin{aligned}
    \tilde B &= TB = \begin{bmatrix} 0 \\ \vdots \\ 0 \\ 1\end{bmatrix} \\
    u(t) &= -\tilde K \tilde x(t) + \gamma(t)
    \end{aligned}
    $$

    $$
    \tilde A - \tilde B \tilde K = \begin{bmatrix} 0&1&0&\dots&0\\ \end{bmatrix}
    $$

    $$
    \begin{aligned}
    p_{\tilde A - \tilde B \tilde K}(\lambda) &= p_{A-BK}(\lambda) = \lambda^n + (a_{n-1}+\tilde K_{n-1})\lambda^{n-1}+\dots+(a_1 + \tilde K_1)\lambda + (a_0 + \tilde K_0) \\
    p_n^*(\lambda) &= \Pi_{i=1}^n(\lambda - \lambda_i^*) = \lambda^n + \alpha_{n-1}\lambda^{n-1} + \dots + \alpha_0
    \end{aligned}
    $$

    * $\lambda_i^*$ is desired eigenvalues

    We determine the $\tilde K_i = \alpha_i - a_i$, $i=0,\dots,n-1$, and $K=\tilde K T$, in the MIMO case, where $m > 1$, if $(A, b_i)$ is reachable,

    $$
    \begin{aligned}
    u_j(t) &= 0, &\forall j \neq i \\
    u_i(t) &= -K_ix(t) + \gamma(t) &
    \end{aligned}
    $$

    Where $K=\begin{bmatrix} 0 & \cdots & K_i & \cdots & 0\end{bmatrix}^T$

    Steps:
    
    1. Compute $p^*(\lambda)$ based on the desired set of $n$ eigenvalues, $\lambda_i^*$, $i=1,\dots,n$
    2. Compute $p_A(\lambda)$
    3. Build $\tilde A$, $\tilde B$ in controllable canonical form
    4. Determine the $M_R$ and $\tilde M_R$ $\Rightarrow$ $T = \tilde M_R M_R^{-1}$, where:

        $$
        \begin{aligned}
        M_R &= \begin{bmatrix} B&AB&\cdots&A_{n-1}B\end{bmatrix} \\
        \tilde M_R &= \begin{bmatrix} \tilde B&\tilde A\tilde B&\cdots&\tilde A_{n-1}\tilde B\end{bmatrix} = TM_R\\
        \end{aligned}
        $$

        Where $\tilde A = TAT^{-1}$, and $\tilde B = TB$
    
    5. $\tilde K = \begin{bmatrix} \alpha_0-a_0\cdots \alpha_{n-1}-a_{n-1}\end{bmatrix}$
    6. $K=\tilde KT$

    We give Ackermann's Formula:

    $K = \begin{bmatrix} 0&\cdots&0&1\end{bmatrix}M_R p^*(A)$

    where:

    * $p^*(\lambda) = \lambda^n + \alpha_{n-1}\lambda^{n-1} + \dots + \alpha_0$
    * $p^*(A) = A^n + \alpha_{n-1}A^{n-1} + \dots + \alpha_0I$

    !!! example
        $$
        \begin{aligned}
        &A = \begin{bmatrix} -1&3\\0&2 \end{bmatrix}
        &B = \begin{bmatrix} 1\\2 \end{bmatrix} \\
        &\lambda_1^* = -3 & \lambda_2^* = -4
        \end{aligned}
        $$

        $p^*(\lambda) = (\lambda + 3)(\lambda + 4) = \lambda^2 + 7\lambda + 12$

        And $M_R = \begin{bmatrix} 1&5\\2&4 \end{bmatrix}$, $(A,B)$ is reachable,

        $K = \begin{bmatrix} 0\\1 \end{bmatrix}
        \begin{bmatrix}-\frac46 &\frac56 \\ \frac26 &-\frac16 \end{bmatrix}
        (A^2+7A+12I)=\begin{bmatrix} 2&3 \end{bmatrix}$

        $$
        \begin{aligned}
        p_{A-BK}(\lambda) &= \det(\lambda I_2 - (A-BK)) \\
        &= \lambda^2 + (-1+K_1 + 2K_2)\lambda + 4K_1 + 2K_2 - 2 \\
        p^*(\lambda) &= \lambda^2 + 7\lambda + 12 \\
        \left\{\begin{aligned}
        -1 + K_1 + 2K_2 = 7 \\
        4K_1 + 2K_2 - 2 = 12
        \end{aligned}\right. \rightarrow 
        \left\{\begin{aligned}
        K_1=2 \\
        K_2=3
        \end{aligned}\right.
        \end{aligned}
        $$

!!! bug 
    missing figure
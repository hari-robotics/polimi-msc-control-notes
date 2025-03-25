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
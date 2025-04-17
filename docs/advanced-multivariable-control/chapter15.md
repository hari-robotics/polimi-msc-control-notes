## 1. LQR infinity horizon control

Given linear system,

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t), &x(0) = x_0
\end{aligned}
$$

The LQR cost function could be defined:

$$
J(x_0, u, 0) = \int_0^\infty(x^T(\tau)Qx(\tau) + u^T(\tau)Ru(\tau))d\tau
$$

* $Q = Q^T = C_q^TC_q \succeq 0$
* $R = R^T \succ 0$

It should satisfy the condition: 

* $(A, C_q)$ is observable
* $(A, B)$ is reachable

The optimal $LQ_\infty$ Control law is:

$$
\bar K = R^{-1}B^T\bar P
$$

And the Riccati equation is:

$$
\begin{aligned}
\bar PA + A^T\bar P + Q - \bar PBR^{-1}B^T\bar P &= 0 \\
\bar PA + A^T\bar P + Q - \bar K^TR\bar K &= 0
\end{aligned}
$$

The closed loop system have:

$$
\dot x = (A-B\bar K)x(t)
$$

is A.S.

!!! example
    $$
    \dot x(t) = ax(t) + b_1u_1(t) + b_2u_2(t)
    $$

    $$
    \begin{aligned}
    A &= a, 
    &B = \begin{bmatrix} b_1 & b_2 \end{bmatrix}
    \end{aligned}
    $$

    We can define the weights:

    $$
    \begin{aligned}
    Q = q, 
    &&R^{-1} = \begin{bmatrix} \rho_1&0 \\ 0&\rho_2 \end{bmatrix},
    &&R = \begin{bmatrix} \frac{1}{\rho_1}&0 \\ 0&\frac{1}{\rho_2} \end{bmatrix}
    \end{aligned}
    $$

    * $\rho_1 > 0$, $\rho_2 > 0$
    * $C_q = \sqrt{q}$

    The Riccati Equation are:

    $$
    2\bar pa + q - \bar p^2(b_1^2\rho_1 + b_2^2\rho_2) = 0
    $$

    And given:

    * $a = 0$, $b_1 = b_2 = 1$

    We can solve the Riccati Equation:

    * $\bar p = \sqrt{\frac{q}{\rho_1 + \rho_2}}$
    * $\bar K = 
    \begin{bmatrix} \rho_1&0 \\ 0&\rho_2 \end{bmatrix}
    \begin{bmatrix} 1&1 \end{bmatrix}^T
    \sqrt{\frac{q}{\rho_1 + \rho_2}} =
    \begin{bmatrix} k_1 \\ k_2 \end{bmatrix} = 
    \begin{bmatrix} \sqrt{\frac{\rho_1^2q}{\rho_1 + \rho_2}} \\ \sqrt{\frac{\rho_2^2q}{\rho_1 + \rho_2}} \end{bmatrix}$

!!! example 2
    $$
    \dot x(t) = ax(t) + u(t)
    $$

    $$
    \begin{aligned}
    A &= a, &B = 1
    \end{aligned}
    $$

    We can choose the weight:
    
    * $Q = 1$, $R = r$

    The Riccati Equation:

    $$
    \begin{aligned}
    2a\bar p + 1 - \frac{\bar p^2}{r} &= 0 \\
    \bar p^2 - 2ar\bar p - r &= 0 \\ \hfill \\
    \bar p = ar + \sqrt{(ar)^2 + r}
    \end{aligned}
    $$

    * $\bar k = \frac{ar + \sqrt{(ar)^2 + r}}{r} = a + \sqrt{a^2 + \frac{1}{r}}$

    The closed loop system is:

    $$
    \dot x(t) = -\sqrt{a^2 + \frac{1}{r}}x(t)
    $$

    When $r \to \infty$,

    $$
    \dot x(t) = -|a|x(t)
    $$

    is A.S.

    When $r \to 0$,

    $$
    \dot x(t) = -\alpha x(t)
    $$

    * $\alpha = \sqrt{a^2 + \frac{1}{r}} \to \infty$

    And the complementary sensitive function is:

    $$
    L(s) = \bar k G(s) = \frac{a + \sqrt{a^2 + \frac{1}{r}}}{s-a}
    $$

    At the crossing frequency: $|L(j\omega_c)| = 1$
    
    $$
    |\frac{a + \sqrt{a^2 + \frac{1}{r}}}{j\omega_c - a}| = \frac{a + \sqrt{a^2 + \frac{1}{r}}}{\sqrt{a^2 + \omega_c^2}} = 1
    $$


!!! example
    Constrain the speed of converging: $\tilde A = A + \alpha I$

    Given the system

    $$
    \dot x(t) = x(t) + u(t)
    $$

    $$
    A = B = 1
    $$

    * $\tilde A = 1 + \alpha$

    The Riccati Equation:

    $$
    \bar P \tilde A + \tilde A^T P + Q - \bar PBR^{-1}B^T\bar P = 0
    $$

    * $Q = q > 0$
    * $R = r > 0$

    $$
    2\bar p(1+\alpha) + q - \frac{\bar p^2}{r} = 0
    $$

    * $\bar p = \frac{1+\alpha + \sqrt{(1+\alpha)^2 + q/r}}{1/r}$
    * $\bar k_\alpha = 1+\alpha + \sqrt{(1+\alpha)^2 + q/r}$
    
    $$
    A - B\bar k_\alpha = 1 - \bar k_\alpha = -\alpha - \sqrt{(1+\alpha)^2 + q/r} < -\alpha
    $$

!!!example
    $$
    \left\{\begin{aligned}
    &\dot x_1(t) = bu(t) \\
    &x_2(t) = x_1(t) + u(t)
    \end{aligned}\right.
    $$

    $$
    \begin{aligned}
    A = \begin{bmatrix} 0&0 \\ 1&0 \end{bmatrix}
    &&B = \begin{bmatrix} b \\ 1 \end{bmatrix}
    \end{aligned}
    $$

    * $Q = \begin{bmatrix} q_1&0 \\ 0&q_2 \end{bmatrix}$, $q_1 \geq 0$, $q_2 \geq 0$
    * $R = 1$

    We need $(A, B)$ is reachable and $(A, C_q)$ is observable, $Q = C_q^TC_q$: 

    $$
    M_R = 
    \begin{bmatrix} B&AB \end{bmatrix} = 
    \begin{bmatrix} b&0 \\ 1&b \end{bmatrix}
    $$

    The system is reachable,

    $$
    C_q = Q^\frac12 = \begin{bmatrix} \sqrt{q_1}&0 \\ 0&\sqrt{q_2} \end{bmatrix}
    $$

    $$
    M_O = 
    \begin{bmatrix} C_q \\ C_qA \end{bmatrix} = 
    \begin{bmatrix} \sqrt{q_1}&0 \\ 0&\sqrt{q_2} \\ 0&0 \\ \sqrt{q_2}&0 \end{bmatrix}
    $$

    To make the system observable, $q_2 \neq 0$,

    $$
    \tilde y(t) = C_qx(t) = 
    \begin{bmatrix} \sqrt{q_1}x_1(t) \\ \sqrt{q_2}x_2(t) \end{bmatrix} 
    $$

    We can set $Q = I$, and $b = 1$, $\Rightarrow$ $\bar P = I$, check the stability of the closed loop system

    $$
    \dot x(t) = (A-B\bar K)x(t)
    $$

    1. by computing the eigenvalue of $(A-B\bar K)$
    2. by using a suitable Lyapunov Function

    ---
    * $\bar K = \begin{bmatrix} 1&1 \end{bmatrix}$
    
    $$
    A-B\bar K = \begin{bmatrix} 0&0\\1&0 \end{bmatrix} 
    \begin{bmatrix} 1\\1 \end{bmatrix} 
    \begin{bmatrix} 1&1 \end{bmatrix} = 
    \begin{bmatrix} -1&-1\\0&-1 \end{bmatrix}  
    $$

    * $\lambda_1 = \lambda_2 = -1$

    ---
    
    $$
    \begin{aligned}
    V(x) &= J^\circ(x) = x^T\bar P x = x^Tx \\
    \dot V(x) &= \dot x^T x + x^T\dot x \\
    &= x^T(A-B\bar K)^Tx + x^T(A-B\bar K)x \\
    &= -x^T 
    \begin{bmatrix} 2&1\\1&2 \end{bmatrix}
    x
    \end{aligned}
    $$

    $$
    \det(\lambda I - \begin{bmatrix} 2&1\\1&2 \end{bmatrix}) = 
    \det\begin{bmatrix} \lambda-2&-1\\-1&\lambda-2 \end{bmatrix} = 
    \lambda^2 - 4\lambda + 3
    $$

    * $\lambda_1 = 1$, $\lambda_2 = 3$

!!! example
    $$
    u(t) = -\rho \bar K x(t)
    $$

    We can get the new closed loop function:

    $$
    \tilde A_\rho = A-\rho B\bar K = \begin{bmatrix} -\rho&-\rho\\1-\rho&-\rho \end{bmatrix}
    $$

    $$
    \det(\lambda I - \tilde A_\rho) = \lambda^2 + 2\rho\lambda + \rho
    $$
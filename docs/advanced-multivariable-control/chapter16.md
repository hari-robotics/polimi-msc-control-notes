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

## 2. Kalman Filter

The reference system gives:

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t) + v_x(t) \\
y(t) &= Cx(t) + v_y(t)
\end{aligned}
$$

* $v_x(t)$, $v_y(t)$ is defined as gaussian noise, $v(t) = \begin{bmatrix} v_x(t) \\ v_y(t) \end{bmatrix} \sim \mathcal{G}(0, V)$, $E(v_x(t)) = E(v_y(t)) = 0$

$$
\begin{aligned}
E(V(t_1)V(t_2)^T) = V\delta(t_2 - t_1)
\end{aligned}
$$

* $V$ is the covariance matrix, $V = \begin{bmatrix} \tilde Q & z \\ z^T & \tilde R \end{bmatrix}$, where $\tilde Q \succeq 0$, $\tilde R \succ 0$
* $\delta(\tau) = \left\{\begin{aligned} &0, &\tau \neq 0 \\ &1, &\tau = 0\end{aligned}\right.$

For the initial condition, there have:

$$
\begin{aligned}
&x(0) \sim \mathcal{G}(\bar x, \tilde P) \\
&E((x(0) - \bar x_0)v(t)^T) = 0
\end{aligned}
$$

### 2.1 Covariance Matrix is independent
Assume $z = 0$,

$$
\begin{aligned}
\dot{\hat x}(t) &= A\hat x + Bu(t) + L(t)(y(t) - C\hat x(t)) \\
e(t) &= x(t) - \hat x(t) \\ \hfill \\
\dot e(t) &= Ae(t) + v_x(t) + L(t)(Ce(t) + v_y(t)) \\
&= (A - L(t)C)e(t) + B_c(t)v(t) \\ \hfill \\
\dot{\bar e}(t) &= (A - L(t)C)e(t)
\end{aligned}
$$

* $B_c(t) = \begin{bmatrix} I & -L(t) \end{bmatrix}$
* $\bar e(t) = E(e(t))$, at initial state, $e(0) = x(0) - \hat x(0) = x(0) - \bar x(0)$, $\bar e(0) = 0$, thus there have, $\bar e(t) = 0$, $\forall t \geq 0$

For the variance $e(t)$, 

$$
\tilde P(t) = E(e(t) e(t)^T)
$$

* $\tilde P(t)$ is symmetric and $\tilde P(t) \succeq 0$, $\tilde P(0) = \tilde P_0$

Our optimization target is:

$$
\begin{aligned}
&\min_{L(t)} &\gamma^T \tilde P(t) \gamma
\end{aligned}
$$

* $\gamma$ is a generic vector in $\Re^n$

$$
\begin{aligned}
\dot{\tilde P}(t) &= A\tilde P(t) + \tilde P(t)A^T + \tilde Q - \tilde P(t) C^T \tilde R^{-1}C \tilde P(t) \\
\tilde P(0) &= \tilde P_0 \\
L(t) &= \tilde P(t) C^T \tilde R^{-1} \rightarrow L(t)^T = \tilde R^{-1}C\tilde P(t)
\end{aligned}
$$
!!!info
    We go back to look at the LQ controller design:

    $$
    \begin{aligned}
    &\min_{K(t)} &x^T P(t) x
    \end{aligned}
    $$

    $$
    \begin{aligned}
    -\dot P(t) &= AP(t) + P(t)A^T + Q - P(t)C^TR^{-1}CP(t) \\
    P(T) &= S \\
    K(t) &= R^{-1}B^TP(t) \\
    P'(\tau) &= P(T-\tau) \leftarrow \dot P'(\tau) = -\dot P(T-\tau)
    \end{aligned}
    $$

The duality of LQ controller and Kalman Filter is:

|KF|LQR|
|---|---|
|$C$|$B^T$|
|$A$|$A^T$|
|$\tilde Q = B_qB_q^T$|$Q = C_q^TC_q$|
|$\tilde R$|$R$|
|$L$|$K^T$|
|$\tilde P(t)$|$P(T-t)$|

For the LQR design, 

* $(A, B)$ should be reachable
* $(A, C_q)$ should be observable

Similarly, we can derive the condition for Kalman Filter:

* $(A, C)$ should be observable $\Leftrightarrow$ $(A^T, C^T)$ should be reachable
* $(A, B_q)$ should be reachable $\Leftrightarrow$ $(A^T, B_q^T)$ should be observable

If $(A, C)$ is observable and $(A, B_q)$ is reachable, $\tilde Q = B_qB_q^T$, then, the optimal steady state observer is:

$$
\begin{aligned}
\dot{\hat x}(t) &= A\hat x(t) + Bu(t) + L(y(t) - C\hat x(t)) \\
&= (A-LC) \hat x(t) + Bu(t) + Ly(t)
\end{aligned}
$$

With $L = \bar{\tilde P}C^T R^{-1}$,

Where $\bar{\tilde P}$ is the unique (symmetric) positive definite solution to the stationary Riccati equation, 

$$
\begin{aligned}
A\bar{\tilde P} + \bar{\tilde P}A^T + \tilde Q - \bar{\tilde P}C^TR^{-1}C\bar{\tilde P} = 0
\end{aligned}
$$

The observer is A.S. ($A-LC$ has all eigenvalues with negative real part)

### 2.2 Covariance Matrix is non-independent
Assume $z \neq 0$,

$$
V = \begin{bmatrix} \tilde Q & z \\ z^T & \tilde R \end{bmatrix}
$$

The state space equation becomes:

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t) + v_x(t) + z\tilde R^{-1}(y(t) - (Cx(t) + v_y(t))) \\
&= (A-z\tilde R^{-1}C)x(t) + Bu(t) + z\tilde R^{-1}y(t) + v_x(t) - z\tilde R^{-1}v_y(t)
\end{aligned}
$$

The Kalman Filter equation becomes:

$$
\begin{aligned}
\dot{\hat x}(t) &= \tilde A\hat x(t) + Bu(t) + z\tilde R^{-1}y(t) + L(y(t) - C\hat x(t)) \\
\end{aligned}
$$

* $E(v_x(t)) = 0$, $E(v_x(t)v_x(t)^T) = \tilde Q$
* $v(t) = \begin{bmatrix} v_x(t) \\ v_y(t) \end{bmatrix} \sim \mathcal{G}(0, V)$
* $E(\tilde v_x(t)) = 0$, 

$$
\begin{aligned}
E(\tilde v_x(t)\tilde v_x(t)^T) &= E((v_x(t)z\tilde R^{-1}v_y(t))(v_x(t)z\tilde R^{-1}v_y(t))^T) \\
&= E(v_x(t)v_x(t)^T) + z\tilde R^{-1} E(v_x(t)v_y(t)^T)\tilde R^{-1}z^T - z\tilde R^{-1} E(v_y(t)v_x(t)^T) - E(v_x(t)v_y(t)^T)\tilde R^{-1}z^T \\
&= \tilde Q - z\tilde R^{-1}z^T \succeq 0
\end{aligned}
$$

Now we have:

$$
\begin{aligned}
\tilde v &= \begin{bmatrix} \tilde v_x(t) \\ \tilde v_y(t) \end{bmatrix} &
V &= \begin{bmatrix} \tilde Q - z\tilde R^{-1}z^T & 0 \\ 0 & \tilde R \end{bmatrix}
\end{aligned}
$$

Thus we can define $\tilde z$, 

$$
\begin{aligned}
\tilde z &= E(\tilde v_x(t) \tilde v_y(t)^T) \\
&= E((v_x(t) - z\tilde R^{-1}v_y^T)v_t(t)^T) \\
&= \underbrace{E(v_x(t)v_y(t)^T)}_{z} - z\tilde R^{-1}\underbrace{E(v_y(t)v_y(t)^T)}_{\tilde R} = 0
\end{aligned}
$$

!!! example
    Estimation of a constant

    $$
    \begin{aligned}
    &\dot x(t) = 0 &&x(0) = \bar x \\
    &y(t) = x(t) + v_y(t) &&v_y = \mathcal G(0,r)
    \end{aligned}
    $$

    We can find the state space matrices: $A = 0$, $B = 0$, $\dot Q = 0$, $C = 1$, $\tilde R = r$.

    * $(A,C)$ is observable
    * $(A,B_q)$ is not reachable

    $$
    \begin{aligned}
    \dot{\hat x} &= L(t)(y(t) - \hat x(t)) \\
    \dot{\tilde P}(t) &= -\frac{\tilde P(t)^2}{r} &\tilde P(0) = 0 \\
    \tilde P(t) &= \frac{1}{r^{-1}t + \frac{1}{\tilde P}_0} &t\geq0 \\
    L(t) &= \frac{r^{-1}}{r^{-1}t + \frac{1}{\tilde P}_0}
    \end{aligned}
    $$

!!! example
    $$
    \begin{aligned}
    \dot x(t) &= Ax(t) + N_x(t) \\
    y(t) &= N_y(t)
    \end{aligned}
    $$

    Here, $C = 0$, $L(t) = 0$

    * $(A,C)$ is not observable

!!! example
    __Brownian Motion__

    $$
    \begin{aligned}
    \dot x(t) &= v_x(t) &&v_x = \mathcal G(0,\tilde Q) &&\tilde Q > 0\\
    y(t) &= Cx(t) + v_y(t) &&v_y = \mathcal G(0,\tilde R) &&\tilde R > 0\\
    \end{aligned}
    $$

    Here, $C>0$, $A=0$, $B=0$, $B_q = \sqrt{\tilde Q} > 0$

    * $(A,C)$ is observable
    * $(A,B_q)$ is reachable

    $$
    \begin{aligned}
    &\tilde Q - \frac{\tilde P^2 C^2}{\tilde R} = 0 \\
    &\bar{\tilde P} = \sqrt{\frac{\tilde P^2 \tilde R}{C^2}} \\
    &\bar L = \bar{\tilde P}C\tilde R^{-1} = \sqrt{\frac{\tilde Q}{\tilde R}} \\
    &\dot{\hat x} = \bar L(y(t)-C\hat x(t)) \\
    &\dot{\hat x} = -\sqrt{\frac{\tilde Q}{\tilde R}}C\hat x(t) + \sqrt{\frac{\tilde Q}{\tilde R}}y(t) \\
    \end{aligned}
    $$

    We assume $\tilde Q$ and $\tilde R$ and $C$ to be 1

    $$
    \dot{\hat x} = -\hat x(t) + y(t) \\
    $$

    Now assume $\tilde R = \begin{bmatrix} \sigma_1^2 & 0 \\ 0 & \sigma_2^2 \end{bmatrix} = I$, $C = \begin{bmatrix} 1\\1 \end{bmatrix}$,

    $$
    \begin{aligned}
    \bar{\tilde P} &= \sqrt{\frac12} \\
    \bar L &= \sqrt{\frac12} \begin{bmatrix} 1&1 \end{bmatrix} \\
    \dot{\hat x} &= \sqrt{\frac12} (y_1 + y_2 - 2\hat x)
    \end{aligned}
    $$

!!! example
    $$
    \begin{aligned}
    &\dot x = -ax + bu + v && \dot v = \gamma v + \delta v_x && v_x = \mathcal G(0,\tilde q^2)\\
    &y = x + v_y && v_y = \mathcal G(0,\tilde R) && \tilde R > 0\\
    \end{aligned}
    $$

    We can define the enlarged system with the noise:

    $$
    \begin{aligned}
    \begin{bmatrix} \dot x \\ \dot v \end{bmatrix} &=
    \begin{bmatrix} -a&1 \\ 0&-\gamma \end{bmatrix}
    \begin{bmatrix} x\\v \end{bmatrix} + 
    \begin{bmatrix} b\\0 \end{bmatrix}u + 
    \begin{bmatrix} 0\\ \gamma \end{bmatrix}v_x \\
    y &= \begin{bmatrix} 1&0 \end{bmatrix}\begin{bmatrix} x\\v \end{bmatrix} + v_y
    \end{aligned}
    $$

    Where, $\tilde v_x = \mathcal G(0,\tilde Q)$, $\tilde Q = E\begin{bmatrix} \tilde v_x & \tilde v_x^T \end{bmatrix} = Mq^2M^T = q^2\begin{bmatrix} 0&0\\ 0&\delta^2 \end{bmatrix}$

    $$
    M_o = \begin{bmatrix} 1&0\\ -Q&1 \end{bmatrix}
    $$

    $(A,C)$ is observable

    $$
    \begin{aligned}
    \tilde Q &= B_q B_q^T = \tilde q M \tilde q M^T \\ 
    B_q &= \begin{bmatrix} 0\\ \delta \tilde q \end{bmatrix} \\ 
    M_r &= \begin{bmatrix} 0 & \delta \tilde q  \\ \delta \tilde q & -\gamma \delta \tilde q\end{bmatrix}
    \end{aligned}
    $$

    $(A,B_q)$ is reachable

    $$
    \begin{aligned}
    \begin{bmatrix} \hat{\dot x} \\ \hat{\dot v} \end{bmatrix} &= 
    A \begin{bmatrix} \hat{x} \\ \hat{v} \end{bmatrix} + Bu + \bar L(y - C
    \begin{bmatrix} \hat{x} \\ \hat{v} \end{bmatrix}) \\
    \hat{\dot x} &= -a\hat{x} + \hat{v} + bu + \bar l_1(y - \hat x) \\
    \hat{\dot v} &= -\gamma\hat{v} + \bar l_2(y - \hat x)
    \end{aligned}
    $$

    Consider $a=1$, $\tilde R = 1$, $\delta = \gamma > 0$, $\tilde q = 1$

    * $\gamma = 0.1$ $\rightarrow$ slow
    * $\gamma = 10$ $\rightarrow$ fast

    We look at the TF of $y\rightarrow x$,

    $$
    C(sI - (A-\bar LC))^{-1} \bar L
    $$

!!! example
    When the noise is not a gaussian noise:

    $$
    \dot x = Ax + Bu + v
    $$

    we can use spectral factorization

    $v$ is stationary
    
    $$
    \Phi_v(s) = \int_{-\infty}^{+\infty}c_v(\tau)e^{-s\tau}d\tau
    $$

## 3. LQG Control

$$
\begin{aligned}
\dot x(t) = Ax(t) + Bu(t) + v_x(t) \\
y(t) = Cx(t) + v_y(t)
\end{aligned}
$$

Same assumption as for kalman filter on $v_x(t)$, $v_y(t)$, $x(0)$.

The loss function is:

$$
J = \lim_{T\to \infty}\frac{1}{T}E[\int_0^T(x(t)^TQx(t) + u(t)^TRu(t)dt)]
$$

In the long run, if the system is A.S., the loss function becomes:

$$
J = E[(x_\infty(t)^TQx_\infty(t) + u_\infty(t)^TRu_\infty(t)dt)]
$$

The solution is:
if $(A,B)$ is reachable, and $(A,C_q)$ is observable ($(A,C)$ is observable, and $(A,B_q)$ is reachable)

* $R \succ 0$, $\tilde R \succ 0$
* $u(t) = -\bar K \hat x(t)$
* $\dot{\hat x}(t) = A\hat x(t) + Bu(t) + \bar L(y(t)-C\hat x(t))$

It combined LQ controller and Kalman filter together, we can find the transfer function of $y \to u$.

$$
\begin{aligned}
\dot{\hat x}(t) &= \underbrace{(A-B\bar K - \bar LC)}_{\tilde A} \hat x + \underbrace{\bar L}_{\tilde B} y(t) \\
u(t) &= \underbrace{-K}_{\tilde C}\hat x(t) \\
R(s) &= \bar K(sI - (A-B\bar K - \bar LC))^{-1}\bar L
\end{aligned}
$$
## 1. State Observer
Given a linear MIMO system,

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t) \\
y(t) &= Cx(t) + Du(t)
\end{aligned}
$$

Since states cannot be measured directly, we can design a state observer to get the unknown states,

$$
\dot {\hat x} = A\hat x + Bu + L\underbrace{(y-C\hat x -Du)}_{\text{output estimation error}}
$$

Given the state estimation error $e = x - \hat x$, there have:

$$
\begin{aligned}
\dot e &= \dot x - \dot{\hat x} \\
&= Ax + Bu - A \hat x - Bu - L(Cx+Du-C\hat x -Du) \\
&= (A-LC)e
\end{aligned}
$$

The eigenvalue of $(A-LC)$ are the same as those of $(A^T-C^TL^T)$, we can let $\tilde A = A^T$, $\tilde B = B^T$, $\tilde C = C^T$, thus we have: $A^T-C^TL^T = \tilde A - \tilde B \tilde K$, Given the observable matrix:

$$
\begin{aligned}
&M_O = \begin{bmatrix} C \\ CA \\ \vdots \\ CA^{n-1}\end{bmatrix} & M_O^T = \begin{bmatrix} \tilde B & \tilde A \tilde B & \cdots & \tilde A^{n-1} \tilde B\end{bmatrix}
\end{aligned}
$$

A N&S condition for the design of an asyntotic observer with arvitrarily specified eigenvalue of the estimation error dynamics is that $(A,C)$ is observable.

Given a system $p = 1$, we can apply Ackermann's formula,

$$
L^T = \begin{bmatrix} 0&\cdots&0&1\end{bmatrix}(M_O^T)^{-1} p^*(A^T)
$$

When the system have $p > 1$, where $C  = \begin{bmatrix} C_1 \\ \vdots \\ C_p \end{bmatrix}$, if $(A,C)$ is observable $\Rightarrow$ $\exists i$, such that $(A, C_i)$ that is observable. We can apply Ackermann's formula on $(A,C_i)$,

$$
\begin{aligned}
L &= \begin{bmatrix} L_1&\cdots&L_p\end{bmatrix} \\
&= \begin{bmatrix} 0&\cdots&0&L_i&0&\cdots&0\end{bmatrix}
\end{aligned}
$$

## 2. Observer for System with Disturbances

$$
\begin{aligned}
&\dot x = Ax + Bu + Md, &x\in\Re^n, u\in\Re^m\\
&y = Cx + Du + Nd, &y\in\Re^p, d\in\Re^r
\end{aligned}
$$

If $d$ is measurable,

$$
\dot{\hat x} = A \dot{\hat x} + Bu + Md + L(y - C\hat x - Du - Nd)
$$

We let $e=x - \hat x$, thus we have:$\dot e=(A-LC)e$

If $d$ is not measurable,

$$
\begin{aligned}
\dot{\hat x} &= A \dot{\hat x} + Bu + L(y - C\hat x - Du) \\
\dot e &= (A-LC) e + (M-LN) d \\
e &= x - \hat x
\end{aligned}
$$

If $d(t) = \bar d$, $\forall t \geq 0$,

$$
e_\infty = -(A-LC)^{-1} (M-LN) \bar d
$$

!!! bug
    missing figure

## 3. Estimation of Constant Disturbances via Observer Design

Motivations:

1. You can estimate the state correctly
2. You can use the disturbances estimattion for the disturbance compensation

    !!! bug
        missing figure

Give the system disturbance: $d(t) = \bar d$, $\forall t$, 

$$
\begin{aligned}
&\dot x = Ax + Bu + Md, &x\in\Re^n, u\in\Re^m\\
&y = Cx + Du + Nd, &y\in\Re^p, d\in\Re^r
\end{aligned}
$$

Because the disturbance $d$ is constant, $\dot d = 0$, and we have:

$$
\begin{aligned}
\begin{bmatrix} \dot x \\ \dot d \end{bmatrix} &= 
\begin{bmatrix} A&M \\ 0&0 \end{bmatrix}
\begin{bmatrix} x \\ d \end{bmatrix} + 
\begin{bmatrix} B \\ 0 \end{bmatrix} u \\
y &= \underbrace{\begin{bmatrix} C&N \end{bmatrix}}_{\tilde C}
\begin{bmatrix} x \\ d \end{bmatrix} + Du
\end{aligned}
$$

* $(\tilde A, \tilde C)$ must be observable $\Leftrightarrow$ $(A,C)$ is observable

* $\text{rank}\begin{bmatrix} A&M \\ 0&0 \end{bmatrix} = n+r$, 

    $r \leq p$, more output than disturbances

    No invraiant zero in $0$ in the transfer matrix for $d$ to $y$

!!! bug 
    missing figure

What are the close loop eigen values:

We assume the order of the system is $n$, 

$$
\begin{aligned}
\text{system: }&\begin{aligned}
\dot x &= Ax + Bu \\
y &= Cx + Du
\end{aligned} \\
\text{control law: }&u = -K\hat x + \gamma \\
\text{observer: }&\dot{\hat x} = A \hat x + Bu + L(y-C\hat x -Du)
\end{aligned}
$$

And we can get:

$$
\begin{aligned}
\dot x &= Ax - BK \hat x + B\gamma \\
\dot {\hat x} &= A\hat x -BK\hat x + B \gamma + L(y-C\hat x)
\end{aligned} \\
$$

Since we have: $e = x - \hat x$,

$$
\begin{aligned}
\dot x &= (A-BK)x + BKe + B\gamma \\
\dot e &= (A-LC)e
\end{aligned} \\
$$

### 3.1 Separation Principle
We can let:

$$
\tilde A = \begin{bmatrix} A-BK&BK \\ 0&A-LC \end{bmatrix}
$$

The eigen value of $\tilde A$ are the union of the eigenvalue of $A-BK$ and $A-LC$, it means that we can design controller and observer independently.

## 4. Stablizing Regulator Transfer Matrix

!!! bug
    missing figure

We replaced observer with the transfer matrix $R(s)$, to find the expression of $R(s)$,

$$
\begin{aligned}
\text{control law: }&u = -K\hat x \\
\text{observer: }&\dot{\hat x} = A \hat x + Bu + L(y-C\hat x)
\end{aligned}
$$

We have:

$$
\begin{aligned}
\dot{\hat x} &= \overbrace{(A-BK-LC)}^{\tilde A} \hat x + \overbrace{L}^{\tilde B}y  \\
u &= \underbrace{-K}_{\tilde C}\hat x
\end{aligned}
$$

The transfer matrix is:

$$
R(s) = K(sI - (A-BK-LC))^{-1}L
$$

## 5. Reduced Order Ovserver
We start with a simplified linear system:

$$
\begin{aligned}
\dot x &= Ax + Bu \\
y &= Cx
\end{aligned}
$$

We can transfer the system,

$$
\begin{aligned}
\tilde x &= Tx \\
\tilde A &= TAT^{-1} \\
\tilde B &= TB \\
\tilde C &= CT^{-1} = \begin{bmatrix} I&0 \end{bmatrix}
\end{aligned}
$$

* $T = \begin{bmatrix} C \\ T_1 \end{bmatrix}$, $\det T \neq 0$
* $(A,C)$ should be observable

$\tilde y = \begin{bmatrix} y \\ \tilde x_v \end{bmatrix}$

$$
\begin{aligned}
\dot y &= \tilde A_{11}y + \tilde A_{12} \tilde x_v + \tilde B_1 u \\
\dot {\tilde x}_v &= \tilde A_{21}y + \tilde A_{22}\tilde x_v + \tilde B_2 u
\end{aligned}
$$

We can let:

$$
\begin{aligned}
z &= \dot y - \tilde A_{11}y - \tilde B_1 u \\ 
&= \tilde A_{12} \tilde x_v \\
\eta &= \tilde A_{21}y + \tilde B_2 u
\end{aligned}
$$

And we have $\dot {\tilde x}_v = \tilde A_{22}\tilde x_v + \eta$, 

Now, we can build the new system:

$$
\begin{aligned}
\dot {\tilde x}_v &= \tilde A_{22}\tilde x_v + \eta \\
z &= \tilde A_{12} \tilde x_v
\end{aligned}
$$

Now this new system have $n-p$ states,

$$
\begin{aligned}
\dot{\hat{\tilde x}}_v &= \tilde A_{22} \hat{\tilde x}_v + \eta + L(z-\tilde A_{12}\hat{\tilde x}_v) \\
\dot{\tilde e}_v &= (\tilde A_{22} - L\tilde A_{12})\tilde e
\end{aligned}
$$

* $(\tilde A_{22}, \tilde A_{12})$ must be observable

$$
\begin{aligned}
\dot{\hat{\tilde x}}_v &= \tilde A_{22} \hat{\tilde x}_v + \tilde A_{21}y + \tilde B_2 u + L(\dot y - \tilde A_{11}y - \tilde B_1 u-\tilde A_{12}\hat{\tilde x}_v) \\
\end{aligned}
$$

Let $w = \tilde x_v - Ly$, 

$$
\begin{aligned}
\dot w &= (\tilde A_{22} - L\tilde A_{12})\hat{\tilde x}_v + (\tilde A_{21} - L\tilde A_{11})y + (\tilde B_2 - L\tilde B_1) u \\
&= (\tilde A_{22} - L\tilde A_{12})w + (\tilde A_{22} - L\tilde A_{12})Ly + (\tilde A_{21} - L\tilde A_{11})y + (\tilde B_2 - L\tilde B_1) u
\end{aligned}
$$

And we have: $\hat{\tilde x}_v = w + Ly$,

$$
\hat x = T^{-1} \hat{\tilde x}_v = T^{-1}
\begin{bmatrix} y\\ \hat{\tilde x}_v \end{bmatrix}
$$

!!! example
    $$
    \left\{\begin{aligned}
    &\dot x_1 = x_2 \\
    &\dot x_2 = u \\
    &y = x_1
    \end{aligned}\right.
    $$

    * $A = \begin{bmatrix} 0&1\\0&0 \end{bmatrix}$
    * $B = \begin{bmatrix} 0\\1 \end{bmatrix}$
    * $C = \begin{bmatrix} 1&0 \end{bmatrix}$
    * $(A,C)$ is observable

    let $z = \dot y$, 
    
    We have $\dot y = x_2$, $\dot x_2 = u$, $z = x_2$, from these equations, we have:

    $$
    \begin{aligned}
    \dot {\hat x}_2 &= u + L(z - \hat x_2) \\
    &= u + L(\dot y - \hat x_2)
    \end{aligned}
    $$

    let $w = \dot x_2 - L\dot y$, we have $\dot w = -L$, and:

    $$
    \dot {\hat x}_2 - L\dot y = u - L\hat x_2 \\
    $$

    Thus we have: $\dot w = -L(\hat x_2 - Ly) - L^2y + u$,

    $$
    \begin{aligned}
    \dot w &= -Lw - L^2y + u \\
    \hat x_2 &= w + Ly
    \end{aligned}
    $$

    Now we have: $\hat x = \begin{bmatrix} y\\ \hat x_2 \end{bmatrix}$

    !!! bug 
        missing figure
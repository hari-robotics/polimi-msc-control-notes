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

## 5. Reduced Order Observer
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

## 6. Pole placement for Observer design

## 7. Pole placement via TF Approach for SISO Linear Systems

!!! bug 
    missing figure

We assume $G(s)$ have following structure:

$$
G(s) = \frac{B(s)}{A(s)} = \frac{b_ns^{n-1}+b_{n-1}s^{n-2}+\dots + b_1s+b_0}{s^{n}+a_{n-1}s^{n-1}+\dots + a_1s+a_0}
$$

And for $R(s)$, it have the order of $n-1$:

$$
R(s) = \frac{F(s)}{\Gamma(s)} = \frac{f_{n-1}s^{n-1}+f_{n-2}s^{n-2}+\dots + f_1s+f_0}{\gamma_{n-1}s^{n-1}+\gamma_{n-2}s^{n-2}+\dots +\gamma_1s+\gamma_0}
$$

We give $P^*(s)$, which  is the desired characteristic polynomial in the closed loop,

$$
P(s) = s^{2n-1} + p_{2n-2}s^{2n-2} + \dots + p_1s + p_0
$$

The characteristic polynomial of the closed loop system is:

$$
P(s) = \Gamma(s)A(s) + B(s)F(s)
$$

We can set the system desired polynomial function the same as our desired one:

$$
P(s) = P^*(s)
$$

Expend it, we have:

$$
\begin{aligned}
\begin{bmatrix} 
1 & 0 &  &&&0&&&& \\
a_{n-1} & 0 &&&& b_{n-1} & 0\\
\vdots & a_{n-1} & \ddots &&& \vdots & b_{n-1} & \ddots \\
a_0  &  \vdots & \ddots &&& b_0  &  \vdots & \ddots \\
0 & a_0 & \ddots && 1 & 0 & b_0 & \ddots && 0\\
\vdots & 0 &\ddots && a_{n-1} & \vdots & 0 &\ddots && b_{n-1}\\
0 & \vdots &&& \vdots & 0 & \vdots &&& \vdots\\
0 & 0 &&& a_0 & 0 & 0 &&& b_0
\end{bmatrix}
\begin{bmatrix} \gamma_{n-1} \\ \vdots \\ \gamma_0 \\ f_{n-1} \\ \vdots \\ f_0\end{bmatrix} = 
\begin{bmatrix} 1 \\ p_{2n-2} \\ p_{2n-3} \\ \vdots \\ p_0 \end{bmatrix}
\end{aligned}
$$

!!! bug
    missing figure

$$
\tilde G(s) = \frac{1}{s}G{s} = \frac{B(s)}{sA(s)}
$$

$\tilde G(s)$ have the order of $n+1$, And we want to design $R(s)$ of order $n$,

$$
R(s) = \frac{F'(s)}{\Gamma'(s)}
$$

The desired polynomial TF $P^*(s)$ have a order of $2n+1$, the characteristic polynomial function of the system is:

$$
P(s) = P(s) = \Gamma'(s)\underbrace{sA(s)}_{\tilde A(s)} + B(s)F'(s) = P^*(s)
$$

### 7.1 Zeros of the Closed Loop System
!!! bug
    missing figure

To calculate the zeros, we need to calculate the comlementry sensitive functions

!!! warning
    Because in the previous part, we already use the $F(s)$, which is not the complementry sensitivity function, so here we rename it to $H(s)$ to resolve the naming conflict

$$
H(s) = \frac{\frac{H(s)B(s)}{\Gamma(s)A(s)}}{1 + \frac{H(s)B(s)}{\Gamma(s)A(s)}} = \frac{F(s)B(s)}{\Gamma(s)A(s) + F(s)B(s)} = \frac{F(s)B(s)}{P^*(s)}
$$

!!! bug
    missing figure

The choosen $\Delta$ should be:

$$
\Delta(s) = s^{n-1} \delta_{n-2}s^{n-2}+\dots +\delta_1s + \delta_0
$$

Calculate the TF from $y^\circ$ to $y$:

$$
W(s) = \frac{F(0)}{\Delta(0)} \frac{\frac{\Delta(s)}{\Gamma(s)}\frac{B(s)}{A(s)}}{1+\frac{F(s)B(s)}{\Gamma(s)A(s)}} = \frac{F(0)}{\Delta(0)}\frac{\Delta(s)B(s)}{P^*(s)}
$$

### 7.2 How to cancel the poles in the system
Given the system:

$$
G(s) = \frac{B(s)}{\underbrace{(s+a)A'(s)}_{A(s)}}
$$

The desired polynomial fuction is:

$$
P^*(s) = \underbrace{(s+a)\tilde P^*(s)}_{2n-1}
$$

For the system polynomial function:

$$
\begin{aligned}
P(s) &= (s+a)A'(s)\Gamma(s) + B(s)F(s) = (s+a)\tilde P^*(s) \\
B(s)F(s) &= (s+a)[\tilde P^*(s) - A'(s)]
\end{aligned}
$$

For the condition that $F(s)$ has a root in $a$, which $F(s) = (s+a)F'(s)$,

$$
L(s) = R(s)G(s) = \frac{(s+a)F'(s)}{\Gamma(s)} \frac{B(s)}{(s+a)A'(s)}
$$

For the system disturbance $d_u$ to $y$, there have the TF:

$$
\begin{aligned}
V(s) &= \frac{G(s)}{1+R(s)G(s)} \\
&= \frac{\frac{B(s)}{(s+a)A'(s)}}{1+\frac{B(s)}{(s+a)A'(s)} \frac{(s+a)F'(s)}{\Gamma(s)}} \\
&= \frac{A'(s)\Gamma(s)B(s)}{\underbrace{\underbrace{(A'(s)\Gamma(s)+B(s)F'(s))}_{\tilde P^*(s)}(s+a)A'(s)}_{P^*(s)}}
\end{aligned}
$$

!!! bug
    missing figure

!!! example
    Given the system:

    $$
    G(s) = \frac{1}{s-1}
    $$

    Design a regulator which include an integral action such that all the close loop poles are $-1$

    1. State space approach

        $$
        \begin{aligned}
            \dot x &= x + u \\
            y &= x
            \dot v= -x
        \end{aligned}
        $$

        !!! bug
            missing figure

        $$
        \begin{bmatrix} \dot x \\ \dot v \end{bmatrix} = 
        \underbrace{\begin{bmatrix} 1&0 \\ -1&0 \end{bmatrix}}_{\tilde A}
        \begin{bmatrix} x \\ v \end{bmatrix} + 
        \underbrace{\begin{bmatrix} 1 \\ 0 \end{bmatrix}}_{\tilde B} u
        $$

        $$
        u = -K \begin{bmatrix} x \\ v \end{bmatrix} = -K_xx - K_vv
        $$

        The closed loop system is:

        $$
        \begin{bmatrix} \dot x \\ \dot v \end{bmatrix} =
        \underbrace{(A-BK)}_{\hat L} \begin{bmatrix} x \\ v \end{bmatrix} 
        $$

        The characteristic polynomial is:

        $$
        P_{\tilde A - \tilde BK}(\lambda) = \det
        \begin{bmatrix} \lambda - 1+ K_x & K_v \\ 1&\lambda \end{bmatrix} =
        \lambda^2 + (K_x - 1)\lambda - K_v
        $$

        And the desired polynomial function is:
        
        $$
        P^*(\lambda) = (\lambda + 1)^2 = \lambda^2 + 2\lambda + 1
        $$

        And the result is:

        $$
        \begin{aligned}
        K_x &= 3 \\
        K_v &= -1
        \end{aligned}
        $$

    2. Pole placement with TF

        !!! bug
            missing figure

        $$
        \tilde G(s) = \frac{1}{s(s-1)}
        $$

        $$
        R'(s) = \frac{f_1s + f_0}{\gamma_1s + \gamma_0}
        $$

        $$
        \begin{aligned}
        P(s) &= (s^2 - s)(\gamma_1s + \gamma_0) + f_1s + f_0 \\
        P^*(s) &= (s+1)^3 = s^3 + 3s^2 + 3s + 1
        \end{aligned}
        $$

        $$
        \begin{bmatrix} 
        1 & 0 & 0 & 0\\
        -1& 1 & 0 & 0\\
        0 &-1 & 1 & 0\\
        0 & 0 & 0 & 1
        \end{bmatrix}
        \begin{bmatrix} \gamma_1 \\ \gamma_0 \\ f_1 \\ f_0 \end{bmatrix} = 
        \begin{bmatrix} 1 \\ 3 \\ 3 \\ 1 \end{bmatrix}
        $$

        $$
        \begin{aligned}
        &\gamma_1 = 1 & f_1 = 7 \\
        &\gamma_2 = 4 & f_0 = 1
        \end{aligned}
        $$

        $$
        R'(s) = \frac{f_1s+f_0}{\gamma_1s+\gamma_0} = \frac{7(s+\frac17)}{s+4}
        $$

    3. $R(s) = p\frac{s+\alpha}{s}$

        $$
        \begin{aligned}
        1 + R(s)G(s) &= 0 \\
        s(s-1) + p(s+\alpha) &= (s+1)^2
        \end{aligned}
        $$
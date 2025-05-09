## 1. Poles and Zeros of MIMO Linear Systems
### 1.1 From State Space to Transfer Matrix
For a linear system, there have state space representations and TF, which can converts bi-directionally:

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t) \\
y(t) &= Cx(t) + Du(t)
\end{aligned} \Leftrightarrow 
\begin{aligned}
y(s) = G(s)u(s)
\end{aligned}
$$

The conversion between TF and state space have: 

$$
G(s) = C(s\mathbf I -A)^{-1}B+D
$$

* $G(s) = \begin{bmatrix} G_{11}(s) & \dots & G_{1j} \\ \vdots && \vdots \\ G_{i1} & \cdots & G_{ij} \end{bmatrix}$ is the transfer matrix of the system, the element $G_{ij} \in G(s)$ means that input $u_j$ contributes to output $y_i$.

__Definition__: The poles of $G(s)$ are the eigenvalues of the reachable and conservable part of the system.

!!!note 
    If the system is reachable and observable, then: $\lambda_A$ is the poles of $G(s)$.

### 1.2 Poles of a MIMO system
__Question__: Now we have the transfer matrix of the MIMO system, how can we calculate the poles for $G(s)$?

__Answer__: Within the following theorem:

* The characteristic polynomial $\phi(s)$ of a minimal realization of $G(s)$ is the least common denominator of all (non null) minors of $G(s)$.
* Poles is the solution for $\phi(s) = 0$.

!!! example
    $$
    G(s) = \begin{bmatrix} 
        \frac{1}{s+1} & 0 \\
        0 & \frac{3}{s+1}
    \end{bmatrix}
    $$

    * Minors of order 1: $\frac{1}{s+1}$, $\frac{3}{s+1}$,
    * Minors of order 2: $\frac{3}{(s+1)^2}$
    * The minimal realization has order $n=2$: $\phi(s) = (s+1)^2$
    * Poles: $-1$, $-1$

!!! example
    $$
    G(s) = \begin{bmatrix} 
        \frac{1}{s+1} & -\frac{1}{s+1} \\
        \frac{1}{s+1} & \frac{s}{s+1}
    \end{bmatrix}
    $$

    * Minors of order 1: $\frac{1}{s+1}$, $-\frac{1}{s+1}$, $\frac{1}{s+1}$, $\frac{s}{s+1}$
    * Minors of order 2: $\frac{s}{(s+1)^2} + \frac{1}{(s+1)^2} = \frac{1}{s+1}$
    * The minimal realization has order $n=2$: $\phi(s) = s+1$
    * Poles: $-1$

!!! example
    $$
    \begin{aligned}
    \dot x(t) &= -x(t) + \begin{bmatrix} 1 & -1 \end{bmatrix} \begin{bmatrix} u_1(t) \\ u_2(t)\end{bmatrix} \\
    \begin{bmatrix} y_1(t) \\ y_2(t)\end{bmatrix} &= \begin{bmatrix} 1 \\ 1\end{bmatrix}x(t) + \begin{bmatrix} 0 & 0 \\ 0 & 1 \end{bmatrix}\begin{bmatrix} u_1(t) \\ u_2(t)\end{bmatrix}
    \end{aligned}
    $$

!!!example
    $$
    G(s) = \begin{bmatrix} 
        \frac{1}{s+1} & 0 & \frac{s-1}{(s+1)(s+2)} \\
        -\frac{1}{s+1} & \frac{1}{s+2} & \frac{1}{s+2}
    \end{bmatrix}
    $$

    * Minors of order 1: $\frac{1}{s+1}$, $-\frac{1}{s+1}$, $\frac{s-1}{(s+1)(s+2)}$, $\frac{1}{s+2}$, $\frac{1}{s+2}$
    * Minors of order 2: 

        $M_1 = \det\begin{bmatrix} 
            0 & \frac{s-1}{(s+1)(s+2)} \\
            \frac{1}{s+2} & \frac{1}{s+2}
        \end{bmatrix} = -\frac{s-1}{(s+1)(s+2)^2}$

        $M_2 = \det \begin{bmatrix} 
        \frac{1}{s+1} & \frac{s-1}{(s+1)(s+2)} \\
        -\frac{1}{s+1} & \frac{1}{s+2}
        \end{bmatrix} = \frac{2}{(s+1)(s+2)}$

        $M_3 = \det \begin{bmatrix} 
        \frac{1}{s+1} & 0 \\
        -\frac{1}{s+1} & \frac{1}{s+2}
        \end{bmatrix} = \frac{1}{(s+1)(s+2)}$

    * The minimal realization has order $n=4$: $\phi(s) = (s-1)(s+1)(s+2)^2$,
    * Poles: $1$, $-1$, $-2$, $-2$

### 1.3 Zeros of a SISO System

Given TF of a SISO system:

$$
G(s) = \frac{N(s)}{D(s)}
$$

__Definition__: Zeros for the SISO system is the root for equation: $N(s)=0$.

__Theorem__ :

1. response to an exponential input signal

    If $\alpha$ is not an eigenvalue of matrix $A$ of the SISO system, 

    $$
    \begin{aligned}
    \dot x(t) &= Ax(t) + Bu(t) \\
    y(t) &= Cx(t) + Du(t)
    \end{aligned} \Leftrightarrow 
    \begin{aligned}
    y(s) = G(s)u(s)
    \end{aligned}
    $$

    There exists an initial state of $x_0$, such that:

    Given $u(t) = u_0e^{\alpha t}, t \geq 0$, the output is: $y(t) = y_0e^{\alpha t}, t\geq 0$, with $y_0 = u_0G(s)|_{s=\alpha}$

2. Corollary (Blocking property of zeros in SISO case):

    If $\alpha$ is a zero of $G(s)$, then there exists an initial condition $x_0$ such that: 
    
    Given the input $u(t) = u_0e^{\alpha t}$, the output is null at any t ($y(t) = 0, t \geq 0$).

!!! remark
    1. If the system is A.S., then $\forall x_0$, the output associated to $u(t) = u_0e^{\alpha t}, t \geq 0$, will tend to $y_\infty(t) = u_0G(\alpha)e^{\alpha t}, t \geq 0$, if $\alpha = 0$, then $\lim_{t\to \infty}y(t)=0$

    2. If $G(s)$ has a zero in $\alpha = 0$, and the system is A.S., then $u(t) = u_0, t \geq 0$, will correspond to $y(t)$ that $\lim_{t\to \infty}y(t)=0$


    $$
    G(s) = s\tilde G(s)
    $$

    <figure markdown="span">
        ![](pics/chapter12/figure1.png){ width="500" }
    </figure>

For the regulator that regulates the system,

<figure markdown="span">
    ![](pics/chapter12/figure2.png){ width="500" }
</figure>

If $G(s)$ has a zero in $s = 0$, the TF for $y^\circ \to y$ is:

$$
T(s) = \frac{R(s)G(s)}{1+R(s)G(s)} = \frac{N_R(s)N_G(s)}{D_R(s)D_G(s) + N_R(s)N_G(s)}
$$

$T(s)$ also has a zero in $s = 0$.

### 1.4 Zeros of a MIMO system
__Definition__:

1. system matrix

    $$
    \begin{aligned}
    \dot x(t) &= Ax(t) + Bu(t) \\
    y(t) &= Cx(t) + Du(t)
    \end{aligned}
    $$

    within the laplacian transform and the initial condition $x(0) = 0$, we can get:

    $$
    \begin{aligned}
    &\begin{aligned}
    sx(s) &= AX(s) + BU(s) \\
    y(t) &= CX(s) + DU(s)
    \end{aligned} \\
    \Rightarrow&\underbrace{\begin{bmatrix} sI-A & -B \\ C & D \end{bmatrix}}_{\text{system matrix } P(s)} \begin{bmatrix} X(s) \\ U(s) \end{bmatrix} = \begin{bmatrix} 0 \\ y(s) \end{bmatrix}
    \end{aligned}
    $$

    The nominal rank of $P(s)$ is the rank of the matrix for all values of $s$ except for a finite number. 

2. Invariant zeros of a MIMO system:

    The invariant zero values of a system $=$ the values of $s$, such that: the rank of $P(s)$ is slower than its normal rank. 

!!! remark
    the invariant zeros of a MIMO system satisfy the blocking property

    1. If $\alpha$ is an invariant zero, then, there exists an initial state $x_0$, and a vector $u_0$, such that: given the input, $u(t) = u_0e^{\alpha t}, t \geq 0$, the output is null for any $t$.

__Question__: How to compute the invariant zeros form $G(s)$?

__Answer__: $r =$ The normal rank of $G(s)$ $=$ the rank of $G(s)$ for all values of $s$ except for a finite number.

__Theorem__: Let $Z(s)$ be the polynomial whose roots are all and only the invariant zeros of the system. $Z(s)$ is called __polynomial of the invariant zeros__. Then $Z(s)$ is the greatest common divisor of all minors of order $r$ of the rank of $G(s)$ written, so that the polynomial of the poles of $\phi(s)$ at the denominator.

!!! example 

    $$
    G(s) = \frac{1}{(0.2s+1)(1+s)}\begin{bmatrix} 1 & 1 \\ 1+2s & 2 \end{bmatrix}
    $$

    * rank of $G(s)$: $r = \text{rank}(G(s)) = 2$
    * $\phi(s)$: 
        * minors of order 1: all $G_{ij} \in G(s)$
        * minors of order 2: $\det(G(s)) = \frac{1-2s}{(0.2s+1)^2(1+s)^2}$
        * $\phi(s) = (0.2s+1)^2(1+s)^2$

    * $Z(s) = 1-2s$
        * Zeros: $\frac12$

!!! example
    $$
    G(s) = \begin{bmatrix} \frac{s+1}{(s+2)(s+3)} & \frac{4}{(s+2)(s+3)} \\ \frac{0.5}{(s+2)(s+3)} & \frac{2}{(s+2)(s+3)} \end{bmatrix}
    $$

    * rank of $G(s)$: $r = rank(G(s)) = 2$
    * $\phi(s)$: 
        * minors of order 1: all $G_{ij} \in G(s)$
        * minors of order 2: $\det(G(s)) = \frac{2s}{(s+2)^2(s+3)^2}$
        * $\phi(s) = (s+2)^2(s+3)^2$
        * Poles: $-2$, $-2$, $-3$, $-3$
    * $Z(s) = 2s$
        * Zeros: $0$
    
    The system is A.S.

    $$
    \begin{bmatrix} \bar y_1 \\ \bar y_2 \end{bmatrix} = G(0) \begin{bmatrix} \bar u_1 \\ \bar u_2 \end{bmatrix} 
    $$

    $G(0)$ is static gain matrix

    $$
    \begin{aligned}
    G(0) &= \begin{bmatrix} \frac16 & \frac23 \\ \frac{0.5}{6} & \frac13 \end{bmatrix} \\
    \det(G(0)) &= 0
    \end{aligned}
    $$

    $\bar y_1 = \frac16 \bar u_1 + \frac23 \bar u_2$, 
    
    $\bar y_2 = \frac12 (\frac16 \bar u_1 + \frac23 \bar u_2)$

    If define input $u_0 = \begin{bmatrix} \bar u_1 \\ -\frac14 \bar u_1 \end{bmatrix}$, we get $\bar y = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$.

!!! example
    $$
    \begin{aligned}
    G(s) &= \begin{bmatrix} \frac{1}{s+1} & 0 & \frac{s-1}{(s+1)(s+2)} \\ -\frac{1}{s-1} & \frac{1}{s+2} & \frac{1}{s+2} \end{bmatrix} \\
    \end{aligned}
    $$

    * rank of $G(s)$: $r = rank(G(s)) = 2$
    * $\phi(s) = (s-1)(s+1)(s+2)^2$
    * Minors of order 2: $M_1 = -\frac{s-1}{(s+1)(s+2)^2}$, $M_2 = \frac{2}{(s+1)(s+2)}$, $M_3 = \frac{1}{(s+1)(s+2)}$
    * $M_1 = -\frac{(s-1)^2}{\phi(s)}$, $M_2 = \frac{2(s+2)(s-1)}{\phi(s)}$, $M_3 = \frac{(s+2)(s-1)}{\phi(s)}$
    * $Z(s) = (s-1)$
    * Zeros: 1

### 1.5 Poles and Invariant Zeros of Discrete MIMO Systems
For Discrete Time MIMO Linear Systems

Same definitions for poles and invariant zeros, just $z$ in place of $s$,

$$
\begin{aligned}
P(z) &= \begin{bmatrix} zI-A & -B \\ C & D \end{bmatrix} \\
G(z) &= (z-1)\tilde G(z)
\end{aligned}
$$

## 2. MIMO Linear System Analysis

### 2.1 Cascade System Analysis
<figure markdown="span">
    ![](pics/chapter12/figure3.png){ width="500" }
</figure>

* $G_1$ is a $m_1 \times n_1$ Matrix,
* $G_2$ is a $m_2 \times n_2$ Matrix, $n_1 = m_2$

We can describe the system:

$$
\begin{aligned}
y &= G_2(s)u_2 = G_2(s)G_1(s)u \\
G(s) &= \underbrace{G_2(s)G_1(s)}_{n_2 \times m_1}
\end{aligned}
$$

### 2.2 Feedback System Analysis
Now we looks at the feedback system:

<figure markdown="span">
    ![](pics/chapter12/figure4.png){ width="500" }
</figure>

* $u_1 = u - y_2$
* $G_1$ is $n \times m$, 
* $G_2$ is $m\times n$, 

we can calculate the transfer matrix of the system:

$$
\begin{aligned}
y(s) &= (I_n + G_1(s)G_2(s))^{-1}G_1(s)U(s) \\
&= G_1(s)(I_m + G_1(s)G_2(s))^{-1}U(s)
\end{aligned}
$$

!!! info

    Proof:

    $$
    \begin{aligned}
    y(s) &= G_1(s)U_1(s) = G_1(s) (U(s) - G_2(s)y(s)) \\
    (I_n + G_1(s)G_2(s))y(s) &= G_1(s)U(s) \\
    y(s) &= (I_n + G_1(s)G_2(s))^{-1}G_1(s)U(s)
    \end{aligned}
    $$

    $$
    \begin{aligned}
    y(s) &= G_1(s)U_1(s) \\
    U_1(s) &= U(s) - G_2(s)y(s) = U(s) - G_2(s)G_1(s)U_1(s) \\
    (I_m + G_2(s)G_1(s))U_1(s) &= U(s) \\
    U_1(s) &= (I_m + G_2(s)G_1(s))^{-1}U(s) \\
    y(s) &= G_1(s)U_1(s) = G_1(s)(I_m + G_2(s)G_1(s))^{-1}U(s)
    \end{aligned}
    $$

### 2.3 Frequency Response 
We consider a SISO A.S. system, with its TF of $G(s)$

<figure markdown="span">
    ![](pics/chapter12/figure5.png){ width="500" }
</figure>

The gain at $\omega$ of the TF $G(s)$ is:

$$
|G(j\omega)| = \frac{|y(j\omega)|}{|U(j\omega)|}
$$

Now we deal with MIMO systems, we have the same as SISO one, which gives the gain of the MIMO system with TF $G(s)$ at $\omega$:

$$
\begin{aligned}
\frac{||y(j\omega)||_2}{||U(j\omega)||_2} &= \frac{||G(j\omega)U(j\omega)||_2}{||U(j\omega)||_2} \\
\end{aligned}
$$


$$
||G(j\omega)U(j\omega)||_2^2 = U^*(j\omega)\underbrace{G^*(j\omega)G(j\omega)}_{m \times m}U(j\omega)
$$

$$
\underbrace{\lambda_{\min} (G^*(j\omega)G(j\omega))}_{\geq 0}||U(j\omega)||_2^2 \leq 
U^*(j\omega)\underbrace{G^*(j\omega)G(j\omega)}_{\text{symmetric, } \succeq 0}U(j\omega) \leq 
\underbrace{\lambda_{\max} (G^*(j\omega)G(j\omega))}_{> 0}||U(j\omega)||_2^2
$$

$$
\underline{\sigma}(G(j\omega)) = \left\{\begin{aligned} 
&\sigma_\min, &m\leq p\\
&0, &m>n
\end{aligned}\right.
$$

<figure markdown="span">
    ![](pics/chapter12/figure6.png){ width="300" }
</figure>

And we have $\gamma(G(j\omega)) = \frac{\bar \sigma (G(j\omega))}{\underline \sigma (G(j\omega))}$, is the condition number at $\omega$.

!!!example
    Consider a static system,

    $$
    \begin{aligned} 
    &G = \begin{bmatrix} 1&2 \\3&4 \end{bmatrix} &  \\
    &U_1 = \begin{bmatrix} 1\\0 \end{bmatrix} &y_1 = \begin{bmatrix} 1\\3 \end{bmatrix} \\
    & U_2 = \begin{bmatrix} 0\\1 \end{bmatrix} &y_2 = \begin{bmatrix} 2\\4 \end{bmatrix} \\
    & U_3 = \begin{bmatrix} \frac{\sqrt 2}{2}\\\frac{\sqrt 2}{2} \end{bmatrix} &y_3 = \begin{bmatrix} 2.12\\4.95 \end{bmatrix} \\
    & U_4 = \begin{bmatrix} \frac{\sqrt 2}{2}\\-\frac{\sqrt 2}{2} \end{bmatrix} &y_4 = \begin{bmatrix} -\frac{\sqrt 2}{2}\\-\frac{\sqrt 2}{2} \end{bmatrix} \\
    & U_5 = \begin{bmatrix} 0.8\\-0.6 \end{bmatrix} &y_5 = \begin{bmatrix} -0.4\\0 \end{bmatrix}
    \end{aligned}
    $$

    $||y_1||_2 = 3.16$, $||y_2||_2 = 4.45$, $||y_3||_2 = 5.38$, $||y_4||_2 = 1$, $||y_5||_2 = 0.4$,

    $\underline \sigma(G) = 0.37$, $\bar \sigma(G) = 5.17$

<figure markdown="span">
    ![](pics/chapter11/figure1.png){ width="500" }
</figure>

* $G(s)$ is $n\times m$ matrix, 
* $R(s)$ is $m \times n$ matrix, 
* $L=G(s)R(s)$ is $n\times n$ matrix,
* $L_u(s) = R(s)G(s)$ is $m\times m$ matrix.

$$
\begin{aligned} 
y(s) &= T(s)(y^\circ(s)-N(s)) + S(s)D_y(s) + S(s)G(s)D_u(s) \\
T(s) &= (I_n + L(s))^{-1}L(s) = L(s)(I+L(s))^{-1} \\
S(s) &= (I_n + L(s))^{-1} \\
T(s) + S(s) &= I \\
U(s) &= (I_m + L_u(s))^{-1}R(s)(y^\circ(s)-D_y(s)-N(s)) + (I_m + L_u(s))^{-1}D_u(s)
\end{aligned}
$$

The feedback system is A.S. if:

1. There is no cancellation if unstable poles inside the blocks 
2. Bounded input applied at any point of the feedback system produce bounded outputs at any point of the system 

The feedback system with $R(s)$ and $G(s)$ are stabilizable and detectable is A.S. if and only if the transfer matrices:

$$
\begin{aligned} 
k_1(s) &= (I+L(s))^{-1} L(s) \\
k_2(s) &= (I+L(s))^{-1} \\
k_3(s) &= (I+L(s))^{-1} G(s) \\
k_4(s) &= (I+L_u(s))^{-1} R(s) \\
k_5(s) &= (I+L_u(s))^{-1}
\end{aligned}
$$

Have all poles with $\Re < 0$.

!!! remark

    <figure markdown="span">
        ![](pics/chapter12/figure3.png){ width="500" }
    </figure>

    $$
    \begin{aligned} 
    G_1(s) &= \begin{bmatrix}\frac{4}{s+3}&0 \\ 0&\frac{4(s-1)}{s} \end{bmatrix} \\
    G_2(s) &= \begin{bmatrix}\frac{4}{s-3}&0 \\ 0&\frac{1}{s+8} \end{bmatrix} 
    \end{aligned}
    $$

    * Poles for $G_1$: $-3$, $0$,
    * Zeros for $G_1$: $1$
    * Poles for $G_2$: $1$, $-8$,

    $$
    G(s) = G_2(s)G_1(s) = \begin{bmatrix}\frac{16}{(s-1)(s-3)}&0 \\ 0&\frac{-4(s-1)}{s(s+8)} \end{bmatrix} 
    $$

    * Poles for $G$: $1$, $-8$, $-3$, $0$,
    * Zeros for $G$: $1$

### 2.3 Nyquist Criterion

<figure markdown="span">
    ![](pics/chapter12/figure7.png){ width="300" }
</figure>

$L(s) = G(s)R(s)$, assume $L(s)$ is the transfer matrix of a stabilizable and detectable system,

$p_{ol}$ is the number of the poles of $L(s)$ with $Re > 0$

Then, the closed loop system is A.S. if and only if the Nyquist plot of $\det(I+L(s))$ does not pass through the origin, and the number of its encirclements around the origin is $p_{ol}$.

__Sufficient Condition__: A closed loop system with loop transfer matrix $L(s)$ made by A.S. systems is A.S. if $||L(s)||_\infty = \sup_\omega \bar \sigma(L(j\omega))< 1$.

### 2.4 Analysis of a Feedback Control Scheme

<figure markdown="span">
    ![](pics/chapter10/figure4.png){ width="500" }
</figure>

Assume that $G(s)$ and $R(s)$ are the transfer matrix of the systems, that are stabilizable and detectable.

If there are no cancellations between poles and invariant zeros of $R(s)$ and $G(s)$, with $\Re \geq 0$

Then the feedback system is A.S. if and only if one of the transfer matrices between one input and one output signal (port) has all poles with $\Re < 0$.

## 3. Static Performance
### 3.1 SISO System Case

<figure markdown="span">
    ![](pics/chapter12/figure8.png){ width="500" }
</figure>

$$
\begin{aligned}
y^{\circ}(t) &= A,& t\geq 0 \\
d(t) &= B,& t \geq 0
\end{aligned}
$$

Assume the closed loop system is A.S., the TF $y^{\circ} \to y$ is: $T=\frac{L(s)}{1+L(s)}$

$$
y_{y^{\circ}, \infty} = \lim_{t\to\infty}y_{y^{\circ}}(t) = \lim_{s\to 0}s\frac{L(s)}{1+L(s)} \frac{A}{s} = \left\{\begin{aligned}
&\frac{\mu_L}{1+\mu_L}A, &g = 0 \\
&A, &g > 0
\end{aligned}\right.
$$

* $\mu_L$ is the static gain
* $L(s) = \frac{\mu_L}{s^g}\frac{\prod_i(1+sT_i)}{\prod_i(1+s\tau_i)}$, $g$ is the number of poles $\leq 0$.

And for the sensitivity function, we have TF $d \to y$: $S(s) = \frac{1}{1+L(s)}$, and we have:

$$
y_{d, \infty} = \lim_{t\to\infty}y_{y^{\circ}}(t) = \lim_{s\to 0}s\frac{1}{1+L(s)} \frac{B}{s} = \left\{\begin{aligned}
&\frac{1}{1+\mu_L}B, &g = 0 \\
&0, &g > 0
\end{aligned}\right.
$$

And we have: $e = y^{\circ} - y$, for above 2 equations, when $g > 0$, $e_{y^{\circ}, \infty} = 0$, $e_{d, \infty} = 0$

When $g > 0$, we can let $R(s) = \frac{1}{s}R'(s)$, and the block diagram becomes:

<figure markdown="span">
    ![](pics/chapter12/figure9.png){ width="500" }
</figure>

Because $y^\circ$ and $d$ are constants, we can get the plot of the system in steady state:

<figure markdown="span">
    ![](pics/chapter12/figure10.png){ width="500" }
</figure>

### 3.2 MIMO System Case
For a MIMO system, we have following block diagram:

<figure markdown="span">
    ![](pics/chapter12/figure11.png){ width="500" }
</figure>

The system function is:

$$
\left\{\begin{aligned}
&\dot x = Ax + Bu + Md, &x\in\Re^n, &u\in\Re^m\\
&y = Cx + Nd, &y\in\Re^p, &d\in\Re^r
\end{aligned}\right.
$$

* $d$ is a constant $\to$ $d = \bar d$
* $y^\circ$ is a constant $\to$ $y^\circ = \bar y^\circ$

At steady state, there have:

$$
\begin{aligned}
&\left\{\begin{aligned}
&0 = A\bar x + B\bar u + M\bar d\\
&\bar y^\circ = C\bar x + N\bar d
\end{aligned}\right. \\ \Rightarrow
&\left\{\begin{aligned}
&-A\bar x - B\bar u = M\bar d\\
&C\bar x = \bar y^\circ - N\bar d
\end{aligned}\right. \\ \Rightarrow
&\underbrace{\begin{bmatrix} -A&-B \\ C&0 \end{bmatrix}}_{(n+p)\times(n+m)}
\begin{bmatrix} \bar x \\ \bar u \end{bmatrix} = 
\begin{bmatrix} 0&M \\ I&-N \end{bmatrix}
\begin{bmatrix} \bar y^\circ \\ \bar d \end{bmatrix}
\end{aligned}
$$

And for the system matrix, we have: $P(s) = \begin{bmatrix} Is-A&-B \\ C&0 \end{bmatrix}$

1. $n+p \leq n+m \Leftrightarrow m\geq p$
2. $P(0)$ is full rank $(r=n+p)$ $\Rightarrow$ no zeros in $s=0$

Assume the system is reachable and observable $\Leftrightarrow$ $\left\{\begin{aligned} &\text{rank}(\text{ctrl}(A,B)) = r \\ &\text{rank}(\text{obsv}(A,C)) = r \end{aligned}\right.$

!!!info
    Proof:

    $$
    \dot v = e = y^{\circ}(t) - y(t) = y^{\circ}(t) - Cx(t) - Nd(t)
    $$

    Now we have the enlarged system with the integrator:

    $$
    \begin{aligned}
    \begin{bmatrix} \dot x \\ \dot v \end{bmatrix} &= 
    \underbrace{\begin{bmatrix} A&0 \\ -C&0 \end{bmatrix}}_{\bar A}
    \begin{bmatrix} x(t) \\ v(t) \end{bmatrix} +
    \underbrace{\begin{bmatrix} B \\ 0 \end{bmatrix}}_{\bar B} u(t) + 
    \begin{bmatrix} 0&M \\ I&-N \end{bmatrix}
    \begin{bmatrix} y^\circ \\ d \end{bmatrix} \\
    v(t) &= \underbrace{\begin{bmatrix} 0&I \end{bmatrix}}_{\bar C}
    \begin{bmatrix} x(t) \\ v(t) \end{bmatrix}
    \end{aligned}
    $$

    If $(\bar A, \bar B)$ are reachable, 

    $$
    \begin{aligned}
    \bar M_R &= \begin{bmatrix} \bar B & \bar AB & \bar A^2B & \dots & \bar A^{n+p-1}B \end{bmatrix} \\
    &= \underbrace{\begin{bmatrix} A&B\\-C&0 \end{bmatrix}}_{-P(0)}
    \begin{bmatrix} 0&B&AB&\dots\\-C&0&0&\dots \end{bmatrix}
    \end{aligned}
    $$

    And we have $\text{rank}(\bar M_R) \leq \min(\text{rank}(P(0)), \text{rank}(\bar M))$,

    $(A,B)$ is reachable if and only if no zeros in $s = 0$.

Similarly, if $(\bar A, \bar C)$ are observable, $(A,C)$ is observable if and only if no zeros in $s = 0$.

!!!info
    Proof:
    
    $$
    M_o = \begin{bmatrix} 
    \bar C \\ \bar CA \\ \vdots \\ \bar CA^{n+p-1}
    \end{bmatrix} =
    \begin{bmatrix} 
    0&I \\ -C&0 \\ -CA&\vdots \\ \vdots&\vdots
    \end{bmatrix}
    $$


## 4. Dynamic Performance
### 4.1 SISO Systems 

Given a system with characteristic function $L(s) = R(s)G(s)$, the system stability performance can be described by the figure:

<figure markdown="span">
    ![](pics/chapter12/figure12.png){ width="300" }
</figure>

* $T(s) = \frac{L(s)}{1+L(s)} \simeq 1$ at low frequency
* $S(s) = \frac{1}{1+L(s)} \simeq 0$ at low frequency
* $T(s) = R(s)S(s) \simeq 0$ at high frequency

We can find the minimum $(\underline \sigma)$ and maximum $(\overline \sigma)$ singular value of this system, to maintain the stability performance of the system, we need to make sure:

* $\underline \sigma$ is big enough at low frequency and,
* $\overline \sigma$ is small enough at high frequency

<figure markdown="span">
    ![](pics/chapter12/figure13.png){ width="300" }
</figure>

### 4.2 Discrete Time System Design in SISO case
We consider a realistic discrete time system:

<figure markdown="span">
    ![](pics/chapter12/figure14.png){ width="600" }
</figure>

The system have the following state space equation:

$$
\begin{aligned}
x(k+1) &= Ax(k) + Bu(k) \\
y(k) &= Cx(k) + Du(k)
\end{aligned}
$$

We have done the extended system with integrator in continues time, now we want to solve for the integrator in discrete time:

<figure markdown="span">
    ![](pics/chapter12/figure15.png){ width="400" }
</figure>

For the integrator, we can give the following expression:

1. $\text{INT} = \frac{1}{z-1}$

    Within the chosen integrator, we can turn it into the sample based expression:

    $$
    \begin{aligned}
    v(z) &= \frac{1}{z-1}e(z) = \frac{z^{-1}}{1-z^{-1}}e(z) \\
    v(z) - z^{-1}v(z) &= z^{-1}e(z) \\
    v(k) &= v(k-1) + e(k - 1)
    \end{aligned}
    $$

2. $\text{INT} = \frac{z}{z-1}$

    The similar process could be done for this expression of integration, the sample based expression is:

    $$
    v(k) = v(k-1) + e(k)
    $$

For the 2 methods of integration above, 

* $\text{INT} = \frac{1}{z-1}$ have one step delay, but gives the time for calculation process, could be applied in a real system
* $\text{INT} = \frac{z}{z-1}$ have no delay, but needs zero time for computation, which is not implementable

Considering the time axis:

<figure markdown="span">
    ![](pics/chapter12/figure15.png){ width="400" }
</figure>

The disturbance that inserts between 2 sample points, for the integrator with $\frac{1}{z-1}$, this disturbance could not be considered since it have delay, while $\frac{z}{z-1}$ can correctly accept the disturbance and control it.

Considering the pros and cons of these integrators, we choose $\frac{1}{z-1}$ for the discrete system integration.

### 4.3 Discrete Time System Design in MIMO case
Now we look at the MIMO system in discrete case:

<figure markdown="span">
    ![](pics/chapter12/figure17.png){ width="600" }
</figure>

We have the same structure as the continues time MIMO system design, it should satisfy the following condition (the derivation in discrete time is $(z-1)$):

1. $m\geq p$
2. No invariant zero in $z = 1$
3. $(A,B)$ is reachable and $(A,C)$ is observable
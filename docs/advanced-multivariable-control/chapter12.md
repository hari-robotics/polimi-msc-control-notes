## 1. Poles and Zeros for MIMO Linear Systems

Recall on the state space function:

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t) \\
y(t) &= Cx(t) + Du(t)
\end{aligned}
$$

within laplace transform, we can get:

$$
\begin{aligned}
y(s) = G(s)u(s)
\end{aligned}
$$

Where $G(s) = C(s\mathbf I -A)^{-1}B+D$, for the element $G_{ij} \in G(s)$, it means that input $u_j$ contributes to output $y_i$.

The defination of poles of $G(s)$ is: the poles of $G(s)$ are the eigenvalues of the reachable and conservable part of the system.

!!!note 
    If the system is reachable and obserable, then: $\lambda_A$ is the poles of $G(s)$.

How can we calculate the poles from $G(s)$:

Within the following theorem:

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

### 1.1 Zeros for SISO Linear Systems

Given TF:

$$
G(s) = \frac{N(s)}{D(s)}
$$

Zeros for the SISO system is the root for $N(s)=0$.

The theorem is (response to an exponential input signal):

* If $\alpha$ is not an eigenvalue of matrix $A$ of the SISO system, 

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t) \\
y(t) &= Cx(t) + Du(t)
\end{aligned}
$$

within laplace transform, we can get:

$$
\begin{aligned}
y(s) = G(s)u(s)
\end{aligned}
$$

Then there exists an initial state of $x_0$, such that:

Given $u(t) = u_0e^{\alpha t}, t \geq 0$, the output is: $y(t) = y_0e^{\alpha t}, t\geq 0$, with $y_0 = u_0G(s)|_{s=\alpha}$

Corollary (Bloking properity of zeros in SISO case):

If $\alpha$ is a zero of $G(s)$, then there exists an initial condition $x_0$ such that: given the input $u(t) = u_0e^{\alpha t}$, the output is null at any t ($y(t) = 0, t \geq 0$).

* Remark:
    1. If the system is A.S., then $\forall x_0$, the output associated to $u(t) = u_0e^{\alpha t}, t \geq 0$, will tend to $y_\infty(t) = u_0G(\alpha)e^{\alpha t}, t \geq 0$, if $\alpha = 0$, then $\lim_{t\to \infty}y(t)=0$

    2. If $G(s)$ has a zero in $\alpha = 0$, and the system is A.S., then $u(t) = u_0, t \geq 0$, will correspond to $y(t)$ that $\lim_{t\to \infty}y(t)=0$


$$
G(s) = s\tilde G(s)
$$

Missing Figure


<figure markdown="span">
    ![](pics/chapter11/figure1.png){ width="500" }
</figure>

And we have $G(s)$ has a zero in $s = 0$.

$$
T(s) = \frac{R(s)G(s)}{1+R(s)G(s)} = \frac{N_R(s)N_G(s)}{D_R(s)D_G(s) + N_R(s)N_G(s)}
$$

is the TF for $y^\circ \to y$. $T(s)$ also has a zero in $s = 0$.

### 1.2 Zeros for MIMO Linear Systems
Define (system matrix):

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t) \\
y(t) &= Cx(t) + Du(t)
\end{aligned}
$$

within laplace transform and initial condition $x(0) = 0$, we can get:

$$
\begin{aligned}
&\begin{aligned}
sx(s) &= AX(s) + BU(s) \\
y(t) &= CX(s) + DU(s)
\end{aligned} \\
\Rightarrow&\underbrace{\begin{bmatrix} sI-A & -B \\ C & D \end{bmatrix}}_{\text{system matrix } P(s)} \begin{bmatrix} X(s) \\ U(s) \end{bmatrix} = \begin{bmatrix} 0 \\ y(s) \end{bmatrix}
\end{aligned}
$$

Define: the nominal rank of $P(s)$ is the rank of the matrix for all values of $s$ except for a finite number. 

Define (Invariant zeros of a MIMO system):

The invariant zero values of a system are the values of $s$ such that: the rank of $P(s)$ is slower than its normal rank. 

* Remark: the invariant zeros of a MIMO system satisfy the following blocking properity,
    1. If $\alpha$ is an invariant zero, then, there exists an initial state $x_0$, and a vector $u_0$, such that: given the input, $u(t) = u_0e^{\alpha t}, t \geq 0$, the output is null for any $t$.

How to compute the invariant zeros form $G(s)$:

We need to define the normal rank of $G(s)$: the rank of $G(s)$ for all values of $s$ except for a finite number.

Theorem:

Let $Z(s)$ be the polynomial whose roots are all and only the invariant zeros of the system. $Z(s)$ is called __polinomial of the invariant zeros__. Then $Z(s)$ is the greatest common divisor of all minors of order of the rank of $G(s)$ written, so that the polynomial of the poles of $\phi(s)$ at the denominator.

!!! example 

    $$
    G(s) = \frac{1}{(0.2s+1)(1+s)}\begin{bmatrix} 1 & 1 \\ 1+2s & 2 \end{bmatrix}
    $$

    * rank of $G(s)$: $r = rank(G(s)) = 2$
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

!!! example 
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

For Discreate Time MIMO Linear Systems

Same definitions for poles and invariant zeros, just $z$ in place of $s$,

$$
\begin{aligned}
P(z) &= \begin{bmatrix} zI-A & -B \\ C & D \end{bmatrix} \\
G(z) &= (z-1)\tilde G(z)
\end{aligned}
$$
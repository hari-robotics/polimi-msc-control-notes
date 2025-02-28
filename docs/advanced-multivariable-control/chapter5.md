## 5.1 LQ Problem
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
    & \Rightarrow \lambda = \frac{-1 \pm i\sqrt 3}{2}
    \end{aligned}
    $$

    The system is A.S. for $Q  = Q^T\succ 0$

    $$
    \begin{aligned}
    A^TP+PA=-Q
    \end{aligned}
    $$

    We can choose the value $Q = \mathbf I$, $P = \begin{bmatrix} P_{11} & P_{12} \\ P_{21} & P_{22}\end{bmatrix} = \begin{bmatrix} \frac32 & -\frac12 \\ -\frac12 & 1\end{bmatrix} \succ 0$

    The eigen value of $P$ is $\lambda = \frac54 \pm \frac{\sqrt 5}{4}$

    Let $V(x) = x^TPx$ is globally PD in $\bar x = 0$ and radially unbunded.

    $$
    \begin{aligned}
    \dot V(x) &= \dot x^TPx + x^TP\dot x = x^T(A^TP + PA)x = -x^TQx\\
    \dot x &= Ax + \varphi(x) -Ax \\
    \Rightarrow& \lim_{||x||\to 0}\frac{\delta \varphi(x)}{||x||} = 0
    \end{aligned}
    $$

    $$
    \begin{aligned}
    \dot V(x) &= -(x_1^2 + x_2^2) - x_1^3x_2 + 2x_1^2x_2^2
    \end{aligned}
    $$

    ND in $\bar x = 0$ but __not__ globally, $\bar x$ is A.S.

    $$
    \begin{aligned}
    \dot V(x) &= -||x||^2 + x_1 x_1x_2 (-x_1 +2x_2) \\
    &\leq -||x||^2 + |x_1| |x_1x_2| |-x_1 +2x_2| \\
    &\leq -||x||^2 + ||x|| \frac12 ||x||^2 \sqrt 5 ||x||  = -||x||^2 (1- \frac{\sqrt 5}{2}||x||^2) \\
    (|x_1|-|x_2|)^2 &= x_1^2 +x_2^2 - 2|x_1||x_2| \geq 0
    \end{aligned}
    $$

    <figure markdown="span">
        ![](pics/chapter5/figure1.HEIC){ width="400" }
    </figure>

## 5.2 Discreate Time Systems
1. The discreate form of nonlinear system is:

    $$
    x(k+1) = f(x(k), u(k)), x \in \mathbb R^n, u \in \mathbb R^n
    $$

2. The discreate form of autonomous system is:

    $$
    x(k+1) = f(x(k))
    $$

3. The discreate form of linear system is:

    $$
    x(k+1) = Ax(k) + Bu(k)
    $$

$u(k) = \bar u$, $k \geq 0$

$$
\bar x = f(\bar x, \bar u)
$$

Where $(\bar x, \bar u)$ is an equilibrium pair, for linear systems, there have:

$$
\bar x = A \bar x + B \bar u
$$

if $A$ has no eigenvalue $\lambda = 1$, $\Rightarrow$ $\bar x = -(\mathbf I - A)^{-1}B\bar u$.

Stability of $(\bar x, \bar u)$ of the equilibrium pair:

$\forall \varepsilon$, $\exists \delta > 0$, such that $\forall x_0 \in B_\delta(\bar x)$, it holds that $x_{x_0}(k) \in B_\varepsilon (\bar x)$, $\forall k \geq 0$

$(\bar x, \bar u)$ is an equlibrium pair if:

1. $(\bar x, \bar u)$ is stable
2. $\exists \delta > 0$, such that $\lim_{k\to \infty}||x_{x_0}(k)-\bar x = 0||$, $\forall x_0 \in B_\delta(\bar x)$

Remarks:

1. Stability depends on the specific equilibrium pair $(\bar x, \bar u)$
2. A.S. is a local properity

For linear systems:

1. Stability is a property of the system
2. A.S. $\Leftrightarrow$ G.A.S.

A N&S condition for a linear system to be A.S. is that all eigenalues of $A$ satisfy $|\lambda| < 1$

<figure markdown="span">
    ![](pics/chapter5/figure2.HEIC){ width="400" }
</figure>

Linearization:

$$
x(k+1) = f(x(k), u(k)), f \in C^1
$$

$(\bar x, \bar u)$ is an equilibrium pair

$$
\delta x(k+1) = A\delta x(k) + B\delta u(k)
$$

$A = \frac{\partial f}{\partial x}|_{x=\bar x, u=\bar u}$, $B = \frac{\partial f}{\partial u}|_{x=\bar x, u=\bar u}$

* if all eigenvalues of $A$ have $|\lambda| < 1$ $\Rightarrow$ $(\bar x, \bar u)$ is A.S.
* if $\exists$ an eigenvalue of $A$ have $|\lambda| > 1$ $\Rightarrow$ $(\bar x, \bar u)$ is unstable
* if all eigenvalues of $A$ have $|\lambda| \leq 1$ and $\exists$ one with $|\lambda = 1|$ $\Rightarrow$ could not tell the stability

## 5.3 Lyapunov Method for Discreate System
$$
x(k+1) = \varphi(x(k))
$$

$\bar x$ is an equlibrium that $\bar x = \varphi (\bar x)$, $\varphi$ is lipschitz

* if $\exists V$ that is continous and PD in $\bar x$ such that $\Delta V(x) = V(\varphi(x)) - V(x)$ is NSD in $\bar x$ 
    
    $\Rightarrow$ $\bar x$ is stable

* if $\Delta V(x)$ is ND in $\bar x$ 

    $\Rightarrow$ $\bar x$ is A.S.

* if $\exists V$ that is continous, and radially unbounded, globally PD in $\bar x$, such that $\Delta V(x)$ is globally ND in $\bar x$

    $\Rightarrow$ $\bar x$ is G.A.S

Krasowski - La Salle Theorem:

Suppose $\exists V$ that is continous and PD in $\bar x$ on the neighbor of $D$ of $\bar x$, such that $\Delta V$ is NSD in $\bar x$ on $D$.

If the set:

$$
S = \{x\in D: \Delta V(x) = 0\}
$$

does not contain any perturbed trajectory of the system, then $\bar x$ is A.S.

Note if $D=\mathbb R^n$ and $V$ is radially unbounded, then $\bar x$ is G.A.S.

For a discreate linear system

The N&S condition of the A.S. of the system is that $\forall Q = Q^T \succ 0$, $\exists P = P^T \succ 0$ satisfying

$$
A^TPA - P = -Q
$$

Proof (Succficiency): 

$\bar u = 0 \to \bar x = 0$, $Q\succ0 \to P \succ 0$

$$
\begin{aligned}
V(x) = x^TPx \\
\delta V(x) = \underbrace{(Ax)^TP(Ax)}_{V(\dot \varphi(x))} - \underbrace{x^TPx}_{V(x)} = -x^TQx
\end{aligned}
$$

is ND in $\bar x$

## 5.4 Control Design via Lyapunov Theory

!!!abstract "Example"
    $$
    \left\{\begin{aligned}
    \dot x_1 &= -3 x_1 + 2x_1 x_2^2 + u \\
    \dot x_2 &= -x_2^3 - x_2
    \end{aligned}\right.
    $$

    Design $u = k(x_1, x_2)$ such that $\bar x$ is G.A.S.

    $$
    V(x) = \frac12 (x_1^2 + x_2^2)
    $$ 

    is globally PD in $\bar x = 0$ and radially unbounded

    $$
    \begin{aligned}
    \dot V(x) &= x_1\dot x_1 + x_2 \dot x_2 \\
    &= -3x_1^2 +2x_1^2x_2^2 + x_1u - x_2^4 - x_2^2 \\
    \end{aligned}
    $$

    To make $\dot V$ ND, one possiable choice is $u = -2x_1x_2^2$, hence,

    $$
    \dot V(x) = -3x_1^2 -x_2^2 - x_2^4
    $$

    is globally ND in $\bar x = 0$. $\Rightarrow$ $\bar x = 0$ is a G.A.S. equilibrium for the closed loop system.

## 5.5 Back-stepping Method
$$
\begin{aligned}
\dot x_1(t) &= f(x_1(t)) + g(x_1(t)) x_2(t), x_1 \in \mathbb R^n \\
\dot x_2(t) &= u(t)
\end{aligned}
$$

* $f$, $g$ $\in C^1$ on the neighbor of $D$ of $\bar x_1 = 0$
* $f(x) = 0$

Goal: design $u = k(x_1, x_2)$ such that $\bar x = 0$ is an A.S. equilibrium for the closed loop system

suppose that you know a  "fictitious" control law: $x_2 = \Phi(x_1)$ such that $\Phi$ is smooth and $\Phi(0) = 0$ and $\bar x_1 = 0$ is an A.S. equilibrium of $\dot x_1 = f(x_1)g(x_1)\Phi(x_1)$, with $V_1(x_1) \in C^1$ is PD in $\bar x = 0$, such that, 

$$
\dot V_1(x_1) = \frac{\partial V_1}{x_1}\left[ f(x_1)+g(x_1)\Phi(x_1) \right]
$$

is ND in $\bar x = 0$ on $D$, then the control law is:

$$
u = - \frac{\partial V_1}{\partial x_1}(x_1)g(x_1) - \mu(x_2 - \Phi(x_1)) + \frac{\partial \Phi}{\partial x_1}(x_1)(f(x_1) + g(x_1)x_2), \mu > 0
$$

is A.S. for $\bar x = 0$.

Proof:

$$
V(x_1, x_2) = V_1(x_1) + \frac12 (x_2 - \Phi(x_1))^2
$$

Extension:

$$
\begin{aligned}
\dot x_1(t) &= f(x_1(t)) + g(x_1(t)) x_2(t), x_1 \in \mathbb R^n \\
\dot x_2(t) &= a(x_1,x_2) + b(x_1,x_2)u(t)
\end{aligned}
$$

If $b(x_1,x_2) \neq 0$ is on the domain of interest,

$$
\begin{aligned}
u(t) &= -\frac{1}{b(x_1,x_2)}(a(x_1,x_2)-v) \\
\dot x_2 &= v
\end{aligned}
$$

$v = k(x_1,x_2)$, by backsteppings

## 5.6 Feedback Linearization
$$
\begin{aligned}
\dot x_1 &= A_1x_1 + A_2x_2 \\
\dot x_2 &= a(x_1,x_2) + b(x_1,x_2)u(t)
\end{aligned}
$$

$u = -\frac{1}{b(x_1,x_2)}(a(x_1,x_2)-v)$, $b(x_1,x_2) \neq 0, \forall (x_1, x_2)$, $\dot x_2 = v$, $v = Kx$
## 7.1 Control Design via Lyapunov Theory

!!! example
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

    $V(\bar x) \succ 0, \forall \bar x$, and $V \in \mathbb R^n \to \mathbb R$

    $$
    \begin{aligned}
    \dot V(x) &= x_1\dot x_1 + x_2 \dot x_2 \\
    &= -3x_1^2 +2x_1^2x_2^2 + x_1u - x_2^4 - x_2^2 \\
    \end{aligned}
    $$

    To make $\dot V$ ND, one possible choice is $u = -2x_1x_2^2$, hence,

    $$
    \dot V(x) = -3x_1^2 -x_2^2 - x_2^4
    $$

    is globally ND in $\bar x = 0$. $\Rightarrow$ $\bar x = 0$ is a G.A.S. equilibrium for the closed loop system.

## 7.2 Back-stepping Method
Given the system with the form:

$$
\begin{aligned}
\dot x_1(t) &= f(x_1(t)) + g(x_1(t)) x_2(t), x_1 \in \mathbb R^n \\
\dot x_2(t) &= u(t)
\end{aligned}
$$

* $f$, $g$ $\in C^1$ on the neighbor $D$ of $\bar x_1 = 0$
* $f(0) = 0$

Goal: design $u = k(x_1, x_2)$ such that $\bar x = 0$ is an A.S. equilibrium for the closed loop system

### 7.2.1 Controller Design
Suppose that you know a "fictitious" control law: 

$$
x_2 = \Phi(x_1), \Phi(x) \in C^\infty, \Phi(0) = 0
$$

$\bar x_1 = 0$ is an A.S. equilibrium of the reduced order system:

$$
\dot x_1 = f(x_1) + g(x_1)\Phi(x_1)
$$

give $V_1(x_1) \in C^1, V_1(\bar x) \succ 0$ for $\bar x = 0$ such that, 

$$
\dot V_1(x_1) = \frac{\partial V_1}{\partial x_1}\left[ f(x_1)+g(x_1)\Phi(x_1) \right]
$$

$\dot V_1(x_1) \prec 0$ in $\bar x = 0$ on $D$, then the control law is:

$$
u = - \frac{\partial V_1}{\partial x_1}(x_1)g(x_1) - \mu(x_2 - \Phi(x_1)) + \frac{\partial \Phi}{\partial x_1}(x_1)(f(x_1) + g(x_1)x_2), \mu > 0
$$

is A.S. for $\bar x = 0$.

### 7.2.2 Proof
$$
V(x_1, x_2) = V_1(x_1) + \frac12 (x_2 - \Phi(x_1))^2
$$

### 7.2.3 Extension
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

$v = k(x_1,x_2)$, by back-stepping

## 7.3 Feedback Linearization
$$
\begin{aligned}
\dot x_1 &= A_1x_1 + A_2x_2 \\
\dot x_2 &= a(x_1,x_2) + b(x_1,x_2)u(t)
\end{aligned}
$$

$u = -\frac{1}{b(x_1,x_2)}(a(x_1,x_2)-v)$, $b(x_1,x_2) \neq 0, \forall (x_1, x_2)$, $\dot x_2 = v$, $v = Kx$
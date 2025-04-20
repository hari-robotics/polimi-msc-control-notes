First we introduce some form of discrete systems:

1. Nonlinear system: $x(k+1) = f(x(k), u(k)), x \in \mathbb R^n, u \in \mathbb R^n$
2. Autonomous system: $x(k+1) = f(x(k))$
3. Linear system: $x(k+1) = Ax(k) + Bu(k)$

### 6.1 Equilibrium of Linear Systems
Let $u(k) = \bar u$, $k \geq 0$, $\bar x = f(\bar x, \bar u)$, where $(\bar x, \bar u)$ is an equilibrium pair, for linear systems, we have:

$$
\bar x = A \bar x + B \bar u
$$

* if $A$ has no eigenvalue $\lambda = 1$, $\Rightarrow$ $\bar x = -(\mathbf I - A)^{-1}B\bar u$.

### 6.2 Stability of Linear Systems
Consider the stability of $(\bar x, \bar u)$ of the equilibrium pair:

* $\forall \varepsilon$, $\exists \delta > 0$, such that $\forall x_0 \in B_\delta(\bar x)$, it holds that $x_{x_0}(k) \in B_\varepsilon (\bar x)$, $\forall k \geq 0$

$(\bar x, \bar u)$ is an equilibrium pair if:

1. $(\bar x, \bar u)$ is stable
2. $\exists \delta > 0$, such that $\lim_{k\to \infty}||x_{x_0}(k)-\bar x = 0||$, $\forall x_0 \in B_\delta(\bar x)$

!!! quote
    1. Stability depends on the specific equilibrium pair $(\bar x, \bar u)$
    2. A.S. is a local property

    For linear systems:

    1. Stability is a property of the system
    2. A.S. $\Leftrightarrow$ G.A.S.

A N&S condition for a linear system to be A.S. is that all eigenvalues of $A$ satisfy $|\lambda| < 1$

<figure markdown="span">
    ![](pics/chapter5/figure2.HEIC){ width="400" }
</figure>

### 6.3 Stability of Nonlinear Systems
Consider a nonlinear system $x(k+1) = f(x(k), u(k)), f \in C^1$, $(\bar x, \bar u)$ is an equilibrium pair, we can do linearization for this system:

$$
\delta x(k+1) = A\delta x(k) + B\delta u(k)
$$

Where, $A = \frac{\partial f}{\partial x}|_{x=\bar x, u=\bar u}$, $B = \frac{\partial f}{\partial u}|_{x=\bar x, u=\bar u}$. $\lambda$ is the eigenvalue of matrix $A$, the stability can be judged in following conditions:

* $|\lambda_i| < 1, \forall \lambda_i \in \lambda$ $\Rightarrow$ $(\bar x, \bar u)$ is A.S.
* $\exists |\lambda_i| > 1, \lambda_i \in \lambda$ $\Rightarrow$ $(\bar x, \bar u)$ is unstable
* $|\lambda_i| \leq 1, \forall \lambda_i \in \lambda$ and $\exists |\lambda_j| = 1, \lambda_j \in \lambda$ $\Rightarrow$ could not tell the stability

### 6.4 Lyapunov Methods
Considering the perturbance of the discrete system:

$$
x(k+1) = \varphi(x(k))
$$

$\bar x$ is an equilibrium, $\bar x = \varphi (\bar x)$, $\varphi$ is Lipchitz, $\Delta V(x) = V(\varphi(x)) - V(x)$

* if $\exists V, V \in C^1, V(\bar x) \succ 0$, and $\Delta V(\bar x) \preceq 0$ $\Rightarrow$ $\bar x$ is stable
* if $\Delta V(\bar x) \prec 0$ $\Rightarrow$ $\bar x$ is A.S.
* if $\exists V, V \in C^1, V \in \mathbb R^n \to \mathbb R$, and $V(\bar x) \succ 0, \Delta V(\bar x) \prec 0, \forall \bar x$ $\Rightarrow$ $\bar x$ is G.A.S

### 6.5 Krasowski - La Salle Theorem:

Suppose $\exists V, V(\bar x) \succ 0, \Delta V(\bar x) \preceq 0, \bar x \in D$, if the set: $S = \{x\in D: \Delta V(x) = 0\}$ does not contain any perturbed trajectory of the system, $\Rightarrow$ $\bar x$ is A.S.

!!!note
    if $D=\mathbb R^n$ and $V \in \mathbb R^n \to \mathbb R$ $\Rightarrow$ $\bar x$ is G.A.S. for the above condition

* For a discrete linear system, the N&S condition of the A.S. of the system is that $\forall Q = Q^T \succ 0$, $\exists P = P^T \succ 0$ that satisfying

$$
A^TPA - P = -Q
$$

!!! info

    Proof (Sufficiency): 

    $\bar u = 0 \to \bar x = 0$, $Q\succ0 \to P \succ 0$

    $$
    \begin{aligned}
    V(x) &= x^TPx \\
    \delta V(x) &= \underbrace{(Ax)^TP(Ax)}_{V(\dot \varphi(x))} - \underbrace{x^TPx}_{V(x)} = -x^TQx
    \end{aligned}
    $$

    $\Delta V(\bar x) \prec 0$
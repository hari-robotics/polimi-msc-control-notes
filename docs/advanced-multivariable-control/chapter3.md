# 3. Linearization and Stability of Nonlinear Systems
From last part, we have known how to define the stability of linear systems, for solving the stability question of nonlinear systems, we could apply the linearization to the nonlinear systems,

$$
\dot x(t) = f(x(t), u(t)), x \in \mathbb R^n, u \in \mathbb R^m \Rightarrow \dot x(t) = Ax(t) + Bu(t)
$$

## 3.1 Linearization
We know that for a linear system, 
* Stability is a properity of the system
* The system is A.S. if and only if all the eigenvalues of its dynamic matrix $A$ have negative real parts

So for defining the stability of nonlinear systems, the idea is how to convert it into a linear system. Giving the nonlinear system of the following form:

$$
\dot x(t) = f(x(t), u(t))
$$

Assumed that $f \in C^1$, $(\bar x, \bar u)$ is an equilibrium pair if $\varphi(\bar x, \bar u) = 0$. Now we assume at time $t$, there exists small perturbance close to the equilibrium pair:

$$
\begin{aligned}
\delta u(t) &= u(t) - \bar u\\
\delta \dot x(t) &= A\delta x (t) + B\delta u(t)\\
\end{aligned}
$$

Where $A = \frac{\delta f}{\delta x}|_{x=\bar x, u = \bar u}, B = \frac{\delta f}{\delta u}|_{x=\bar x, u = \bar u}$. As long as the perturbance is small enough, $A = \frac{\partial f}{\partial x}|_{x=\bar x, u = \bar u}, B = \frac{\partial f}{\partial u}|_{x=\bar x, u = \bar u}$. Which indicates $A$ and $B$ is the Jacobian of the of the point $(\bar x, \bar u)$.

Now the stability of the linearized model can be conclude as:

1. if $A$ has all __eigenvalues with negative real part__ ($\lambda_i < 0$, in this condition, we also called $A$ is __negative definite__ (ND)), then $(\bar x, \bar u)$ is A.S.
2. if $\exists \lambda_i > 0$, then $(\bar x, \bar u)$ is unstable
3. if $\forall \lambda_i \leq 0$, and $\exists \lambda_j = 0$, the stability cannot be defined unless more information were given

About point 3 above, we can introduce an example to explain this:
!!!abstract "Example"
    $$
    \dot x(t) = x(t)\cdot u(t)
    $$

    | $u = 1, t\geq 0$ | $u = -1, t\geq 0$ |
    |------------------|-------------------|
    |$\begin{aligned}x &= x^3(t)\\ \bar x &= 0 \Rightarrow (\bar x, \bar u) = (0,1) \end{aligned}$|$\begin{aligned}x &= -x^3(t)\\ \bar x &= 0 \Rightarrow (\bar x, \bar u) = (0,-1) \end{aligned}$|
    | $A = [3\bar x ^2 \bar u] = 0$, $B = [0]$ | $A = [3\bar x ^2 \bar u] = 0$, $B = [0]$ |
    | ![](pics/chapter3/figure1.png){ height="160" } | ![](pics/chapter3/figure2.png){ height="160" } |

!!!warning
    if $f$ is not continues, then it is not linearizable.
    
    !!!abstract "Example"
        $\dot x = |x|$ is not linearizable

Limitation of the linearization approach is:

1. It requires $f \in C^1$
2. If $A$ is __semi-negative definite__ (SND), then no conclusion can be made to the stability analysis
3. If $(\bar x, \bar u)$ is A.S., the domain of attraction is still unknown.

!!!abstract "Example"
    $$
    \dot x(t) = -x(t) +x^2(t) +u(t)
    $$

    Let $u(t) = 0$, at $t \geq 0$,

    $$
    -\bar x +\bar x^2 = 0 \Rightarrow \left\{\begin{aligned} 
    \bar x = 0 \\
    \bar x = 1
    \end{aligned}\right.
    $$

    For $(\bar x, \bar u) = (0,0)$, $\delta \dot x(t) = -\delta x(t) + \delta u(t)$,
    $\lambda = -1 < 0$, the system at $(0,0)$ is A.S.

    <figure markdown="span">
        ![](pics/chapter3/figure3.png){ width="200" }
    </figure>

## 3.2 Phase Portait for 2nd Order Systems
For the system:

$$
\dot x (t) = Ax(t), \bar x = 0
$$

Where $A$ is diagonalizable with pure real eigenvalues, $\exists a_1, a_2, T$, $det(T) \neq 0$, $a_1 \neq a_2$, satisfy $TAT^{-1} = \begin{bmatrix} a_1 & 0 \\ 0 & a_2\end{bmatrix}$, let

$$
\begin{aligned}
&z = Tx \\
\Rightarrow &\dot z(t) = \begin{bmatrix}
a_1 & 0 \\
0 & a_2
\end{bmatrix}z(t) \\
\Rightarrow & \left\{\begin{aligned}
z_1(t) &= e^{a_1 t}z_1(0)\\
z_2(t) &= e^{a_2 t}z_2(0)
\end{aligned}\right.
\end{aligned}
$$

This converts $a_1$, $a_2$ to real eigen vectors $z_1$, $z_2$

<figure markdown="span">
    ![](pics/chapter3/figure4.png){ width="600" }
    ![](pics/chapter3/figure5.png){ width="320" }
</figure>


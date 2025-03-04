__Ex.1__ Given the continues system

$$
\left\{\begin{aligned}
\dot x_1 &= -x_1 + x_2^2 \\
\dot x_2 &= -x_2
\end{aligned}\right.
$$

Show that,

1. the $(\dot x_1, \dot x_2) = (0,0)$ is an equilibriym point
    
    !!!note "Answer"
        Let $(\dot x_1, \dot x_2) = (0,0)$, we can get:

        $$
        \left\{\begin{aligned}
        \dot 0 &= -x_1 + x_2^2 \\
        \dot 0 &= -x_2
        \end{aligned}\right.
        $$

        $\Rightarrow$ $x_2 = 0$, $x_1 = 0$, (0,0) is an equilibriym point.

2. and study its stability through the linearized system

    !!!note "Answer"
        Linearize the system: $\delta \dot x = A \delta x$, where, $A = \frac{\partial f}{\partial x}|_{\bar x}$

        $$
        \begin{bmatrix}
        \delta \dot x_1\\ \delta \dot x_2
        \end{bmatrix} = \begin{bmatrix}
        -1 & 0 \\
        0 & -1
        \end{bmatrix} \begin{bmatrix}
        \delta x_1\\ \delta x_2
        \end{bmatrix}
        $$

        $\lambda_{1,2} = -1$, The system is A.S. at equilibrium point $(0,0)$.

        !!! warning
            1. $s < 0 \Rightarrow$, locally A.S. at equilibrium point
            2. $s < 0, \exists s = 0$, no conclusion
            3. $\exists s > 0$, unstable

Given the function $V(x) = \frac12(x_1^2 +x_2^2)$,

3. Check that it is in fact a suitable Lyapunov function

    !!!note "Answer"
        1. The function is PD
        2. The function is continous
        3. Radially unbounded

        $V(x) \succ 0$, $V(x) \in C^1$, $||V|| \in \mathbb R^n \to \mathbb R^n$, so it is a suitable Lyapunov function.

4. and study the stability of the system with the given function

    !!!note "Answer"
        $$
        \begin{aligned}
        \dot V(x) &= x_1 \dot x_1 + x_2 \dot x_2 \\
        &= x_1 (-x_1 + x_2^2) + x_2(-x_2) \\
        &= -x_1^2 -x_2^2 + x_1x_2^2
        \end{aligned}
        $$

        From above equation, we cannot say the stability of the system, to find the stability, we can make an approximation near the equilibrium point,

        $$
        \begin{aligned}
        \dot V(x) &\approx -x_1^2 - x_2^2 + \vartheta(\bar x^3) \\
        &\approx -x_1^2 - x_2^2
        \end{aligned}
        $$

        The system is A.S. near the equilibrium point. This conclusion has no difference with the linearization method, to get the region of attraction, we can let:

        $$
        \dot V(x) = -x_1^2 + x_2^2(1 - x_1)
        $$

        if $x_1 \leq 1$, $\dot V(x) < 0$

        $$
        D = \{(x_1, x_2)\in \mathbb R | x_1 < 1 \}
        $$

        !!! extension
        We can add the initial state into the system,

        $$
        \begin{aligned}
        x_1(t) &= x_1(0)e^{-\tau} + (x_2(0)e^{-\tau})^2 \\
        x_2(t) &= x_2(0)e^{-\tau}
        \end{aligned}
        $$
        
        $$
        \begin{aligned}
        x_1(t) &= x_1(0)e^{-\tau} + \int_0^tV(\tau)e^{t-\tau}dt \\
        x_2(t) &= x_2(0)e^{-\tau}
        \end{aligned}
        $$

        $$
        \begin{aligned}
        x_1(t) &= x_1(0)e^{-t} + (e^{-t}-e^{-2t})(x_2(0))^2 \\
        x_2(t) &= x_2(0)e^{-t}
        \end{aligned}
        $$

        if $t \to +\infty$, $e^{-t} \to 0$, $e^{-2t} \to 0$, $x_1(+\infty) = 0, x_2(+\infty) = 0$, the system is G.A.S.

__Ex. 2__: Given the following parametric system

$$
\left\{\begin{aligned}
\dot x_1 &= x_1(k^2 - x_1^2 - x_2^2) + x_2(k^2 + x_1^2 + x_2^2)\\
\dot x_2 &= -x_1(k^2 + x_1^2 + x_2^2) + x_2(k^2 - x_1^2 - x_2^2)\\
\end{aligned}\right.
$$

and the function $V(x) = \frac12(x_1^2 + x_2^2)$,

1. Check that V(x) is a Lyapunov function,

2. study the stability of the origin of the system for $k = 0$

3. and for $k \neq 0$

    !!! note "Answer"
        $$
        \begin{aligned}
        \dot V(x) &= x_1 \dot x_1 + x_2 \dot x_2 \\
        &= x_1^2(k^2 - x_1^2 - x_2^2) + x_1x_2(k^2 + x_1^2 + x_2^2) - x_1x_2(k^2 + x_1^2 + x_2^2) + x_2^2(k^2 - x_1^2 - x_2^2) \\
        &= (x_1^2+x_2^2)(k^2 - x_1^2 - x_2^2)
        \end{aligned}
        $$

        1. if $k=0$, $\dot V(x) \leq 0$, the system is G.A.S.

        2. if $k\neq 0$, $k^2 - x_1^2 - x_2^2 < 0$, $k^2 < x_1^2 + x_2^2$, the system is A.S. and the region of attraction is the area outside of the circle $K^2 = x_1^2 + x_2^2$. Inside the circle, the system is unstable.

__Ex. 3__: Given the continuous time system

$$
\left\{\begin{aligned}
\dot x_1 &= x_2\\
\dot x_2 &= -x_2 - \alpha x_1 - (x_1^2 + x_2^2)x_2
\end{aligned}\right.
$$

with $\alpha > 0$ and the function $V(x) = \alpha x_1^2 + x_2^2$,

1. Check that $V(x)$ is a Lyapunov function,
2. study the stability of the origin of the system
3. and characterize the trajectories of the state around the origin (linearized system’s eigenvalues)

    !!!note "Answer"

        $$
        \begin{aligned}
        \dot V(x) &= 2\alpha x_1 \dot x_1 + 2x_2 \dot x_2 \\
        &= 2\alpha x_1 x_2 + 2 x_2 \left[ -x_2 - \alpha x_1 - (x_1 + x_2)^2 x_2 \right] \\
        &= -2x_2^2 (1 + (x_1 +x_2)^2)
        \end{aligned}
        $$

        $\dot V(x) = 0, \forall x_1$, when $x_2 = 0$
        
        KLS: $x_2 = 0$,

        $$
        \left\{\begin{aligned}
        \dot x_1 &= 0\\
        \dot x_2 &= -0 - \alpha x_1 - 0
        \end{aligned}\right.
        $$

        $\dot x_2 = 0$ if and only if when $x_1 = 0$, the system is G.A.S.

        Use the linearization method, the linearized system is:
        
        $$
        \begin{aligned}
        \delta \dot x_1 = \delta x_2 \\ 
        \delta \dot x_2 = \alpha \delta x_1 - \delta x_2
        \end{aligned}
        $$

        $A = \begin{bmatrix} 0&1\\ -\alpha & -1 \end{bmatrix}$, $det(A - s\mathbf I) = 0$,

        $$
        s_{1,2} = \frac{-1 \pm \sqrt{1-4\alpha}}{\alpha}
        $$

        1. $1-4\alpha < 0$, $\Rightarrow$ A.S. with complex conjugate eigenvalues
        2. $1-4\alpha > 0$, 
            * $\alpha = 0$, $s_1 = -1$, $s_2 = 0$
            * $\alpha \neq 0$, $s_1 < s_2 < 0$, $\Rightarrow$ A.S. with real eigenvalues.

__Ex. 4__: Given the following discrete time system

$$
\left\{\begin{aligned}
x_1(k+1) &= x_2(k) \cos(x_1(k))\\
x_2(k+1) &= x_1(k) \cos(x_2(k))
\end{aligned}\right.
$$

1. Study the stability of the origin of the linearized system,

    !!! note "Answer"

        $$
        \begin{aligned}
        &\left\{\begin{aligned}
        \delta x_1(k+1) &= - \bar x_2 \sin(\bar x_1) \delta x_1(k) + \cos(\bar x_1) \delta x_2(k)\\
        \delta x_2(k+1) &= \cos(\bar x_2) \delta x_2(k) + (-\bar x_1 \sin(\bar x_2)) \delta x_2(k)
        \end{aligned}\right. \\
        \Rightarrow &\left\{\begin{aligned}
        \delta x_1(k+1) &= \delta x_2(k)\\
        \delta x_2(k+1) &= \delta x_1(k)
        \end{aligned}\right.
        \end{aligned}
        $$

        $A = \begin{bmatrix} 0&1\\1&0 \end{bmatrix}$, $det(-A+z\mathbf I) = 0$, $z^2 -1 = 0$, $z_{1,2} = \pm 1$, we cannot get any conclusion from the linearization.

2. Use the following Lyapunov function to study the stability of the system, $V(x) = x_1^2(k) + x_2^2(k)$,

    !!!note "Answer"
        $$
        \begin{aligned}
        \Delta V(x) &= V(x(k+1)) - V(x(k))\\
        &= (x_2(k)\cos(x_1(k)))^2 + (x_1(k)\cos(x_2(k)))^2 - x_1^2(k) - x_2^2(k) \\
        &= -x_1^2\sin^2(x_2) - x_2^2 \sin^2(x_1) \leq 0
        \end{aligned}
        $$

        if $x_1 = 0$, $\Delta V = 0, \forall x_2$,

        if $x_2 = 0$, $\Delta V = 0, \forall x_1$,

        * Case 1:

            $$
            \left\{\begin{aligned}
            x_1(0) &= 0 \\
            x_2(0) &= \bar x_2
            \end{aligned}\right.
            $$

            We take one step forward,

            $$
            \left\{\begin{aligned}
            x_1(1) &= \bar x_2 \\
            x_2(1) &= 0
            \end{aligned}\right. \to \left\{\begin{aligned}
            x_1(2) &= 0 \\
            x_2(2) &= \bar x_2
            \end{aligned}\right.
            $$

            The system is stable but not A.S.,

        * Case 2:

            $$
            \left\{\begin{aligned}
            x_1(0) &= \bar x_1 \\
            x_2(0) &= 0
            \end{aligned}\right. \to \left\{\begin{aligned}
            x_1(1) &= 0 \\
            x_2(1) &= \bar x_1
            \end{aligned}\right.
            $$

            The system is also only stable but not A.S.

__Ex. 8__: Given the following system

$$
\left\{\begin{aligned}
\dot x_1(t) &= -x_1^3 + x_2 \\
\dot x_2(t) &= x_2^2 + u
\end{aligned}\right.
$$

and the Back-stepping formula (given at the exam)

$$
u = - \frac{dV_1(x_1)}{dx_1} g_1 (x_1) - k(x_2 - \phi(x_1)) + \frac{\phi(x_1)}{dx_1}(f_1(x_1) + g_1(x_1)x_2)
$$

Determine a control law stabilizing the origin using the Back-stepping method.

!!!note "Answer"

    Backstepping can be applied to the system with the form:

    $$
    \left\{\begin{aligned}
    \dot x_1 &= f_1(x_1) + g_1(x_1)x_2 \\
    \dot x_2 &= u
    \end{aligned}\right.
    $$

    We cannnot apply the backstepping to the system directly, but we can apply the extended backstepping to the system, the extended backstepping have the form:

    $$
    \left\{\begin{aligned}
    \dot x_1 &= f_1(x_1) + g_1(x_1)x_2 \\
    \dot x_2 &= f_2(x_1, x_2) + g(x_1, x_2) u
    \end{aligned}\right.
    $$

    In this system, we have:

    * $f_1 = x_1^3$, $g_1 = 1$,
    * $f_2 = x_2^2$, $g_2 = 1$

    With the change of varibale,

    $$
    u_a = f_2 + g_2 u
    $$

    The system becomes:

    $$
    \left\{\begin{aligned}
    \dot x_1 &= f_1(x_1) + g_1(x_1)x_2 \\
    \dot x_2 &= u_a
    \end{aligned}\right.
    $$


    For the system above, we have:
    
    $$
    u_a = x_2^2 + u
    $$

    To design the parameter,

    1. 

        $$
        \begin{aligned}
        &\phi(x_1): x_2 = \phi(x_1) | \phi(0) = 0 \\
        &\phi(x_1) = -\gamma x_1, \gamma > 0
        \end{aligned}
        $$

    2. 

        $$
        \begin{aligned}
        V_1(x_1) &= \frac12 x_1^2 \\
        \dot V_1(x_1) &= -x_1^4 - \gamma x_1^2
        \end{aligned}
        $$

        and $u_a = -x_1 - k\gamma x_1 + \gamma x_1^3 -kx_2 - \gamma x_2$,
        $u(t) = u_a - x_2^2$, is G.A.S in $(0,0)$

    |Pros|Cons|
    |---|---|
    |G.A.S|No guarantees for the performance|
    ||$\phi$, $V$ is hard to design|
    ||Requests a good model|
    ||Need to care about saturation problem|
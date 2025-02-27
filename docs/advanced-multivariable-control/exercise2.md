Ex.1 Given the continues system

$$
\left\{\begin{aligned}
\dot x_1 &= -x_1 + x_2^2 \\
\dot x_2 &= -x_2
\end{aligned}\right.
$$

Show that,

1. the $(\dot x_1, \dot x_2) = (0,0)$ is an equilibriym point
    
    !!!experiment "Answer"
        Let $(\dot x_1, \dot x_2) = (0,0)$, we can get:

        $$
        \left\{\begin{aligned}
        \dot 0 &= -x_1 + x_2^2 \\
        \dot 0 &= -x_2
        \end{aligned}\right.
        $$

        $\Rightarrow$ $x_2 = 0$, $x_1 = 0$, (0,0) is an equilibriym point.

2. and study its stability through the linearized system

    !!!experiment "Answer"
        Linearize the system: $\dot x = Ax$, where, $A = \frac{\partial f}{\partial x}$

        $$
        \begin{bmatrix}
        \dot x_1\\ \dot x_2
        \end{bmatrix} = \begin{bmatrix}
        0 & 2 \\
        0 & 0
        \end{bmatrix} \begin{bmatrix}
        x_1\\ x_2
        \end{bmatrix} + \begin{bmatrix}
        -1 \\
        -1
        \end{bmatrix}
        $$
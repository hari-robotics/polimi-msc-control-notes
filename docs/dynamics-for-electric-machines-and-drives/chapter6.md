## 1. Review on Phase Vector

From last part, we already get the expression of flux density in a 3 phase machine, giving the current:

$$
\begin{aligned}
i_a &= I_m \cos(\omega t) \\
i_b &= I_m \cos(\omega t - \frac23 \pi) \\
i_c &= I_m \cos(\omega t + \frac23 \pi)
\end{aligned}
$$

The flux density is:

$$
\begin{aligned}
\bar B &= \frac{4}{\pi} \frac{N}{2\delta}(i_ae^{j0} + i_be^{j\frac23\pi} + i_ce^{j(-\frac23\pi)}) \\
&= \frac{4}{\pi} \frac{N}{2\delta} \underbrace{(\frac32 I_me^{j\omega t})}_{\bar i}
\end{aligned}
$$

Thus, we have: $\bar B = k \bar i$, where $\bar i$ is the current space vector. We let $\alpha = e^{j\frac23\pi}$, and we have the expression for $\bar i$:

$$
\bar i = i_a + \alpha i_b + \alpha^2 i_c
$$

And we can also do the same thing to the 3 phase voltage,

$$
\bar v = (v_a + \alpha v_b + \alpha^2 v_c)
$$

## 2. Clarke-Park Transform

### 2.1 Clarke Transform
By obtainning the current vector, we can simplify the 3 phase machine into 2 phase representation,

<figure markdown="span">
    ![](pics/chapter6/figure1.png){ width="400" }
</figure>

And we have:

$$
\bar i = i_\alpha + j i_\beta
$$

And we can also convert it back to 3 phase current:

$$
\begin{aligned}
i_a &= \frac23 \Re(\bar i e^{j0}) \\
i_b &= \frac23 \Re(\bar i e^{-j\frac23\pi}) \\
i_c &= \frac23 \Re(\bar i e^{j\frac23\pi}) \\
\end{aligned}
$$

This conversion is called (inverse) clarke transform, with $i_a$, $i_b$ and $i_c$ have a equal amplitude to the real phase current. 

!!! bug
    For the 3 phase current with 120 degree phase shift, we can get:

    $$
    \begin{aligned}
    \bar B_{tot} &= \bar B_a + \bar B_b + \bar B_c \\
    &= \frac{4}{\pi} (i_a e^{j0} + i_b e^{j\frac23 \pi} + i_c e^{j \frac43 \pi}) \\
    &= k \bar i
    \end{aligned}
    $$

    Where $i_a = I_{m} \cos(\omega t)$, $\bar i = \frac32 I_{m} e^{j\omega t}$

    Thus the current generated flux density that will rotate in the speed of $\omega$. The sum current and phase current have the following relationship: 

    $$
    i_a = \frac23 Re(\bar i e^{j0})
    $$

    Similarly, we can have the space vectors for the voltage,

    $$
    \bar v = (v_a\angle0 + v_b\angle \frac23 \pi + v_c \angle \frac43 \pi)
    $$

    The more commonly used conversion is the same energy conversion,

    $$
    \begin{aligned}
    \bar i = \sqrt{\frac23} \frac32 I_{m}e^{j\omega t} \\
    \bar v = \sqrt{\frac23} \frac32 V_{m}e^{j\omega t}
    \end{aligned}
    $$

    So that, the power is:

    $$
    P = Re(\bar v \bar i) = 3V_{m}I_{m}
    $$

    Between stator and the rotor, we have the angle difference $\theta_m$,

    we can use the matrix form to represent the electrical machine dynamics:

    $$
    \begin{aligned}
    \begin{bmatrix}
    v_a \\ v_b \\ v_c
    \end{bmatrix} = \mathbf R \begin{bmatrix}
    i_a \\ i_b \\ i_c
    \end{bmatrix} + \frac{d}{dt} \begin{bmatrix}
    \psi_a \\ \psi_b \\ \psi_c
    \end{bmatrix}
    \end{aligned}
    $$

    Where $\mathbf R$ is the resistance matrix.

    And we can rotate the matrix within rotating matrix $\sqrt{\frac{2}{3}} \begin{bmatrix} 1 & \alpha & \alpha^2 \end{bmatrix}$, and we have:

    $$
    \begin{aligned}
    \bar v_s^s &= R_s \bar i_s^s + \frac{d}{dt} \bar \psi_s^s \\
    \bar v_R^R &= R_R \bar i_s^R + \frac{d}{dt} \bar \psi_R^R
    \end{aligned}
    $$

    And this results in a DC like expression:

    $$
    \begin{aligned}
    v_{sd} = Ri_{sd} + \frac{d}{dt} \psi_{sd} \\
    v_{sq} = Ri_{sq} + \frac{d}{dt} \psi_{sq}
    \end{aligned}
    $$

    If there exists a constant current for the 3 phases, the composed current is $0$, but it will consumed power as the form of heat. This is called __Homopolar Current (Voltage)__.



## 1. Review on Induction Machine:
We transformed induction stator and rotor into d-q axis. We have expression:

$$
\begin{aligned}
\bar v_s &= R_s \bar i_s + p\bar \psi_s + j\dot \theta_s\psi_s \\
\bar v_r &= R_r \bar i_r + p\bar \psi_r + j\dot \theta_r\psi_r
\end{aligned}
$$

Where:

* $p = \frac{d}{dt}$

We can find the $L_s$, $M$, $L_r$ from the machine,

And we have: $\bar \psi_s = L_s \bar i_s + M \bar i_r$,
The same for the rotor: $\bar \psi_r = L_s \bar i_r + M \bar i_s$,

$$
\Rightarrow \quad
\begin{aligned}
v_s = R_s \bar i_s + L_s p \bar i_s + M p \bar i_r + j\dot \theta_s\psi_s \\
v_r = R_r \bar i_r + L_r p \bar i_r + M p \bar i_s + j\dot \theta_r\psi_r 
\end{aligned}
$$

And for the torque, we have: $T = n_p I_m (\bar \psi_r \underline{i_r})$,

$$
\frac{v_r^*}{v_r} = \frac{i_r}{i_r^*} = \frac{\psi_r^*}{\psi_r} = k
$$

And we have:

$$
\begin{aligned}
&\frac{v_r^*}{k} =  R_r k i_r^* + k L_r p i_r^* + M p \bar i_s + j\dot \theta_r \frac{\psi_r^*}{k} \\
\Rightarrow &v_r^* = R_r k^2 i_r^* + k^2 L_r p i_r^* + k M p \bar i_s + j\dot \theta_r \psi_r^* \\
&v_r^* = k^2 R_r i_r^* + (k^2 L_r - k M)p i_r^* + k M p(\bar i_s + i_r^*) + j\dot \theta_r \frac{\psi_r^*}{k}
\end{aligned}
$$

$$
k^2L_r - kM = 0 \Rightarrow K(KL_r - M) = 0 \Rightarrow K = \frac{M}{L_r}
$$

The short circuit inductance is: $L_{ks} = L_s - \frac{M^2}{L_r}$. We know that $L = \frac{\psi_1}{i_i}$, $M = \frac{\psi_2}{i_i}$, and the flux likage pass though itself is much larger than the other winding, so $M < L$.

$$
\begin{aligned}
\bar \psi_s &= L_{ks} \bar v_s + \bar \psi_r\\
\psi_r &= M'(\bar i_s + i_r^*)
\end{aligned}
$$

The slip is: $X = \frac{\omega - \omega_m}{\omega}$
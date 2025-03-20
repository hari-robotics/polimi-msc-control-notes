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
## 1. AC Brushless, DC Brushless and Switch Reluctance Machine

BLDC, BLAC and SR Machines are all synchronous machines, 

* BLDC and BLAC are the machine within permanent magnet, SR machine does not have permanent magnets
* BLDC is the PMSM that optimized the design for apply the DC controller
* BLAC is the PMSM that optimized the design for apply the AC controller

## 2. Surface Mounted PMSM

For BLAC machine the magnetic field have sinusoidal waveform, with a surface mounted structure, to obtain this magnetic field, the field strength of the magnetic is different in different position,

## 3. Internal Mounted PMSM


$$
\begin{aligned}
\bar v_s &= R_s \bar i_s + p \bar \psi_s \\
\bar \psi_s &= L_s \bar i_s + \bar \psi_{pm}
\end{aligned}
$$

at steady state, 

$$
\bar v_s = R_s \bar i_s + p(L_s \bar i_s + \bar \psi_{pm}) = R_s \bar i_s + j\omega L_s \bar i_s + j\omega \bar \psi_{pm}
$$

$$
\begin{aligned}
\psi_{sd} &= L_d i_{sd} +\psi_{pm} \\
\psi_{sq} &= L_q i_{sq} \\
L_d &\gg L_q
\end{aligned}
$$

## 4. FOC Control
The dynamics of synchronous machine is:

$$
\begin{aligned}
\bar v_s &= R_s \bar i_s + p \bar \psi_s \\
\bar v_s &= R_s \bar i_s + p \bar \psi_s + j \dot \theta_s \bar \psi_s \\
&= R_s \bar i_s + p \bar \psi_s + j \dot \theta_m \bar \psi_s \\
\end{aligned}
$$

For dq axis, there have:

$$
\begin{aligned}
\bar v_d + jv_q &= R_s(i_{sd} + ji_{sq}) + p(\psi_{sd} + j\psi_{sq}) + j\dot \theta_m(\psi_{sd} + j\psi{sq}) \\
\psi_{sd} &= L_{sd}i_{sd} + \psi_{pm} \\
\psi_{sq} &= L_{sq}i_{sq} \\
\bar v_d + jv_q &= R_si_{sd} + jR_si_{sq} + p\psi_{sd} + jp\psi_{sq} + j\dot \theta_m(L_{sd}i_{sd} + \psi_{pm} + jL_{sq}i_sq) \\ \hfill \\
v_{sd} &= R_si_{sd} + L_{sd}pi_{sd} - \dot \theta_m L_{sq}i_{sq} \\ 
v_{sq} &= R_si_{sq} + L_{sq}pi_{sq} + \dot \theta_m L_{sd}i_{sd} + \psi_{pm}\dot \theta_m
\end{aligned}
$$

$$
\Re(\bar v_s i_s) = \Re(R_s \bar i_s \underline{i_s}) + \Re(p\psi_s \underline{i_s}) + \Re(j\dot \theta_m \bar \psi_s \underline{i_s})
$$

$$
\begin{aligned}
P_m &= -\dot \theta_m \Im(\bar i_s \underline{i_s}) \\
&= -\dot \theta_m \Im(L_{sd}i_{sd} + \psi_{pm} + jL_{sq}i_{sq})(i_{sd} - ji_{sq}) \\
&= -\dot \theta_m \Im(L_{sd}i_{sd}^{2} + \psi_{pm}i_{sd} + j(L_{sq}i_{sq}i_{sd} - \psi_{pm}i_{sq} + L_{sq}i_{sq}^{2} - L_{sd}i_{sd}i_{sq})) \\
&= -\dot \theta_m \Im(L_{sd}i_{sd}^2 + L_{sd}i_{sq}^2 + \psi_{pm}i_{sd} + j(-\psi_{pm}i_{sq} + (L_{sq} - L_{sd})i_{sd}i_{sq}))
\end{aligned}
$$

$$
\begin{aligned}
v_{sd} + jv_{sq} &= j \dot \theta_m (L_{sd}i_{sd} + \psi_{pm} + j L_{sq}i_{sq}) \\
&=  j \dot \theta_m L_{sd} i_{sd} +  j \dot \theta_m \psi_{pm} - \dot \theta_m L_{sq} i_{sq} \\
v_{sd} &= - \dot \theta_m L_{sq} i_{sq} \\
v_{sq} &= \dot \theta_m L_{sd}i_{sd} + \dot \theta_m \psi_{pm}
\end{aligned}
$$

We consider $L_{sd} = L_{sq}$, and we let $i_{sd} = 0$
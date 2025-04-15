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
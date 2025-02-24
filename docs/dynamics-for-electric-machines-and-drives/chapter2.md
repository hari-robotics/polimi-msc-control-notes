# 2. DC Machine Dynamics
## 2.1 

$$
\begin{aligned}
e &= k \psi \omega \\
E &= k^* \psi \omega = K_{exc} \omega
\end{aligned}
$$

EMF is Propotional to the speed of the rotor.

Right hand law to find current direction.

Short circuit windings

Sum of all the EMF is 0

Left hand law for finding the torque generated

$$
T = 2FR
$$

* Electrical Power: $P_{elec} = vi$
* Mechanical Power: $P_{mech} = T \omega$

$$
\begin{aligned}
T &= K_e i \\
E &= K_{e} \omega
\end{aligned}
$$

Give the dynamic equations of the DC machine:

$$
\left\{\begin{aligned}
v_a &= R_a i_a + L_a \frac{di_a}{dt} + e \\
v_e &= R_e i_e + L_e \frac{di_e}{dt} \\
e &= k \psi \omega\\
T &= k \psi i_a
\end{aligned}\right.
$$

And $L_e >> L_a$ because the flux pass through more path on the iron, and the permiability of iron is much larger than the air.

$$
T - T_{RES} = J \frac{d\omega}{dt} (+ G\omega)
$$

## Conclusion
1. Circuit Model
2. Equations
3. Transfer Function Model
4. Power converter, RL-Diode buck

    Large pwr IGBT, Small pwr MOS
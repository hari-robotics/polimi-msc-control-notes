## 4.1 Review on DC Machine Dynamics

$$
\begin{aligned}
V_a &= R_a i_a + L_a \frac{d i_a}{dt} + e \\
V_e &= R_e i_e + L_e \frac{d i_e}{dt} \\
e &= K \psi_e \omega \\
T &= K \psi_e i_a \\
T - T_\delta &= J \frac{d \omega}{dt} (+ G \omega) \\
\psi_e &= L_e i_e
\end{aligned}
$$

The system model for the DC machine is:
<figure markdown="span">
    ![](pics/chapter5/figure1.png){ width="600" }
</figure>

Give the PI controller design for DC machine:
<figure markdown="span">
    ![](pics/chapter5/figure2.png){ width="600" }
</figure>

!!! warning
    * Commonly we use sensor to measure the current instead of the speed because the installation of speed sensor may introduce vibration to the shaft.
    * Between the controller and electrical machine there have the power converter, but we often ignore it because compared with the controll loop, the power converter module have a fast response.
    * The system is not fesiable when $\frac{1}{R_a + s L_a} = \frac{1}{sJ + G}$

If the DC machine is seperately excited, then the controller for the exciting loop should be:
<figure markdown="span">
    ![](pics/chapter5/figure3.png){ width="600" }
</figure>


## 4.2 Space phasors

### 4.2.1 Field distributions of fixed magnetic fields
Given the rotating machine with single windings, 
<figure markdown="span">
    ![](pics/chapter5/figure4.png){ width="300" }
</figure>

We can find the magnetic field $B$ of the rotor that are relevent to the angle of the space $\theta$:

<figure markdown="span">
    ![](pics/chapter5/figure5.png){ width="300" }
</figure>

The magnetic field pass though the rotor is a square wave, the magnitude of the square wave is the average of the sinosoidal wave $B_{avg}$

As the winding number increases and distributed in the space, the magnetic field pass though the windings would be:

<figure markdown="span">
    ![](pics/chapter5/figure6.png){ width="300" }
</figure>

It approaches the sinosoidal wave, for a multiple winding machine, we commonly treat this as a sinosodial wave, ignoring the higher order harmonics.


### 4.2.2 Field distributions of rotating magnetic fields
If we add different group of windings in different angle, the magnetic field of different groups of windings will have the same shape with different phase.

$$
B_a = \frac{4}{\pi} \frac{Ni}{2\delta}\cos(\theta)
$$

$$
B_b = \frac{4}{\pi} \frac{Ni}{2\delta}\cos(\theta - \alpha)
$$

And we can represent them in the pasor:

$$
B_a = Re(B_{max} e^{j\theta})
$$

$$
B_b = Re(B_{max} e^{j(\theta - \alpha)})
$$

Now introduce a 3 phase windings, each of them have a 120 degree phase shift,

$$
\begin{aligned}
i_a &= I_{max} \cos (\omega t) \\
i_b &= I_{max} \cos (\omega t - \frac23 \pi) \\
i_c &= I_{max} \cos (\omega t + \frac23 \pi) \\
\end{aligned}
$$

### 4.2.3 Clarke Transform

### 4.2.4 Park Transform
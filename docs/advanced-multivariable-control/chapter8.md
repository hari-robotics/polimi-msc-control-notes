## 8.1 Norm of a Vector

Given $e = \begin{bmatrix} e_1 \\ \vdots \\ e_m \end{bmatrix}$,

* The 2-norm of the vector is:

    $$
    ||e||_2 = \sqrt{e^Te} = \sqrt{\sum_{i=1}^m e_i^2}
    $$

* The n-norm of the vector is:

    $$
    ||e||_n = (\sum_{i=1}^m|e_i|^n)
    $$

* The infinity norm of the vector is:

    $$
    ||e||_\infty = \sup_i |e_i|
    $$

If we want to have the norm with the matrix, given $m\times n$ matrix $A$,

* Induced 2-norm
    
    $$
    ||A||_{i2} = \sup_{x \neq 0} \frac{||Ax||_2}{||x||_2}
    $$

    $$
    ||A||_{i2} = \underbrace{\sqrt{\lambda_{max}(A^TA)}}_{\text{max singular value of } A}
    $$

    * Singular values and SVD of a matrix

        $A \in C^{m,n}$ the singular values of $A$ are $K = \min{\{m,n\}}$ largest roots of $\lambda(A^*A)$ or $\lambda(AA^*)$

        $$
        \begin{aligned}
        \sigma_i (A) &= \sqrt{\lambda_i(A^*A)} = \sqrt{\lambda_i(AA^*)}, m=n \\
        \sigma_i (A) &= \sqrt{\lambda_i(A^*A)}, m<n\\
        \sigma_i (A) &= \sqrt{\lambda_i(AA^*)}, m>n
        \end{aligned}
        $$

    * SVD

        $A = U\Sigma V^*$, $\Sigma \in \mathbb R^{m\times n}$, $U \in C^{m,m}$, $V\in C^{n,n}$, $U$ and $V$ are unitary matrices,

        $U^*U = UU^* = I$, $V^*V = VV^* = I$ $\Rightarrow$ ($\sigma_i(U) = 1$, $\sigma_i(V) = 1$)

        $\Sigma = \begin{bmatrix}\Sigma_1 \\ \mathbf 0\end{bmatrix}$, $\Sigma_1 \in \mathbb R^{n\times n}$, for $m > n$,

        $\Sigma = \begin{bmatrix}\Sigma_1 & \mathbf 0\end{bmatrix}$, $\Sigma_1 \in \mathbb R^{m\times m}$, for $m < n$,

        $\Sigma = \Sigma_1$, for $m = n$,

        $\Sigma_1 = \begin{bmatrix}\sigma_1(A) && \\ &\dots& \\ && \sigma_k(A)\end{bmatrix}$, with $\sigma_1(A) \geq \sigma_2(A) \geq \dots \geq \sigma_k(A)$, $\sigma_i(A) \geq 0, \forall i$




Proof:

$$
\begin{aligned}
||Ax||_2^2 &= x^TA^TAx \leq \lambda_{max}(A^TA)||x||_2^2 \\
||Ax||_2 &\leq \sqrt{\lambda_{max}(A^TA)}||x||_2 \\
\frac{||Ax||_2}{||x||_2} &\leq \sqrt{\lambda_{max}(A^TA)}
\end{aligned}
$$

## 8.2 Norm of a Signal

Given $e = \begin{bmatrix} e_1 \\ \vdots \\ e_m \end{bmatrix}$,

* 2-norm

    $$
    ||e||_2 = \sqrt{\int_{-\infty}^{+\infty} e^T(t)e(t)}
    $$

* infinity norm

    $$
    ||e||_\infty = \sup_t(\sup_i |e_i(t)|)
    $$

* $L_2$ to $L_2$ Gain,

    let $u(t) = 0, t < 0$,

    $$
    \int_{0}^{+\infty} u^T(t)u(t)dt < \infty
    $$

    if $u\in L_2$,

    $$
    ||u||_2 \sqrt{\int_0^{+\infty} u^T(t)u(t)dt}
    $$

    $$
    \gamma_2 = \sup_{u\in L_2, ||u||_2 \neq 0} \frac{||y||_2}{||u||_2} = \sup_{u\in L_2, ||u||_2 \neq 0} \frac{\varphi(u(t))}{||u||_2}
    $$

    $||y||_2 \leq \gamma_2||u||_2$, $\forall u \in L_2$, a system is input output $L_2$ stable if its $L_2$ gain is finite.

!!! example

    $$
    \begin{aligned}
    y(t) &= \int_0^{+\infty} u(\tau) d\tau \\
    u(t) &= \left\{\begin{aligned} 
    1,\quad 0<t<1\\
    0,\quad \text{otherwise}
    \end{aligned}\right. \\
    ||u||_2 &= \sqrt{\int_0^{+\infty} u^2(t)dt} = 1 \Rightarrow u \in L_2
    \end{aligned}
    $$

    $$
    \begin{aligned}
    ||y||_2 &= \sqrt{\int_0^{+\infty}y^2(t)dt} = +\infty \\
    \sigma_{2} &= \sup_{u\in L_2, ||u||_2 \neq 0} \frac{||y||_2}{||u||_2} = +\infty
    \end{aligned}
    $$

!!! example

    $$
    y(s) = G(s)U(s)
    $$

    $u \in L_2$ $\to$ $U(j\omega)$ with Fourier Transform,

    $$
    y(j\omega) = G(j\omega)U(j\omega)
    $$

    $$
    \begin{aligned}
    ||y||_2^2 &= \int_{-\infty}^{+\infty}y^2(t)dt \\
    &= \frac{1}{2\pi} \int_{-\infty}^{+\infty}|y(j\omega)|^2 d\omega \\
    &= \frac{1}{2\pi} \int_{-\infty}^{+\infty}|G(j\omega)|^2|U(j\omega)|^2 d\omega \leq k^2\frac{1}{2\pi} \int_{-\infty}^{+\infty}|U(j\omega)|^2 d\omega\\
    \end{aligned}
    $$

    if $|G(j\omega)| < k$, with $|G(j\omega)| = k$,

    $$
    \begin{aligned}
    ||y||_2 &\leq k ||u||_2 \\
    \sigma_2 &= \sup_{u\in L_2, ||u||_2 \neq 0} \frac{||y||_2}{||u||_2} \leq k = \sup_\omega |G(j\omega)|
    \end{aligned}
    $$

The system is a SISO A.S. linear system

$$
\omega_2 = \underbrace{||G||_\infty}_{H_\infty \text{ norm of } G} = \sup_\omega |G(j\omega)|
$$

How to extend this result to MIMO A.S. linear system,

$$
G(j\omega) = \begin{bmatrix}
G_{11}(j\omega) & \cdots & G_{1n} \\
\vdots & & \vdots \\
G_{m1} & \cdots & G_{mn}
\end{bmatrix}
$$

if $m=3$, $n = 4$, there have $k = \min(m,n) = 3$ singular values,

$$
\sigma_2 = ||G||_\infty = \sup_{\omega} \bar \sigma(G(j\omega))
$$

When $m=n=1$, then $\sigma(G(j\omega)) = \sqrt{G^*(j\omega)G(j\omega)} = |G(j\omega)|$

Proof:

$$
\begin{aligned}
||y||_2^2 &= \int_{-\infty}^{+\infty}y^T(t)y(t)dt \\
&= \frac{1}{2\pi} \int_{-\infty}^{+\infty}y(j\omega)^*y(j\omega) d\omega \\
&= \frac{1}{2\pi} \int_{-\infty}^{+\infty} U(j\omega)^*G(j\omega)^*G(j\omega)U(j\omega)d\omega \\
&\leq \underbrace{\lambda_{max}(G(j\omega)^*G(j\omega))}_{\bar \sigma^2(G(j\omega))}U(j\omega)^*U(j\omega) \\
&\leq \sup_\omega \bar \sigma^2(G(j\omega)) ||u||_2^2
\end{aligned}
$$
## 1. State Observer

$$
\begin{aligned}
\dot x(t) &= Ax(t) + Bu(t) \\
y(t) &= Cx(t) + Du(t)
\end{aligned}
$$

$\dot {\hat x} = A\hat x + Bu + L\underbrace{(y-C\hat x -Du)}_{\text{output estimation error}}$

And $e = x - \hat x$,

$\dot e = \dot x - \dot{\hat x} = Ax + Bu - A \hat x - Bu - L(Cx+Du-C\hat x -Du)$,

$\dot e = (A-LC)e$

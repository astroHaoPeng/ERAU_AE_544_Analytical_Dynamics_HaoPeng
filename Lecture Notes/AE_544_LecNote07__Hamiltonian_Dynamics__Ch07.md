---
date created: 2025-03-03T09:54:12-05:00
date modified: 2026-04-06T07:55:54-04:00
---

# AE_544_LecNote07\__Hamiltonian_Dynamics__Ch07
![[README#Disclaimers]]

We will introduce the canonical form of the equations of motion, and associated canonical
coordinate transformations. 

%% Leaning outcomes include:
1. Hamiltonian is generally different from but closely related to the total energy.
2.  %%

## Introduce Hamiltonian Function $\calH$

The Hamiltonian function $\calH$ is closely related to the Lagrangian function $\calL$ and is defined as
$$
\mathcal{H} \equiv \sum_{i=1}^{n} \frac{\partial \mathcal{L}}{\partial \dq_i} \dq_i - \mathcal{L} = \mathcal{H}(\bmq, \dot{\bmq}, t)
\tag{7.1}
$$

For a lot of time, the Hamiltonian function $\calH$ is taught as a constant of the motion, but it is actually only a conclusion under certain conditions. 
To find those conditions, we study the total time derivatives of $\calH$,
$$
\frac{d\calH}{dt} = \sum_{i=1}^{n} \left[ \frac{d}{dt} \left( \pp{\calL}{\dq_i} \right) \dq_i + \textcolor{red}{ \pp{\calL}{\dq_i} \ddot{q}_i } \right]  - \left[ \sum_{i=1}^{n} \pp{\calL}{q_i} \dq_i + \sum_{i=1}^{n} \textcolor{red}{ \pp{\calL}{\dq_i} \ddot{q}_i} + \pp{\calL}{t} \right] 
\tag{7.6}
$$
Observing the cancellation of the two terms (in red), and re-collecting, we have
$$
\frac{d\mathcal{H}}{dt} = {\sum_{i=1}^{n} \left\{ \frac{d}{dt} \left( \frac{\partial \mathcal{L}}{\partial \dq_i} \right) - \frac{\partial \mathcal{L}}{\partial q_i} \right\}  \dq_i } - \frac{\partial \mathcal{L}}{\partial t}
\tag{7.7}
$$
And the following two sufficient conditions will lead to the vanish of the remaining terms, and thus lead to that $\calH$ is a constant:
1. The first term will vanish as Lagrange's equations for a <u>conservative or holonomic systems</u>. 
2. The second term vanishes when the Lagrangian function $\calL$ does not explicitly depend on time, i.e., is <u>scleronomic</u>.


## $\calH$ is Total Energy in Natural Systems

The Hamiltonian function is frequently found to equal the total energy, but this is not universally true from the definition in Eq. (7.1).

Plug in $\calL(\bmq, \dot{\bmq}, t) = T(\bmq, \dot{\bmq}, t) - V(\bmq, t)$ into Eq. (7.1), we have
$$
\mathcal{H}(\bmq, \dot{\bmq}, t) = \sum_{i=1}^{n} \left( \pp{T(\bmq, \dot{\bmq}, t)}{\dq_i} \right) \dq_i - T(\bmq, \dot{\bmq}, t) + V(\bmq, t)
\tag{7.8}
$$

So, a sufficient condition for the Hamiltonian $\calH$ to equal the total energy $T+V$ is for the following condition to hold:
$$
\sum_{i=1}^{n} \left( \pp{T(\bmq, \dot{\bmq}, t)}{\dq_i} \right) \dq_i = 2 T
\tag{7.9}
$$

In the following, we study what this condition can be simplified to.

The most general structure of kinetic energy function $T(\bmq, \dot{\bmq}, t)$ is
$$
T = T_0 + T_1 + T_2
$$
where
$$
\begin{aligned}
& T_0 = T_0(t, q)  && \text{\textbf{no} dependence on } \dq \\
& T_1 = T_1(t, q, \dq) = \sum_{i=1}^{n} b_i(t, \bmq) \dq_i  && \text{\textbf{linear} dependence on } \dq \\
& T_2 = T_2(t, q, \dq) = \frac{1}{2} \sum_{i=1}^{n} \sum_{j=1}^{n} m_{ij}(t, \bmq) \,\dq_i \dq_j  && \text{\textbf{quadratic} dependence on } \dq
\end{aligned}
$$
where $b_i(t, \bmq)$ and $m_{ij}(t, \bmq)$ are coefficients not depending on $\dot{\bmq}$.

> [!warning]- Note that $m_{ij}$ doesn't have to be mass.
> For example, it will be momentum of inertial for single pendulum, or will be entries of  matrix of inertia in case of rigid-body dynamics.

With this decomposition, we have
$$
\begin{aligned}
\pp{T}{\dq_i} &= \pp{T_0}{\dq_i} + \pp{T_1}{\dq_i} + \pp{T_2}{\dq_i} \\
&= 0 + b_i(t,\bmq) + \frTwo \sum_{j=1}^{n} \left( m_{ij}(t, \bmq) + m_{ji}(t, \bmq) \right) \, \dq_j
\end{aligned}
$$

Plugging it into Eq. (7.8) gives
$$
\begin{aligned}
\mathcal{H}(\bmq, \dot{\bmq}, t) &= \sum_{i=1}^{n} \left( \pp{T(\bmq, \dot{\bmq}, t)}{\dq_i} \right) \dq_i - T(\bmq, \dot{\bmq}, t) + V(\bmq, t)  \\
&= \sum_{i=1}^{n} \left( b_i(t,\bmq) + \frTwo \sum_{j=1}^{n} \left( m_{ij}(t, \bmq) + m_{ji}(t, \bmq) \right) \, \dq_j \right) \dq_i - T(\bmq, \dot{\bmq}, t) + V(\bmq, t)  \\
&= \sum_{i=1}^{n} b_i(t,\bmq) \dq_i + \sum_{i=1}^{n} \sum_{j=1}^{n} m_{ij}(t, \bmq) \,\dq_i \dq_j - T + V \\
&= T_1 + 2T_2 - (T_0 + T_1 + T_2) + V \\
&= T_0 + T_2 + V
\end{aligned}
$$

Recall that we want to find a sufficient condition such that 
$$
\calH = T + V = T_0 + T_1 + T_2 + V
$$

It is apparent from the above expression that $T_0 = T_1 = 0$ is a sufficient condition that guarantees the Hamiltonian $\calH$ equates to the total energy $T+V$.
In other words, <u>the system kinetic energy is a symmetric quadratic form</u> in the generalized coordinate's time derivates $\dot{\bmq}$,
$$
T = T_2 = \frac{1}{2} \sum_{i=1}^{n} \sum_{j=1}^{n} m_{ij}(t, \bmq) \,\dq_i \dq_j = \frac{1}{2} \dot{\bmq}^T \, [M] \, \dot{\bmq}
\tag{7.17}
$$

Such a system is referred to as a **<u>natural system</u>**, which has a purely quadratic kinetic energy.

For a non-natural system, $T_0$ usually comes from frame motion or motion constraints.


### Example 7.1: Forced pendulum attached to moving cart is not a natural system.

![[fig-7-1_cart_pendulum.png|400]] \
An ideal pendulum (assuming the rod is massless) is attached with the movable pivot (assuming the cart is massless). 
The pivot motion is a prescribed function of time
$$
\begin{aligned}
x(t) &= A \sin (\Omega t) \\
\dot{x}(t) &= A \Omega \cos (\Omega t) \\
\ddot{x}(t) &= -A \Omega^2 \sin (\Omega t) 
\end{aligned}
$$

Kinematics: \
$\bm{R} = A \sin (\Omega t) \, \bm{\hat{n}}_1 + r\, \bm{\hat{e}}_r$, \
$\dot{\bm{R}} = A \Omega \cos (\Omega t)\, \bm{\hat{n}}_1 + r \dot{\theta} \, \bm{\hat{e}}_\theta$

$T = \tfrac{1}{2} m \dot{\bm{R}} \cdot \dot{\bm{R}} = \tfrac{1}{2} m \left[ (A \Omega \cos \Omega t)^2 + r^2 \dot{\theta}^2 + 2 {r} \dot{\theta} (A \Omega \cos \Omega t) \cos \theta \right]$

Therefore, we have the three parts of $T$ as: \
$T_0 = \tfrac{1}{2} m A^2 \Omega^2 \cos^2 (\Omega t)$ \
$T_1 = m A \Omega r \cos \theta \cos (\Omega t) \dot{\theta}$ \
$T_2 = \tfrac{1}{2} m r^2 \dot{\theta}^2$

This is therefore not a natural system because $T_0$ and $T_1$ are non-zero.

To verify it, we can calculate $\calH$ explicitly by its definition as
$$
V = mgr (1-\cos\theta)
$$
$$
\calH = \pp{\calL}{\dot{\theta}} \dot{\theta} - \calL 
= \frTwo m A^2 \Omega^2 \cos^2 \Omega t + mgr(1 - \cos\theta) + \frTwo m r^2 \dot{\theta}^2
$$








## Relationship of $\calH$ to Work/Energy Integral

%%
First, let us write the force $\bmF_i$ on $m_i$ as the sum of conservative and nonconservative forces as
$$
\bm{F}_i = - \pp{V}{\bm{R}_i} + \bmf_{{nc}_i}
$$
For a system of $N$ particles, the work-energy equation is
$$
\begin{aligned}
T(t) - T(t_0) &= T - T_0 = \int_{t_0}^{t} \sum_{i=1}^{N} \bm{F}_i \cdot \dot{\bm{R}}_i \, dt \\
&= - \int_{t_0}^{t} \sum_{i=1}^{N} \pp{V}{\bm{R}_i} \cdot \dot{\bm{R}}_i \, dt + \int_{t_0}^{t} \sum_{i=1}^{N} \bmf_{\text{nc}_i} \cdot \dot{\bm{R}}_i \, dt \\
&= -(V-V_0) + \int_{t_0}^{t} \sum_{i=1}^{N} \bmf_{\text{nc}_i} \cdot \dot{\bm{R}}_i \, dt
\end{aligned}
$$
%%

Integrate the work of non-conservative forces and using the Lagrange's equations for non-conservative forces, the relationship of the change of the total energy and the change of Hamiltonian $\calH$ is found as (detailed derivations referred to textbook):
$$
\ddt (T + V) = \ddt[\calH]+ \sum_{i=1}^{N} \bmf_{nc_i} \cdot \pp{\bmR_i}{t} + \pp{\calL}{t} \equiv \sum_{i=1}^{N} \bmf_{nc_i} \cdot \dot{\bmR}_i
\tag{7.28}
$$
or in the integral format:
$$
(T + V) \Big|_{t_0}^{t_f} - \mathcal{H} \Big|_{t_0}^{t_f} = \int_{t_0}^{t} \sum_{i=1}^{N} \bmf_{nc_i} \cdot \frac{\partial R_i}{\partial \tau} d\tau + \int_{t_0}^{t} \frac{\partial \mathcal{L}}{\partial \tau} d\tau = \int_{t_0}^{t} \sum_{i=1}^{N} \bmf_{nc_i} \cdot \dot{R_i} d\tau 
\tag{7.29}
$$

If the Lagrangian $\calL$ does not explicitly depend on time, then the Hamiltonian $\calH$ is identical to the total energy. 

Required to read Section 7.7 for more detailed and insightful discussions. 



## Alternative Momentum Description

If we defined the **<u>generalized momentum</u>** $p_i$ as
$$
p_i \equiv \frac{\partial \mathcal{L}}{\partial \dq_i}
$$
the Hamiltonian function $\calH$ can be rewritten as
$$
\mathcal{H} = \sum_{i=1}^{n} p_i \dq_i - \mathcal{L} = \bmp^T \dot{\bmq} - \mathcal{L}
$$
Note that here $\bmp$ and $\bmq$ are treated as coordinates of vectors (3x1 matrices) rather than abstract vectors.

The Lagrangian $\calL$ has a quadratic dependence on $\dot{\bmq}$, which means we have the relationship
$$
\bmp = \pp{\calL}{\dot{\bmq}} = [B(t,\bmq)] \cdot \dot{\bmq}
$$
$$
\dot{\bmq} = [B(t,\bmq)]^{-1} \cdot \bmp
$$
In other words, $\dot{\bmq}$ and $\bmp$ are alternative velocity (or momentum) descriptions of the system motion.




## Hamilton’s Canonical Equations (Canonical Form)

The Lagrangian function $\calL(\bmq, \dot{\bmq}, t)$ is always expressed as a function of generalized coordinate $q_i$ and generalized velocity $\dq_i$, but never the generalized momentum $p_i$.

Differently, Hamiltonian can be expressed in two formats:
$$
\mathcal{H} \equiv \sum_{j=1}^{n} \frac{\partial \mathcal{L}}{\partial \dq_j} \dq_j - \mathcal{L}(t, \bmq, \dot{\bmq}) \equiv F(\bmq, \dot{\bmq}, t)
\tag{7.52}
$$
or
$$
\mathcal{H} = \sum_{j=1}^{n} \bmp_j g_j(\bmq, \bmp, t) - \mathcal{L}(\bmq, \bmg(\bmq, \bmp, t), t) \equiv G(\bmq, \bmp, t)
\tag{7.53}
$$
where $g_j(\bmq,\bmp,t)=\dq_j$ and $f_j(\bmq,\dot{\bmq},t)=p_j$ are the two transformations. 

This distinction is important because when we calculate partial derivatives, $\pp{\calH}{q_i}$ will have different results for the above two expressions $F(\bmq,\dot{\bmq},t)$ and $G(\bmq,\bmp,t)$.
To prevent confusion when there is need to be specific, we introduce a notation for differentiation of an arbitrary function $\calF$
$$
\ppqq{\calF}{q_j}   \qquad \text{when $(\bmq, \dot{\bmq},t)$ is used}
\tag{7.56}
$$
$$
\ppqp{\calF}{q_j}   \qquad \text{when $(\bmq, \bmp,t)$ is used}
\tag{7.57}
$$

Lagrange's equations can be re-written using these new notations as
$$
\dot{p}_j = \ppqq{\calL}{q_j} + Q_{{nc}_j}
\tag{7.60}
$$

$$
\begin{aligned}
\ppqp{\mathcal{H}}{p_k} &= \qp{ \pp{}{p_k} \left( \sum_{j=1}^{n} p_j \dq_j - \mathcal{L}(q, \dq, t) \right) } \\
&= \dq_k + \sum_{j=1}^{n} p_j \ppqp{\dq_j}{p_k} - \left\{ \sum_{j=1}^{n} \ppqq{\mathcal{L}}{q_j} \ccancelto{0}{\ppqp{q_j}{p_k}} + \sum_{j=1}^{n} \textcolor{green}{ \ppqq{\mathcal{L}}{\dq_j} } \ppqp{\dq_j}{p_k} \right\} \\
&= \dq_k + \sum_{j=1}^{n} p_j \ppqp{\dq_j}{p_k} - \sum_{j=1}^{n} \textcolor{green}{ p_j } \ppqp{\dq_j}{p_k} \\
&= \dq_k
\end{aligned}
\tag{7.61}
$$

Using similar tricks, we get
$$
\begin{aligned}
\ppqp{\calH}{q_k} &= \qp{\pp{}{q_k} \left( \sum_{j=1}^n p_j \dq_j - \calL \right) } \\
&= \sum_{j=1}^n \ccancelto{0}{ \ppqp{p_j}{q_k} } q_j + \sum_{j=1}^n p_j \ppqp{\dq_j}{q_k}  - \ppqp{\calL}{q_k} \\
&= \sum_{j=1}^n p_j \ppqp{\dq_j}{q_k}  - \left( \sum_{j=1}^n \ppqq{\calL}{q_j}\ppqp{q_j}{q_k} + \sum_{j=1}^n \textcolor{green}{ \ppqq{\calL}{\dq_j} } \ppqp{\dq_j}{q_k} \right) \\
&= \sum_{j=1}^n p_j \ppqp{\dq_j}{q_k} - \ppqq{\calL}{q_k} - \sum_{j=1}^n \textcolor{green}{ p_j } \ppqp{\dq_j}{q_k} \\
&= - \ppqq{\calL}{q_k}
\end{aligned}
\tag{7.64}
$$


Finally, the **<u>Hamilton’s canonical equations</u>** are given as
$$
\begin{aligned}
\dq_j &= \ppqp{\calH}{p_j} \\
\dot{p}_j &= - \ppqp{\calH}{q_j} + Q_{{nc}_j}
\end{aligned}
\tag{7.65}
$$
for $j=1,2,\dots,n$.
The explicit notation on the independent set of coordinates used for the partial derivatives is dropped, with the implicit assumption that $(\bmq, \bmp, t)$ are chosen as the independent variables for partial derivatives.

Introducing the canonical state vector
$$
\bmx = \bmt{\bmq \\ \bmp}
$$
then the gradient vector is
$$
\pp{\calH}{\bmx} = \bmt{\pp{\calH}{\bmq} \\ \pp{\calH}{\bmp}}
$$
and we have the matrix form of Hamilton's equations as (~~verify if the negative sign is correct~~ Whether there is a negative sign or not depends on the definition if $[J]$. Here it is consistent.)
$$
\dot{\bmx} = - [J] \pp{\calH}{\bmx} + \bmt{\bm{0} \\ \bmQ_{nc}},
\tag{7.66}
$$
where the skew-symmetric matrix $[J]$ is
$$
[J] = \bmt{0_n & -I_{n} \\ I_{n} & 0_n}
\tag{7.69}
$$

The matrix $[J]$ is orthogonal as
$$
[J]\trans \cdot [J] = [I_{2n}]
$$
and also has a special feature that
$$
[J] \cdot [J] = - [I_{2n}]
$$
The matrix $[J]$ belongs to a larger group of special matrix, the symplectic matrix.

>[!info] $[J]$ is very much like an active rotation matrix for 90 degrees. 


## Canonical Coordinate Transformations 

Suppose $(\bmq,\bmp)$ are a set of canonical variables associated with a Hamiltonian $\calH(\bmq,\bmp,t)$ and these variables satisfy a set of differential equations of the form of Eqs. (7.66), given a general smooth differentiable set of $2n$ transformation functions:
$$
\begin{aligned}
q_j = f_j(\bmq^*, \bmp^*, t) \\
p_j = g_j(\bmq^*, \bmp^*, t) \\
\end{aligned}
\tag{7.78}
$$
and an associated smooth function $\calH^*$.
We will find the conditions to guarantee the same canonical structure.

### Lagrange bracket conditions (fundamental one)

Take time derivatives of the above transformations:
$$
\ddt[q_j] = \pp{f_j}{t} + \sum_{i=1}^{n} \left( \pp{f_j}{q_i^*} \pp{q_i^*}{t} + \pp{f_j}{p_i^*} \pp{p_i^*}{t} \right) = \textcolor{red}{ \pp{\calH}{p_j} }
$$

$$
\ddt[p_j] = \pp{g_j}{t} + \sum_{i=1}^{n} \left( \pp{g_j}{q_i^*} \pp{q_i^*}{t} + \pp{g_j}{p_i^*} \pp{p_i^*}{t} \right) = -\textcolor{green}{ \pp{\calH}{q_j} }
$$
where we have assumed a conservative system to get rid of $\bmQ$ for simplicity. It can be added back later without affecting the analysis here.

For the partial derivative of any new coordinate $\alpha$ picked from $\bmq^*$ or $\bmp^*$
$$
\begin{aligned}
\pp{\calH}{\alpha} &= \sum_{j=1}^{n} \left(\textcolor{red}{ \pp{\calH}{p_j} } \pp{p_j}{\alpha} + \textcolor{green}{ \pp{\calH}{q_j} } \pp{q_j}{\alpha} \right)   \\
&= \sum_{j=1}^{n} \left( \textcolor{red}{ \pp{\calH}{p_j} } \pp{g_j}{\alpha} + \textcolor{green}{ \pp{\calH}{q_j} } \pp{f_j}{\alpha} \right)   \\
&= \sum_{j=1}^{n} \left( \textcolor{red}{ \pp{f_j}{t} } \pp{g_j}{\alpha} - \textcolor{green}{ \pp{g_j}{t} } \pp{f_j}{\alpha} \right) \\
&\phantom{=\,}+ \sum_{i=1}^{n} \sum_{j=1}^{n} \left( \textcolor{red}{ \pp{f_j}{q_i^*} \pp{q_i^*}{t} } \pp{g_j}{\alpha} - \textcolor{green}{ \pp{g_j}{q_i^*} \pp{q_i^*}{t} } \pp{f_j}{\alpha} \right)  \\
&\phantom{=\,}+ \sum_{i=1}^{n} \sum_{j=1}^{n} \left( \textcolor{red}{ \pp{f_j}{p_i^*} \pp{p_i^*}{t} } \pp{g_j}{\alpha} - \textcolor{green}{ \pp{g_j}{p_i^*}\pp{p_i^*}{t} } \pp{f_j}{\alpha} \right)  \\
&= [\alpha, \beta] + \sum_{i=1}^n [q_i^*, \alpha] \ddt[q_i^*] + \sum_{i=1}^n [p_i^*, \alpha] \ddt[p_i^*]
\end{aligned}
\tag{7.87 and 7.89}
$$
where we have used the definition of **Lagrange's bracket** notation given by
$$
% [\alpha, \beta] = \sum_{j=1}^{n} \left( \pp{f_j}{\alpha} \pp{g_j}{\beta} -  \pp{g_j}{\alpha} \pp{f_j}{\beta} \right)  %% The symbol \alpha is confusing.
[*, \alpha] = \sum_{j=1}^{n} \left( \pp{f_j}{*} \pp{g_j}{\alpha} -  \pp{g_j}{*} \pp{f_j}{\alpha} \right)
\tag{7.88 altered}
$$

So, sufficient conditions to guarantee a canonical transformation are the following skew-symmetric conditions on Lagrange’s brackets ($k \neq m$):
$$
\begin{aligned}[]
[t,\alpha] &= 0 \\
[q_k^*,q_m^*] &= 0 \\
[p_k^*,p_m^*] &= 0 \\
[q_k^*,p_m^*] &= 0 \\
[q_k^*,p_k^*] &= +\,1 \\
[p_k^*,q_k^*] &= -\,1 \\
\end{aligned}
\tag{7.90}
$$

The canonical transformation sufficiency conditions of Eqs. (7.90) and (7.91) hold for the case of general forces, with the generalized forces transformed using Eq. (7.93) below:
$$
\begin{aligned}
\calQ_{q_j}^* &= \sum_{k=1}^{n} \left( \pp{q_k}{p_j^*} \calQ_{q_k} - \pp{f_k}{p_j^*} \calQ_{p_k} \right) \\
\calQ_{p_j}^* &= \sum_{k=1}^{n} \left( \pp{q_k}{q_j^*} \calQ_{q_k} - \pp{f_k}{q_j^*} \calQ_{p_k} \right)
\end{aligned}
$$




### Perfect Differential Criterion for Canonical Transformations (convenient when forward transformation available)

The perfect differential criterion is important because it is much more convenient to test than the Lagrange bracket conditions.

Assume the transformation is given by
$$
\begin{aligned}
q_j &= q_j(q_1^*, \ldots, q_n^*; \, p_1^*, \ldots, p_n^*) \\
p_j &= p_j(q_1^*, \ldots, q_n^*; \, p_1^*, \ldots, p_n^*)
\end{aligned}
\tag{7.94}
$$

<u>Theorem 7.1</u>: The transformation of Eq. (7.94) leads to $q^*_j$ and $p^*_j$ that satisfy canonical differential equations if the following perfect differential condition is true:
$$
\sum_{j=1}^{n} \left( q_j^* \, \mathrm{d}p_j^* - q_j \, \mathrm{d}p_j \right) - \mathrm{d} \calW = 0
\tag{7.95}
$$
for $\calW$ being an arbitrarily smooth differentiable function. The new Hamiltonian $\calH^*$ is obtained by simply replacing $q_j$ and $p_j$ by Eq. (7.94) in the original Hamiltonian.

<u>Proof Sketch</u>: We need to verify all the **Lagrange bracket conditions** in the previous section.

The essential is to find two expressions for 
$\frac{\partial^2 \calW}{\partial q^*_k \partial q^*_l}$, 
$\frac{\partial^2 \calW}{\partial q^*_k \partial p^*_l}$,
$\frac{\partial^2 \calW}{\partial p^*_k \partial p^*_l}$,
which will be then used to formulas desired Lagrange brackets.

Specifically, by plugging in the time derivative differentiating of the smooth transformation function $p_i$
$$
\mathrm{d}p_j = \sum_{k=1}^{n} \left( \pp{p_j}{q_k^*} \, \mathrm{d}q_k^* + \pp{p_j}{p_k^*} \, \mathrm{d}p_k^* \right)
$$
into the time derivative the smooth function $\calW$
$$
\mathrm{d}\calW = \sum_{k=1}^{n} \left( \pp{\calW}{q_k^*} \, \mathrm{d}q_k^* + \pp{\calW}{p_k^*} \, \mathrm{d}p_k^* \right),
$$
we obtain the equation after collecting terms in regard of $dq^*_k$ and $dp^*_k$
$$
\sum_{k=1}^{n} \left( \pp{W}{q_k^*} \mathrm{d}q_k^* + \pp{W}{p_k^*} \mathrm{d}p_k^* \right) 
= \sum_{k=1}^{n} \left( q_k^* - \sum_{j=1}^{n} q_j \pp{p_j}{p_k^*} \right) \mathrm{d}p_k^* - \sum_{k=1}^{n} \sum_{j=1}^{n} q_j \pp{p_j}{q_k^*} \mathrm{d}q_k^*.
$$

Equating the coefficients and we get the expressions for first-order partial derivatives as:
$$
\pp{W}{q_k^*} = -\sum_{j=1}^{n} q_j \pp{p_j}{q_k^*}
$$
$$
\pp{\calW}{p_k^*} = \left( q_k^* - \sum_{j=1}^{n} q_j \pp{p_j}{p_k^*} \right)
$$

From the above two equations, we can get two different expressions for the second order partial differentiations $\frac{\partial^2 W}{\partial q_k^* \partial q_l^*}$.
Then substracting them lead to the desired Lagrange brackets.

The last step is to verify Lagrange bracket conditions in Eq. (7.90) one by one.

> **<u>Example 7.6</u>**: An orthogonal transformation is canonical. \
> Consider the orthogonal transformation
> $$
> \bmq = [A] \bmq^*   \qquad \bmp=[A] \bmp^*
> $$
> where $[A]$ is an orthogonal matrix.
> 
> It can be easily verified that 
> $\bmq^{*T} d\bmp^* - \bmq\trans d\bmp = \bmq^{*T} d\bmp^* - ([A] \bmq^*)\trans [A] \bmp^*$ \
> $= \bmq^{*T} d\bmp^* - \bmq^{*T} \cancelto{I_n}{[A]\trans [A]} \bmp^* = 0 = d\calW$ \
> where $\calW=0$ is a smooth differentiable function.



### Transformation Jacobian Perspective on Canonical Transformations (convenient when inverse transformation available)

Let the generalized coordinate and momenta variables be written as
$$
\begin{aligned}
(q_1, \ldots, q_n;\; p_1, \ldots, p_n) &\equiv (x_1, \ldots, x_n, x_{n+1}, \ldots, x_{2n}) \\
(q_1^*, \ldots, q_n^*;\; p_1^*, \ldots, p_n^*) &\equiv (X_1, \ldots, X_n, X_{n+1}, \ldots, X_{2n})
\end{aligned}
$$
Consider the transformation
$$
\bmx = \bmF(\bmX)
$$
%%
$$
[m] = \left[ \pp{\bmF}{\bmX} \right] \equiv \left[ \pp{\bmx}{\bmX} \right]
$$
%%

The inverse transformation is denoted as
$$
\bmX = \bmG(\bmx)
$$
and its Jacobian matrix $[M]$ is
$$
[M] = \left[ \pp{\bmG}{\bmx} \right] \equiv \left[ \pp{\bmX}{\bmx} \right].
$$

The conditions for a canonical transformation is the symplectic requirement for the Jacobian matrix $[M]$:
$$
[M] [J] [M]\trans = [J]
$$
where $[J]$ is the skew symmetric and orthogonal matrix given as
$$
[J] = \bmt{0_n & -I_n \\ I_n & 0_n}.
$$

<u>Proof Sketch</u>: 
After expanding $[M]$ in elements, we will find the LHS contains all the Lagrange brackets.
$$
[M][J][M]^{\trans} =
\begin{bmatrix}
[q_i^*, q_j^*] & [q_i^*, p_j^*] \\
[p_k^*, q_j^*] & [p_k^*, p_j^*]
\end{bmatrix}
= [J]
$$

Applying the Lagrange bracket conditions and it becomes the symplectic matrix $[J]$.















## Poisson’s Brackets

Consider the time variation of a general smooth function $\calF(\bmq, \bmp, t)$, we define the **Poisson's brackets** of $\calF$ and $\calH$ as
$$
(\calF, \calH) \equiv \sum_{i=1}^{n} \left( \pp{\calF}{q_i} \pp{\calH}{p_i} - \pp{\calF}{p_i} \pp{\calH}{q_i} \right)
$$
or in the matrix format
$$
(\calF, \calH) \equiv \left[ \pp{\calF}{\bmq} \right]^{\trans} \left[ \pp{\calH}{\bmp} \right] - \left[  \pp{\calF}{\bmp} \right]^{\trans} \left[  \pp{\calH}{\bmq} \right]
$$

The derivative of $\calF$ is
$$
\begin{aligned}
\ddt[\calF] &=  \left[\pp{\calF}{\bmq}\right]\trans \bm{\dot{\bmq}} + \left[\pp{\calF}{\bmp}\right]\trans \bm{\dot{\bmp}} + \pp{\calF}{t} \\
&= \left[\pp{\calF}{\bmq}\right]\trans \left[\pp{\calH}{\bmp}\right] - \left[\pp{\calF}{\bmp}\right]\trans \left[\pp{\calH}{\bmq}\right] + \left[\pp{\calF}{\bmp}\right]\trans \bmQ_{nc} + \pp{\calF}{t} \\
&= (\calF,\calH) + \left[\pp{\calF}{\bmp}\right]\trans \bmQ_{nc} + \pp{\calF}{t}
\end{aligned}
\tag{7.73 and 7.74}
$$

Poisson's brackets reveal more algebraic structure of Hamiltonian dynamics. 
This will be used frequently in courses link geometric mechanics. 

>[!info] Poisson brackets are more commonly written as $\{\calF, \calH\}$ in sources outside of our textbook. However, differences in notation conventions should not be seen as a barrier to understanding.



## Summary

This chapter is just a brief introduction to basics of Hamiltonian canonical forms and transformations. The richer content about Hamiltonian systems and dynamical system theories to analyzing the system behavior are beyond the scope of this course.

- Hamiltonian $\calH$ is not total energy generally.
- Hamiltonian $\calH$ is not constant generally.

- has units of energy
- is frequently a constant of the motion, even for a large class of nonconservative systems
- is sometimes but not always, equal to the total energy of the system.

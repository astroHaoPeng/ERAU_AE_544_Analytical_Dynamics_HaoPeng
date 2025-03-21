---
date created: 2025-02-09T16:24:50-05:00
date modified: 2025-03-21T01:36:33-04:00
---
# AE_544_LecNote05\__Lagrangian_Dynamics__Ch05
![[README#Disclaimers]]


## Generalized Coordinates

%% These results provided a unifying perspective on analytical mechanics and also stimulated fundamental advances in allied mathematical subfields such as variational calculus, differential equations, and topology. %%

Even in this simple and most familiar example, we see that **an infinity of coordinate choices** is possible. Depending on the **objectives being pursued** in any given problem, any of these coordinate choices may be **appropriate**. It is clear that the details of most traditional analyses, such as formulating the differential equations of motion, are affected by the coordinates selected, because expressions for all kinematical and physical quantities depend on the coordinate choice. 

Develop **a universal form of the differential equations of motion**, as a function of the system kinetic energy and unspecified generalized coordinates, i.e., $T(q_1, q_2, \cdots, q_n; \dot{q}_1, \dot{q}_2, \cdots, \dot{q}_n)$, that holds for all infinity of possible coordinate choices, and for particle motions, rigid body motions, translations, rotations, deformational vibrations, etc.

At the heart of these developments, it is evident that the various vector descriptions for position $\bmr$, velocity $\dot{\bmr}$, and acceleration $\ddot{\bmr}$ are alternative descriptions or mathematical representations of **the same physical quantities**.

Although broad generality necessarily **introduces a level of abstraction in the formulation**, the ensuing analysis is of bearable complexity and well justified by the powerful generalized results obtained therefrom.


## D’Alembert’s Principle (a reformulation of Newton’s second law)

>[!check] The most important role of d’Alembert’s principle is that it is a stepping stone leading to Lagrange’s equations, Hamilton’s principle, and other variational principles in analytical dynamics. 


### Virtual Displacements and Virtual Work

![[fig-5-2_particle_system.png|400]]

For a system of N particles, the total force vector acting on mi to be segregated into two summed
subsets of forces as
$$
\bmF_i = \bmf_{c_i} + \bmf_i + \sum_{j=1, i\neq j}^N \bmf_{ij}
\tag{5.8}
$$
where
- $\bmf_{c_i}$ is the vector sum of all virtually nonworking constraint forces (as explained in the following).
- $\bmf_{ij}$ is the system internal force acting on the $i$-th due to the $j$-th particle.
- $\bmf_i$ is the vector sum of all other forces except the total constraint force $\bmf_{c_i}$.

We will show that the constraint forces $\bmf_c$ can be eliminated from the analysis, and this is an advantageous feature common to all of the methods of generalized mechanics. 

To accomplish the elimination of the constraint forces, we introduce the concept of virtual displacement $\delta\bmR_i$ . A virtual displacement, in the most general context, is an instantaneous differential displacement for the sake of analysis.

>[!info] The virtual displacement $\delta(\cdot)$ of a dynamical motion variable $(\cdot)$ is closely related to the first variation of coordinates in variational calculus, which we will discuss in the later semester.


If the constraints acting on the system are smooth differential functions of $\bmR_i(t,\qOneToEnd)$, then admissible $\delta\bmR_i$ are constrained to lie on a smooth holonomic (function of position coordinates only) constraint surface $\psi(t,\qOneToEnd)$, and we see that admissible or consistent virtual displacements $\delta\bmR_i$ locate points in a tangent plane, whose normal can be obtained by taking the gradient $\nabla \psi$ of the constraint surface. 

![[fig-5-3_smooth_constraint_surface.png|400]]

Note that the differential displacement ${\rm d}\bmR_i$ (total derivative) is tangent to a particular trajectory, whereas the consistent virtual displacement $\delta\bmR_i$ is an arbitrary differential displacement to any neighboring point in the tangent plane of feasible displacements.

Thus <u>the virtual displacements are not necessarily tangent to any solution trajectory</u>, but they are required to <u>locate neighboring differentially displaced points satisfying the constraints</u>, at some arbitrary and unspecified time t in the motion.

The constraint force $\bmf_{c_i}$ is always normal to the constraint surface (i.e., in the direction of $\nabla \psi$), and therefore can be written as
$$
\bmf_{c_i} = \lambda \nabla \psi
\tag{5.9}
$$

^434e04

where $\lambda$ is referred to as a Lagrange multiplier.

The **Virtual Work $\delta W$** is an abstract idea analogous to mechanical work, but associated with the instantaneous virtual displacements. The virtual work $\delta W$ done on $m_i$ as a consequence of virtual displacement $\delta \bmR_i$ is defined as
$$
\delta W_i \equiv \bmF_i \cdot \delta\bmR_i
\tag{5.10}
$$

Observe that the constraint force $\bmf_{c_i}$ is normal to the plane containing all infinity of admissible virtual displacements $\delta\bmR_i$, and this can be stated as the orthogonality condition:
$$
\delta W_{c_i} = \bmf_{c_i} \cdot \delta\bmR_i = 0
\tag{5.11}
$$

>[!note] **Virtual Work** free up the concept of work to more abstract and general cases.

We define the total virtual work $\delta W$ to be the sum of the $\delta W_i$, so that
$$
\begin{align}
\delta W &= \sum_{i=1}^{N} \bm{F}_i \cdot \delta \bm{R}_i \\
&= \sum_{i=1}^{N}  \left( \bmf_{c_i} + \bmf_i + \sum_{k=1, k\neq i}^N \bmf_{ik} \right) \cdot \delta\bmR_i \\
&= \ccancelto{0}{\sum_{i=1}^{N}  \left( \bmf_{c_i} \cdot \delta\bmR_i \right)}  + \sum_{i=1}^{N} \left( \bmf_i \cdot \delta\bmR_i \right)  + \sum_{i=1}^{N} \left( \sum_{k=1, k\neq i}^N \bmf_{ik} \cdot \delta\bmR_i \right) \\
&= \sum_{i=1}^{N} \left( \bmf_i \cdot \delta\bmR_i \right)  + \sum_{i=1}^{N} \left( \sum_{k=1}^{i-1} \bmf_{ik} \cdot \delta\bmR_i \right) + \sum_{i=1}^{N} \left( \sum_{k=i+1}^N \bmf_{ik} \cdot \delta\bmR_i \right)\\
&= \sum_{i=1}^{N} \left( \bmf_i \cdot \delta\bmR_i \right)  + \sum_{k=1}^{N-1} \left( \sum_{i=k+1}^{N} -\bmf_{ki} \cdot \delta\bmR_i \right) + \sum_{i=1}^{N-1} \left( \sum_{k=i+1}^N \bmf_{ik} \cdot \delta\bmR_i \right)\\
&= \sum_{i=1}^{N} \bm{f}_i \cdot \delta \bm{R}_i + \sum_{i=1}^{N-1} \sum_{k=i+1}^{N} \bm{f}_{ik} \cdot (\delta \bm{R}_i - \delta \bm{R}_k)   \tag{5.13}
\end{align}

$$
Assuming the <u>rigidly constraint</u> (rigid-body assumption) so that $\bmf_{ik}$ is always normal to $(\delta \bm{R}_i - \delta \bm{R}_k)$, then we can simplify it to
$$
\delta W = \sum_{i=1}^N \bmf_i \cdot \delta\bmR_i
\tag{5.17}
$$
So, both the **nonworking constraint forces $\bmf_{c_i}$** as well as the **nonworking system internal forces $\bmf_{ik}$** do not contribute to the total virtual work calculation.

>[!info] The rigid-body assumption doesn't require $\delta\bmR_i-\delta\bmR_k=\bm{0}$, but just requires 
>$$(\bmR_i-\bmR_k)\cdot(\delta\bmR_i-\delta\bmR_k)=0 \tag{5.15}$$
>meaning that the relative virtual displacement are orthogonal to the relative position vector, and thus the internal force $\bmf_{ik}$. (Refer to textbook for details.)


### Development of d’Alembert’s Principle using Virtual Work

> $$
> \bmF_i = \bmf_{c_i} + \bmf_i + \sum_{j=1, i\neq j}^N \bmf_{ij}
> \tag{5.8 copied}
> $$

Applying Newton's second law for the motion of $m_i$, we have
$$
\bmf_{c_i} + \bmf_i + \sum_{j=1, i\neq j}^N \bmf_{ij} - m_i \ddot{\bmR}_i = 0
\tag{5.18}
$$
Upon taking the dot product of Eq. (5.18) with an arbitrary consistent/admissible virtual displacement $\delta\bmR_i$ and summing over all $N$ particles, we find the <u>most general form of d’Alembert’s principle</u> to be:
$$
\delta W - \sum_{i=1}^N m_i \ddot{\bmR}_i \cdot \delta\bmR_i = 0
\tag{5.19}
$$
Consider $\delta\bmR_i$ to be generated by a set of independent virtual variations in the $q_i$ through
$$
\delta \bmR_i = \sum_{j=1}^n \pp{\bmR_i}{q_j} \delta q_j
\tag{5.20}
$$
>[!note] The number of particles $m_i$ is $N$. The number of general variables $q_j$ is $n$.

> $$
> \delta W = \sum_{i=1}^{N} \bm{f}_i \cdot \delta \bm{R}_i + \sum_{i=1}^{N-1} \sum_{k=i+1}^{N} \bm{f}_{ik} \cdot (\delta \bm{R}_i - \delta \bm{R}_k)
> \tag{5.13 copied}
> $$

As a consequence, the virtual work $\delta W$ in Eq. (5.17) can be rewritten as
$$
\begin{align}
\delta W &= \sum_{i=1}^{N} \bm{f}_i \cdot \delta \bm{R}_i  \\
&= \sum_{i=1}^{N} \bmf_i \cdot \left( \sum_{j=1}^n \pp{\bmR_i}{q_j} \delta q_j \right)  \\
&= \sum_{j=1}^n \left[ \sum_{i=1}^{N} \bmf_i \cdot \left( \pp{\bmR_i}{q_j} \delta q_j \right) \right]    \tag{finite series; linearity}  \\
&= \sum_{j=1}^n \left[ \textcolor{red}{ \sum_{i=1}^{N} \left(\bmf_i \cdot  \pp{\bmR_i}{q_j} \right) } \delta q_j  \right]        \tag{associativity} \\
&= \sum_{j=1}^n \textcolor{red}{ Q_j } \delta q_j    \tag{5.21}
\end{align}
$$
Here, we defined **generalized force $Q_j$** as a combination of $N$ virtually working forces $\bmf_i$, which is
$$
Q_j \equiv \sum_{i=1}^{N} \left(\bmf_i \cdot  \pp{\bmR_i}{q_j} \right)
\tag{5.22}
$$
^generalized-force-Qi

Plugging everything back to Eq. (5.19) gives us
$$
\sum_{j=1}^{n} \left[ Q_j - \sum_{i=1}^{N} m_i \ddot{\bm{R}}_i \cdot \frac{\partial \bm{R}_i}{\partial q_j} \right] \delta q_j = 0
\tag{5.23}
$$
Because the $\delta q_j$ are independent virtual variations, they may be chosen independently and arbitrarily, so each coefficient must be 0 by itself.
This leads to the most famous form of **<u>d’Alembert’s principle</u>**:
$$
\sum_{i=1}^N m_i \ddot{\bmR}_i \cdot \frac{\partial \bmR_i}{\partial q_j} = Q_j   \qquad \text{for } j=1,2,\dots,n
\tag{5.24}
$$
These equations are generally a coupled system of $n$ second-order differential equations.

----

Observe that the position vector ${\bmR}_i(t,q_1,q_2,\dots,q_n)$ can be differentiated to obtain the expression for velocity $\bmV_i$ as
$$
\bmV_i(t,\qOneToEnd,\qDotOneToEnd) = \dot{\bmR}_i(t,q_1,q_2,\dots,q_n) = \pp{\bmR_i}{t} + \sum_{k=1}^n \pp{\bmR_i}{q_k} \dot{q}_k  \qquad  i = 1,2,\dots,N
\tag{5.25}
$$
From this, we can get the following identity (cancellation of dots identity)
$$
\pp{\bmV_i}{\dot{q}_k} = \pp{\dot{\bmR}_i}{\dot{q}_k} = \pp{\bmR_i}{q_k}
\tag{5.26}
$$
<u>Proof:</u> Simply plugging in Eq. (5.25) and solve the partial derivatives. It relies on the fact that ${\bmR}_i(t,q_1,q_2,\dots,q_n)$ is not explicitly a function of any $\dot{q}_k$.

We define the **partial velocity** $\bmv_{ik} \equiv \pp{\dot{\bmR}_i}{\dq_k} = \pp{{\bmR}}{q_k}$, so Eq. (5.25) becomes,
$$
\bmV_i = \dot{\bmR}_i = \pp{\bmR_i}{t} + \sum_{k=1}^n \dq_k \bmv_{ik},\qquad  i = 1,2,\dots,N
\tag{5.27}
$$
The $n$ vectors $\{\bmv_{i1}, \bmv_{i2}, \dots, \bmv_{in}\}$ form a vector basis for the inertial velocity $\bmV_i$ of the $i$-th mass $m_i$, and for the case that time does not appear explicitly, the $\dq_k$ are the coefficients that linearly combine the basis vectors $v_{ik}$ to give the velocity vector $\bmV_i$.

The d'Alembert's principle in Eq. (5.24) can be rewritten <u>using generalized forces</u> $Q_j$ as
$$
\sum_{i=1}^N m_i \ddot{\bmR}_i \cdot \bmv_{ij} = Q_j    \qquad \text{for } j = 1,2,\dots,n
\tag{5.28}
$$

Combine Eqs. (5.22) and (5.29), we have <u>another form of the d'Alembert's principle</u>:
$$
\sum_{i=1}^N [\bmf_i - m_i \dot{\bmV}_i] \cdot \bmv_{ij} = 0  \qquad  \text{ for } j = 1,2,\dots,n
\tag{5.30}
$$
where 
- $\bmf_i$ is the vector sum of all other forces acting on $m_i$
- $\bmV_i$ is the velocity vector of $m_i$
- $\bmv_{ij} = \pp{\dot{\bmR}_i}{\dot{q}_k} = \pp{\bmR_i}{q_k}$ is the (Kane's definition) partial velocity (not a velocity decomposition!)


>[!check] Different forms of <u>d'Alembert's principle</u>:
> 1. (classical form, Eq. 5.24) $\sum_{i=1}^N m_i \ddot{\bmR}_i \cdot \frac{\partial \bmR_i}{\partial q_j} = Q_j$
> 2. $\sum_{i=1}^N m_i \ddot{\bmR}_i \cdot \bmv_{ij} = Q_j$
> 3. (virtual power form, Eq. 5.30) $\sum_{i=1}^N [\bmf_i - m_i \dot{\bmV}_i] \cdot \bmv_{ij} = 0$
> 
> where $Q_j = \sum_{i=1}^N \bmf_{i}\cdot\pp{\bmR_i}{q_j} = \sum_{i=1}^N \bmf_i \cdot \bmv_{ij}$ and $\bmv_{ij} = \pp{\dot{\bmR}_i}{\dot{q}_k} = \pp{\bmR_i}{q_k}$.
^dalemberts-principle-different-forms

### Example 5.3: Cart + Pendulum + Spring (Newtonian vs. d'Alembert's principle)

![[fig-5-6_cart_pendulum_spring.png|400]] The free body diagram is only needed for direct application of Newton's law.

Kinematics of the two bodies are:
$$
\bmR_1 = x \nht1   \qquad    
\dot{\bmR}_1 = \dot{x}\nht1   \qquad
\ddot{\bmR}_1 = \ddot{x}\nht1
\tag{5.31}
$$
$$
\begin{aligned}
\bmR_2 &= x\nht1 + r\eht{r} = (x+r\sin\theta)\nht1 + (-r\cos\theta)\nht2 \\
%
\dot{\bm{R}}_2 &= \dot{x} \hat{n}_1 + r \dot{\theta} \hat{e}_{\theta} = (\dot{x} + r \dot{\theta} \cos \theta) \hat{n}_1 + (r \dot{\theta} \sin \theta) \hat{n}_2 \\
%
\ddot{\bm{R}}_2 &= \ddot{x} \nht1 - r \dot{\theta}^2 \eht{r} + r \ddot{\theta} \eht{\theta} \\
&= (\ddot{x} - r \dot{\theta}^2 \sin \theta + r \ddot{\theta} \cos \theta) \nht1 + (r \dot{\theta}^2 \cos \theta + r \ddot{\theta} \sin \theta) \nht2 \\
%
&= (\ddot{x} \sin \theta - r \dot{\theta}^2) \eht{r} + (\ddot{x} \cos \theta + r \ddot{\theta}) \eht{\theta}
\end{aligned}
\tag{5.32}
$$

External forces on the two bodies $m_1$ and $m_2$ are
$$
\bmf_1 = -kx\nht1 - m_1g\nht2    \qquad     \bmf_2 = - m_2 g \nht2
\tag{5.35}
$$

**Differential equations derived via Newton’s laws.** 
We need to first introduce the constraint forces $N, F_r$ and then eliminate them.
(Refer to textbook page 219).

**Differential equations derived via d’Alembert’s principle.** 
The chosen generalized coordinates are $(x, \theta)$.

The partial derivatives are
$$
\begin{aligned}
\pp{\bmR_1}{x} &= \nht1     &     \pp{\bmR_1}{\theta} &= \bm{0} \\
\pp{\bmR_2}{x} &= \nht1     &      \pp{\bmR_2}{\theta} &= r\cos\theta\nht1 + r\sin\theta\nht2
\end{aligned}
\tag{5.41}
$$

![[#^generalized-force-Qi]]

Using the definition in Eq. (5.22), we can obtain the generalized forces as
$$
\begin{aligned}
Q_x &= \bmf_1 \cdot \pp{\bmR_1}{x} + \bmf_2 \cdot \pp{\bmR_2}{x} \\
&= (-kx\nht1-m_1g\nht2) \cdot \nht1 + (-m_2g\nht2) \cdot \nht1 = -kx \\
%
Q_y &= \bmf_1 \cdot \pp{\bmR_1}{\theta} + \bmf_2 \cdot \pp{\bmR_2}{\theta} \\
&= (-kx\nht1-m_1g\nht2) \cdot 0 + (-m_2g\nht2) \cdot (r\cos\theta\nht1 + r\sin\theta\nht2) \\
&= -m_2gr\sin\theta
\end{aligned}
\tag{5.42}
$$

![[#^dalemberts-principle-different-forms]]

We are now prepared to develop the differential equations of motion using d’Alembert’s principle (particularly, from-1):
$$
\begin{aligned}
m_1 \ddot{\bmR}_1 \cdot \pp{\bmR_1}{x} + m_2 \ddot{\bmR}_2 \cdot \pp{\bmR_2}{x} = Q_x \\
m_1 \ddot{\bmR}_1 \cdot \pp{\bmR_1}{\theta} + m_2 \ddot{\bmR}_2 \cdot \pp{\bmR_2}{\theta} = Q_\theta \\
\end{aligned}
$$
After substituting everything we prepared, the first equation is
$$
\begin{aligned}
& m_1 \ddot{x} \nht1 \cdot \nht1 + m_2 ((\ddot{x} - r \dot{\theta}^2 \sin \theta + r \ddot{\theta} \cos \theta) \nht1 + (r \dot{\theta}^2 \cos \theta + r \ddot{\theta} \sin \theta) \nht2) \cdot \nht1 = - kx \\
& m_1 \ddot{x} + m_2 (\ddot{x} - r \dot{\theta}^2 \sin \theta + r \ddot{\theta} \cos \theta) = - kx \\
& \textcolor{red}{ (m_1 + m_2) \ddot{x} + m_2 r \ddot{\theta} \cos \theta - m_2 r \dot{\theta}^2 \sin \theta = - kx }
\end{aligned}
$$
and the second equation is
$$
\begin{aligned}
& m_1 \ddot{x} \nht1 \cdot \bm{0} + m_2 ((\ddot{x} - r \dot{\theta}^2 \sin \theta + r \ddot{\theta} \cos \theta) \nht1 + (r \dot{\theta}^2 \cos \theta + r \ddot{\theta} \sin \theta) \nht2) \cdot (r\cos\theta\nht1 + r\sin\theta\nht2) = -m_2 gr \sin\theta \\
& m_2 (\ddot{x} - r \dot{\theta}^2 \sin \theta + r \ddot{\theta} \cos \theta) r\cos\theta + m_2 (r \dot{\theta}^2 \cos \theta + r \ddot{\theta} \sin \theta) r\sin\theta = -m_2 gr \sin\theta \\
& m_2 r \cos\theta \ddot{x} + m_2 r^2 \ddot{\theta} = -m_2 gr \sin\theta \\
& \textcolor{red}{ \cos\theta \ddot{x} + r \ddot{\theta} = - g \sin\theta }
\end{aligned}
$$




### Newtonian Dynamics with Constraints

The preceding developments implicitly assume that the generalized coordinates are independent. It often occurs that the coordinates are not independent. 
In the simplest case, the redundancy of the coordinates arises because of constraining <u>algebraic relationships</u> of the form
$$
\psi_k(t,q_1,q_2,\dots,q_n) = 0     \qquad k=1,2,\cdots,m
\tag{5.54}
$$
which is referred to as **holonomic constraints**.
If time does not explicitly appear in the constraint in Eq. (5.54), then this special case of holonomic constraints are said to be scleronomic.

Some examples of **nonholonomic constraints**:
- Inequality constraints
- Velocity-dependent constraint that cannot be integrated to obtain this form


There are usually two obvious approaches to **dealing with the holonomic constraint**: 
1. Solve the constraint equation for any one of the coordinates as a function of the other coordinates $q_i$ that may be considered independent. <u>Then, the d'Alembert's principle can be directly applied.</u>
2. Replace the constraint surface by an equivalent constraint force that effectively causes the motion to remain on the constraint surface. <u>Then, the constraint force has to be taken into consideration when applying the d'Alembert's principle, because the admissible virtual work is not confined on the constraint surface anymore.</u>

>[!note] Under constraints, the d'Alembert's principle requires admissible/consistent virtual displacement to get rid of constraint forces explicitly. When the constraint forces need to be handled explicitly, Newtonian mechanics or Lagrange multipliers are the fallbacks.


![[fig-5-9_particle__on_holonomic_constraint_surface.png|400]]

For the case of introducing the constraint force $\bmf_c$ that is normal to the smooth holonomic constraint surface $\psi=0$, as shown in Fig. 5.9, 
$$
\bmf_c = \lambda \pp{\psi}{x}\nht1 + \lambda \pp{\psi}{y}\nht2 + \lambda \pp{\psi}{z}\nht3
\tag{5.68}
$$
Adding this constraint force into Newton's second law, we are able to get differential equations with additionally constraints. 

Newton’s second law provides the equation of motion
$$
\bmf + \bmf_c = m \ddot{\bmR}
\tag{5.63}
$$
which can be explicitly expressed as 
$$
\begin{aligned}
m \ddot{x} &= f_x + \lambda\pp{\psi}{x} \\
m \ddot{y} &= f_x + \lambda\pp{\psi}{y} \\
m \ddot{z} &= f_x + \lambda\pp{\psi}{z} \\
\end{aligned}
\tag{5.69}
$$
Together with a algebraic equation (the constraint function)
$$
\psi(x,y,z,t) = 0
\tag{5.70}
$$
From Eqs. (5.69) and (5.70), we observe that the constraint force $\bmf_c$ is not necessarily to be written out explicitly but what we need is just the function $\psi$ and its partial derivatives.

<u>Next, we observe another feature that enables an extension from holonomic constraints to a more general type of constraints. </u>
Differential change $dx,dy,dz$ along the trajectory satisfies the following constraint:
$$
\frac{d\psi}{dt} = \frac{\partial \psi}{\partial x} \dot{x} + \frac{\partial \psi}{\partial y} \dot{y} + \frac{\partial \psi}{\partial z} \dot{z} + \frac{\partial \psi}{\partial t} = 0
$$
which is equivalent to
$$
d\psi = \frac{\partial \psi}{\partial x} dx + \frac{\partial \psi}{\partial y} dy + \frac{\partial \psi}{\partial z} dz + \frac{\partial \psi}{\partial t} dt = 0.
\tag{5.66}
$$

Admissible virtual change $\delta x, \delta y, \delta z$ are along the constraint surface at a fixed moment without an increment in time $t$, which can be expressed as
$$
\delta \psi = \frac{\partial \psi}{\partial x} \delta x + \frac{\partial \psi}{\partial y} \delta y + \frac{\partial \psi}{\partial z} \delta z = 0
\tag{5.67}
$$
So, the essential of the constraint $\psi$ is actually its differential form in Eq. (5.66).

Now, we introduce **Pfaffian Nonholonomic Constraints** which are a special generalization of holonomic constraints and can be expressed commonly as
$$
B(x,y,z,t) + A_1(x,y,z,t) \dot{x} + A_2(x,y,z,t) \dot{y} + A_3(x,y,z,t) \dot{z} = 0
\tag{5.84}
$$
or the differential format
$$
Bdt + A_1 d{x} + A_2 d{y} + A_3 d{z} = 0
$$
Notice that it will degenerate to holonomic constraint if there is a function $\psi$ whose partial derivatives are the coefficients $B,A_1,A_2,A_3$ above.

For the case of $m$ constraints and $n$ generalized coordinates, consider $N$ particles with $m$ Pfaffian nonholonomic constraints:
$$
\sum_{j=1}^{n} A_{kj} \dot{q}_j + B_k = 0 \qquad k = 1, 2, \dots, m
\tag{5.99}
$$
where $A_{kj} = A_{kj}(\qOneToEnd,t)$ and $B_{k}=B_k(\qOneToEnd,t)$ are functions of generalized coordinates $q_j$ and time.
This can also be expressed as
$$
\sum_{j=1}^{n} A_{kj} d{q}_j + B_k dt = 0 \qquad k = 1, 2, \dots, m
\tag{5.100}
$$
For the case that $\bmq$ is the set of $n=3N$ Cartesian inertial coordinates, the equations of motion for the $N$ particles are $n$ second-order ODEs
$$
M_j \ddot{q_j} = f_j + f_{c_j} = f_j + \sum_{k=1}^m A_{kj} \lambda_k  \qquad j = 1,2, \dots, n
\tag{5.102}
$$
and $m$ first-order ODEs
$$
\sum_{j=1}^n A_{kj} \dot{q}_j + B_k = 0   \qquad k = 1,2,\dots,m
\tag{5.103}
$$
The Eqs. (5.102) and (5.103) constitute a set of **differential-algebraic equations (DAEs)**.




### Example 5.6: classical pendulum (two approaches to embed constraints in Derivations)

![[fig-5-8_pendulum.png|250]]

**Algebraic constraint elimination:**
$$
\bm{R} = r \hat{e}_r, \quad \dot{\bm{R}} = \dot{r} \hat{e}_r + r \dot{\theta} \hat{e}_{\theta}, \quad \ddot{\bm{R}} = (\ddot{r} - r \dot{\theta}^2) \hat{e}_r + (r \ddot{\theta} + 2r \dot{\theta}^2) \hat{e}_{\theta}
$$
and there is a holonomic constraint
$$
\psi(r,\theta) = r-R = 0
$$
so that we are only let with a single independent coordinate $\theta$:
$$
\bm{R} = R \eht{r}, \quad \dot{\bm{R}} = R \dot{\theta} \eht{\theta}, \quad \ddot{\bm{R}} = -(R \dot{\theta}^2) \eht{r} + (R \ddot{\theta}) \eht{\theta}
$$

![[#^dalemberts-principle-different-forms]]

Recall the d'Alembert's principle above and apply the classical form here:
$$
\begin{aligned}
m \ddot{\bm{R}} \cdot \frac{\partial \bm{R}}{\partial \theta} &= Q_{\theta} \\
m \left(-(R \dot{\theta}^2) \eht{r} + (R \ddot{\theta}) \eht{\theta}\right) \cdot \pp{}{\theta}\left(R \eht{r}\right) &= \bmf \cdot \pp{\bmR}{\theta} \\
m \left(-(R \dot{\theta}^2) \eht{r} + (R \ddot{\theta}) \eht{\theta}\right) \cdot (R\eht{\theta}) &= mg(\cos\theta\eht{r}-\sin\theta\eht{\theta}) \cdot (R\eht{\theta}) \\
m R^2 \ddot{\theta} &= -mgR \sin \theta \\
\ddot{\theta} &= -\frac{g}{R} \sin \theta
\end{aligned}
$$

**Constraint force via Lagrange multipliers:**
Thus the constraint force associated with $\psi(r,\theta)=r-R=0$ is written as a centripetal force $\bmF_c$
$$
\bmF_c = \lambda \nabla \psi(r,\theta) = \lambda \eht{r}
$$
The <u>total force</u> acting on mass $m$ is 
$$
\bmF=-mg\nht2+\lambda\eht{r}
$$
and the d'Alembert's principle (the classical form) gives two equations this time
![[#^dalemberts-principle-different-forms]]
$$
\begin{aligned}
m \ddot{\bm{R}} \cdot \frac{\partial \bm{R}}{\partial r} &= Q_{r} \\
m \ddot{\bm{R}} \cdot \frac{\partial \bm{R}}{\partial \theta} &= Q_{\theta}
\end{aligned}
$$
which leads to
$$
\begin{aligned}
m \left[ (\ddot{r} - r \dot{\theta}^2) \eht{r} + (r \ddot{\theta} + 2r \dot{\theta}) \eht{\theta} \right] \cdot \eht{r} &= [-mg\nht2+\lambda\eht{r}] \cdot \eht{r} = mg\cos\theta+\lambda  \\
m \left[ (\ddot{r} - r \dot{\theta}^2) \hat{e}_r + (r \ddot{\theta} + 2r \dot{\theta}) \hat{e}_{\theta} \right] \cdot r\eht\theta &= [-mg\nht2+\lambda\eht{r}] \cdot (r\eht\theta) = -mgr\sin\theta
\end{aligned}
$$
Because $r=R$ is a constant, $\dot{r}=\ddot{r}=0$ and we have
$$
\begin{aligned}
\lambda = -mg\cos\theta - mR \dot{\theta} \\
\ddot{\theta} = - \frac{g}{R} \sin\theta
\end{aligned}
$$
which is the same to the previous approach.

>[!info]- Partial derivatives in polar coordinates $\pp{\eht{r}}{\theta}=\eht{\theta}$, $\pp{\eht{\theta}}{\theta}=-\eht{r}$.
>Proof #1: resolving to $\nht1,\nht2$ to show $\theta$ explicitly, then taking partial derivatives directly.
>
>Proof #2:
> $$
> d\eht{r} = \pp{\eht{r}}{t} dt + \pp{\eht{r}}{r} d{r} + \pp{\eht{r}}{\theta} d{\theta}  \tag{total derivative}
> $$
> $$
> \ddtN\eht{r} = \ddtE\eht{r} + \dot{\theta} \eht3 \times \eht{r} = \dot{\theta} \eht{\theta}   \tag{transport theorem}
> $$
> and
> $$
> d\eht{\theta} = \pp{\eht{\theta}}{t} dt + \pp{\eht{\theta}}{r} dr + \pp{\eht{\theta}}{\theta} d{\theta}   \tag{total derivative}
> $$
> $$
> \ddtN\eht{\theta} = \ddtE\eht{\theta} + \dot{\theta} \eht3 \times \eht{\theta} = -\dot{\theta}\eht{r}   \tag{transport theorem}
> $$
> Compare the coefficients and we get the results.


### D’Alembert’s principle vs. Newton's second law
- A fundamental advantage over Newton’s second law in that the internal forces and all other virtually nonworking constraint forces can be simply ignored in developing the equations of motion.
- The vector kinematic algebraic overhead associated with Newton’s second law and d’Alembert’s principle is essentially identical, because both require vector kinematics to be taken through the acceleration level.

## Lagrangian Dynamics

- Lagrange’s equations require only velocity-level vector kinematics.

### Minimal Coordinate Systems and Unconstrained Motion

An assumption for the following derivation is that, if constraints are present, they are simple algebraic holonomic constraints that have been kinematically eliminated to establish a minimal coordinate description of the system, so the generalized coordinates must be independent.

![[AE_544_LecNote05__Lagrangian_Dynamics__Ch05#^dalemberts-principle-different-forms]]

Rewrite Eq. (5.24) explicitly as
$$
\sum_{i=1}^{N} m_i \ddot{\bm{R}}_i \cdot \frac{\partial {\bm{R}}_i}{\partial q_j} = \sum_{i=1}^{N} \bm{f}_i \cdot \frac{\partial \bm{R}_i}{\partial q_j} \quad \text{for} \quad j = 1, 2, \dots, n
$$
and by plugging in the cancellation of dots identity, we have
$$
\sum_{i=1}^{N} m_i \ddot{\bm{R}}_i \cdot \frac{\partial \dot{\bm{R}}}{\partial \dot{q}_j} = \sum_{i=1}^{N} \bm{f}_i \cdot \frac{\partial \dot{\bm{R}}}{\partial \dot{q}_j} \quad \text{for} \quad j = 1, 2, \dots, n
\tag{5.135}
$$

The kinetic energy $T(t,\qOneToEnd;\qDotOneToEnd)$ is generally a function of both $q_i$ and $\dot{q}_i$,
$$
T = \frac{1}{2} \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \dot{\bm{R}}_i
\tag{5.136}
$$
so the partial derivatives with respect to $(q_j,\dot{q}_j)$ are
$$
\begin{aligned}
\frac{\partial T}{\partial q_j} &= \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \frac{\partial \dot{\bm{R}}_i}{\partial q_j} \\
\quad \frac{\partial T}{\partial \dot{q}_j} &= \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j}
\end{aligned}
\tag{5.137}
$$
Now we can do
$$
\begin{align}
\ddt \left( \frac{\partial T}{\partial \dot{q}_j} \right) &= \ddt \left( \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j} \right)   \tag{used 5.137} \\
%
&= \sum_{i=1}^{N} m_i \ddot{\bm{R}}_i \cdot \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j} + \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \ddt \left( \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j} \right) \\
%
&= \sum_{i=1}^{N} \left( \bm{f}_i + \bm{f}_{ci} \right) \cdot \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j} + \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \ddt \left( \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j} \right) \\
%
&=  \sum_{i=1}^{N} \bm{f}_i \cdot \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j}  +  {\sum_{i=1}^{N}\bm{f}_{ci}  \cdot \frac{\partial {\bm{R}}_i}{\partial {q}_j}} +  \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \ddt \left( \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j} \right) \tag{cancel dots for last two terms} \\
%
&=  \sum_{i=1}^{N} \bm{f}_i \cdot \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j}  +  \ccancelto{0}{\sum_{i=1}^{N}\bm{f}_{ci}  \cdot \sum_{j=1}^n\frac{\partial {\bm{R}}_i}{\partial {q}_j}\delta q_j} +  \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \ddt \left( \frac{\partial {\bm{R}}_i}{\partial {q}_j} \right) \tag{special admissible $\delta\bmR_i$ with only $\delta q_j\neq0$} \\
%
&= \sum_{i=1}^{N} \bm{f}_i \cdot \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j} + \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \frac{\partial }{\partial {q}_j}\left(\ddt{\bm{R}}_i\right)       \tag{smooth $\bmR_i$, switch $\pp{}{q_j}$ and $\ddt$} \\
%
&= \sum_{i=1}^{N} \bm{f}_i \cdot \frac{\partial \dot{\bm{R}}_i}{\partial \dot{q}_j} + \frac{\partial T}{\partial {q}_j}     \tag{used 5.137} \\
%
&= Q_j + \pp{T}{q_j}
\end{align}
$$
Therefore, we have the **most fundamental version of Lagrange’s equations**,
$$
\ddt \left(\pp{T}{\dot{q}_j}\right) - \pp{T}{q_j} = \sum_{i=1}^N \bmf_i \cdot \pp{\dot{\bmR}_i}{\dot{q}_j} \equiv Q_j     \qquad \text{for } j = 1,2,\dots,n
\tag{5.139}
$$
^Lagranges-equation-fundamental

An appropriate definition of kinetic energy results in these equations applying to systems of rigid bodies and particles.

Again, the assumption is that the the generalized coordinates $\{\qOneToEnd\}$ must be independent in Eq. (5.139).

### Example 5.10: particles with decreasing radius (Applying Lagrange's equations)

![[fig-5-12_particle_decreasing_radius.png|400]]
A particle moves on a table. A string attached to the particle is being drawn through a hole such that the radius is decreasing at a constant rate; <u>determine angular velocity as a function of time.</u> 

A reference frame $\{\nht{}\}$ and a polar frame $\{\eht{r},\eht{\theta}\}$. 

The radial speed is a constant $v_r = \dot{r} = -c$, where $c>0$ is a constant.

The only generalized coordinate is $\theta$.

The position vector is $\bmR = r\eht{r}$.

The velocity vector is $\dot{\bmR} = {\dot{r}\eht{r}} + r \dot{\theta}\eht{\theta} = -c\eht{r}+r \dot{\theta}\eht{\theta}$

The kinetic energy is $T = \frac{1}{2} m \left( c^2 + r^2 \dot{\theta}^2 \right)$

Apply the Lagrange's equation:
![[#^Lagranges-equation-fundamental]]
and we have
$$
\begin{aligned}
\ddt \left( mr^2\dot{\theta} \right) - 0 &= -F_r \eht{r} \cdot (r\eht{\theta}) \\
\ddt \left( mr^2\dot{\theta} \right) &= 0
\end{aligned}
$$
Since $r = r_0 - ct$ is time-varying, we have 
$$
(r_0 - ct)^2 \dot{\theta} = r_0^2 \dot{\theta}_0 \quad \Longrightarrow \quad \dot{\theta} = \frac{r_0^2}{(r_0 - ct)^2} \dot{\theta}_0
$$


### Lagrange’s Equations for Conservative Forces

For the conservative force $\bmf_i$ determined by the potential function $V(t,\qOneToEnd)$, we have
$$
\bmf_i = - \pp{V}{\bmR_i}
$$
Then the generalized force is given by
$$
Q_j = \sum_{i=1}^N \bmf_i \cdot \pp{\bmR_i}{q_j} = - \sum_{i=1}^N \pp{V}{\bmR_i} \cdot \pp{\bmR_i}{q_j} = - \pp{V}{q_j}
\tag{5.151}
$$
Define the **Lagrangian function $\calL$** as
$$
\calL = \calL(t,\qOneToEnd;\qDotOneToEnd) \equiv T - V
\tag{5.152}
$$
so that we have 
$$
\begin{aligned}
\pp{\calL}{\dot{q}_j} &= \pp{T}{\dot{q}_j} \\
\pp{\calL}{{q}} &= \pp{T}{{q}_j} - \pp{V}{\dot{q}_j}
\end{aligned}
$$
If all forces are conservative, for the fundamental format of Lagrange's equstions
![[#^Lagranges-equation-fundamental]]
we can move all $Q_j$ to LHS and plugin Eq. (5.151) to get
$$
\ddt \left(\pp{T}{\dot{q}_j}\right) - \pp{T}{q_j} + \pp{V}{q_j} = 0
$$
Then, plug in the definition of $\calL$ and its partial derivatives, we get the <u>most famous form of Lagrange's equations</u>, in the case when all forces are conservative,
$$
\ddt \left( \pp{\calL}{\dot{q}_j} \right) - \pp{\calL}{q_j} = 0
\tag{5.153}
$$
^Lagranges-equation-conservative-forces

>[!info] For many elementary conservative systems, the potential and kinetic energy can be simply written with a minimum of derivations; for these cases, Eqs. (5.153) do not require derivation of any generalized forces and are therefore especially attractive.

For more general cases with both conservative and nonconservative forces, we just need to retain the generalized forces at the RHS, resulting,
$$
\ddt \left( \pp{\calL}{\dot{q}_j} \right) - \pp{\calL}{q_j} = Q_{nc_j}
\tag{5.154}
$$
^Lagranges-equation-conservative-and-nonconservative-forces

where the nonconservative generalized force $Q_{nc_j} = \sum_{i=1}^N \bmf_{nc_j} \cdot \pp{\dot{\bmR}_i}{\dot{q}_j}$.

### Example 5.12: linear spring pendulum (Applying Lagrange's equations)

![[fig-5-14_spring_pendulum.png|300]] the linear spring pendulum is considered: nominal unstretched spring length $r_0$, linear spring constant $k$. Develop the equations of motion. 

The only virtually working forces are the spring force and gravity, and that there are two generalized coordinates $\{r,\theta\}$.

The position vector is $\bmR = r \eht{r}$ \
The velocity vector is $\bmV = \dot{\bmR} = \dot{r}\eht{r} + r\dot{\theta}\eht{\theta}$

The kinetic energy is $T=\frac{1}{2}m \bmV \cdot \bmV = \frac{1}{2}m ( \dot{r}^2+r^2\dot{\theta}^2 )$

Both the gravity and the spring force are conservative, so the total potential function is $V=-mgr\cos\theta+\frac{1}{2}k(r-r_0)^2$

So the Lagrangian function is $\calL = T-V = \frac{1}{2}m \bmV \cdot \bmV = \frac{1}{2}m ( \dot{r}^2+r^2\dot{\theta}^2)  + mgr\cos\theta - \frac{1}{2}k(r-r_0)^2$

![[#^Lagranges-equation-conservative-forces]]
Applying the Lagrange's equations for conservative forces, we have
$$
\begin{aligned}
&\ddt \left( \pp{\calL}{\dot{r}} \right) - \pp{\calL}{r} = 0 \\
&\ddt \left( \pp{\calL}{\dot{\theta}} \right) - \pp{\calL}{\theta} = 0 \\
\end{aligned}
$$
which gives
$$
\begin{aligned}
&\ddt \left( m \dot{r} \right) - mr \dot{\theta}^2 - mg\cos\theta + k(r-r_0) = 0 \\
&\ddt \left( mr^2 \dot{\theta} \right) - mgr\sin\theta = 0 \\
\end{aligned}
$$
then
$$
\begin{aligned}
& m \ddot{r} - mr \dot{\theta}^2 - mg\cos\theta + k(r-r_0) = 0 \\
& 2mr \dot{r} \dot{\theta} + mr^2 \ddot{\theta} + mgr\sin\theta = 0 \\
\end{aligned}
$$

Alternatively, if we want to apply the other format of Lagrange's equations
![[#^Lagranges-equation-fundamental]]
we need to first calculate the two generalized forces as
$$
\begin{aligned}
Q_r &= \Big(-k(r-r_0) \eht{r} + mg \cos\theta\eht{r} - mg\sin\theta\eht{\theta} \Big) \cdot \pp{ (\dot{r}\eht{r} + r\dot{\theta}\eht{\theta})}{\dot{r}} \\
Q_\theta &= \Big(-k(r-r_0) \eht{r} + mg \cos\theta\eht{r} - mg\sin\theta\eht{\theta} \Big) \cdot \pp{( \dot{r}\eht{r} + r\dot{\theta}\eht{\theta})}{\dot{\theta}} \\
\end{aligned}
$$
Obviously we will get the same results but with a bit more steps and algebras. These force has been implicitly accounted for by being included in the potential energy function. 

### Problem 5.1:  linear torsional spring (comparing different methods to obtain EOMs)
![[fig-p5-1_torsional_spring.png|400]]

**Use Newton's law and free-body diagrams for the rod and mass.** \
![[fig-p5-1_netwon's_method_free_body.png|150]]

Summing the forces and torques on the <u>massless rod</u>:
$0 \cdot \frac{d^2}{dt^2} \left( \frac{R}{2} \hat{e}_r \right) = (F_r - F_{or}) \hat{e}_r + (F_\theta + F_{o\theta}) \hat{e}_\theta$ \
$-k \theta + R F_\theta = 0$ \
from which we can resolve: 
$F_{or} = F_r \quad F_{o\theta} = -F_\theta  \quad F_\theta = \frac{k \theta}{R}$

Summing the forces on the <u>mass</u> (no torques because it's treated as a mass point now):
$m \left( - R \dot{\theta}^2 \hat{e}_r + R \ddot{\theta} \hat{e}_\theta \right) = \left( - F_r + mg \cos \theta \right) \hat{e}_r + \left( - F_\theta - mg \sin \theta \right) \hat{e}_\theta$ \
$F_r = mg \cos \theta + m r \dot{\theta}^2$ \
$m R \ddot{\theta} = - \frac{k}{R} \theta - mg \sin \theta$

And finally we have the equation of motion as a function of just the angle $\theta$: $\boxed{\ddot{\theta} = - \frac{k}{m R^2} \theta - \frac{g}{R} \sin \theta}$

**Using Euler's equations of rotational motion,** which is essentially still Newton's law for special cases of rotation. \
![[fig-p5-1_euler's_equation_free_body.png|100]]

Apply the Euler's equation $\dot{\bmH} = \bmL$ directly to the total angular momentum (respect to $O$) $H = m R^2 \dot{\theta}$. Notice it is a planar case so only the magnitude will be considered. \
The torque relative to the pivot $O$ can be easily formulated as $L=-mgR\sin\theta-k\theta$, where we assuming the positive direction for $\bmL$ is to point out of the screen/paper. \
Then, we have
$\boxed{m R^2 \ddot{\theta} = -k \theta - mg R \sin \theta}$
which is already the EOM.

**Using Lagrange's equations for conservative forces.**\
The generalized coordinate is just $\theta$ as apparently from previous free-body diagrams. 
The kinematic and potential functions are given as \
$T = \frac{1}{2} m \dot{\bm{R}} \cdot \dot{\bm{R}} = \frac{1}{2} m r^2 \dot{\theta}^2$ \
$V = mgR(1 - \cos \theta) + \frac{1}{2} k \theta^2$ \
So, the Lagrangian function is $\mathcal{L} = T - V$ $= \frac{1}{2} m R^2 \dot{\theta}^2 + mg R \cos \theta - \frac{1}{2} k \theta^2 - mg R$ 

Applying Lagrange's equations $\ddt\left( \pp{\calL}{\dq} \right) - \pp{\calL}{q} = 0$ requires the following derivatives: \
$\frac{d}{dt} \left( \frac{\partial \mathcal{L}}{\partial \dot{\theta}} \right) = m R^2 \ddot{\theta}$ \
$\frac{\partial \mathcal{L}}{\partial \theta} = -mg R \sin \theta - k \theta$

Therefore the equation of motion is obtained as: 
$\boxed{m R^2 \ddot{\theta} + mg R \sin \theta + k \theta = 0}$

>[!question] After-class practice, can the spring force be considered directly in the Lagrange's equations? 
>[Hint] Recall how the potential function $V$ is absorbed into the Lagrange function $\calL$.

>[!done] In this case, Euler's equation of rotational motion turns out to be the easiest approach. But clearly Lagrange's equations have provided a more systematic and streamlined approach. 

### Example 5.13: Generalize Example 5.3 with a damper (Applying Lagrange's equations with non-conservative forces)

![[fig-5-13_pendulum_cart_damped.png|300]] 
The spring is accompanied with a dashpot linear damper with the damping force given as $-c \dot{x} \nht1$. 

The generalized coordinates are still $\{x,\theta\}$.

The kinematics are 
$$
\dot{\bmR}_1 = \dot{x}\nht1 \qquad 
\dot{\bmR}_2 = \dot{x}\nht1 + r\dot{\theta}\eht{\theta}
$$

The virtually working force is $\bmf_d = -c \dot{x}\nht1$

The two generalized forces are (there are two generalized forces because of two generalized coordinates),
$$
\begin{aligned}
Q_x &= \bmf_d \cdot \pp{\dot{\bmR}_1}{\dot{x}} + \ccancelto{0}{\bmf_2 \cdot \pp{\dot{\bmR}_2}{\dot{x}}} = -c \dot{x} \\
Q_\theta &= \bmf_d \cdot  \pp{\dot{\bmR}_1}{\dot{\theta}} + \ccancelto{0}{\bmf_2 \cdot \pp{\dot{\bmR}_2}{\dot{\theta}}} = 0
\end{aligned}
$$

So the kinetic energy is 
$T=\frac{1}{2} (m_1\dot{\bmR}_1\cdot \dot{\bmR}_1 + m_1\dot{\bmR}_2\cdot \dot{\bmR}_2)$ $= \frac{1}{2}\left( m_1 \dot{x}^2 + m_2 \dot{x}^2 + m_2 r^2 \dot{\theta}^2 + 2 m_2\dot{x}r\dot{\theta} \cos\theta \right)$ \
and the potential energy function is
$V=\frac{1}{2}kx^2 - m_2gr\cos\theta$ \
Thus, the Lagrangian function is
$\calL = T-V$ $= \frac{1}{2}\left( m_1 \dot{x}^2 + m_2 \dot{x}^2 + m_2 r^2 \dot{\theta}^2 + 2 m_2 \dot{x}r\dot{\theta} \cos\theta \right)$ $- \frac{1}{2}kx^2 + m_2gr\cos\theta$

Apply the Lagrange's equations with nonconservative forces below
![[#^Lagranges-equation-conservative-and-nonconservative-forces]]
we get
$$
\begin{aligned}
\ddt\left( m_1 \dot{x} + m_2 \dot{x} + m_2 r\dot{\theta}\cos\theta \right) + kx &= -c \dot{x} \\
\ddt\left( m_2r^2\dot{\theta} + m_2 \dot{x}r\cos\theta \right) + m_2 \dot{x}r\dot{\theta}\sin\theta + m_2gr\sin\theta &= 0
\end{aligned}
$$
After working out the derivatives, we get the EOMs as
$$
\begin{aligned}
 m_1 \ddot{x} + m_2 \ddot{x} + m_2 r\ddot{\theta}\cos\theta - m_2r\dot{\theta}^2\sin\theta + kx &= -c \dot{x} \\
 m_2r^2\ddot{\theta} + m_2 \ddot{x}r\cos\theta - m_2 \dot{x}r \dot{\theta}\sin\theta  + m_2 \dot{x}r\dot{\theta}\sin\theta + m_2gr\sin\theta &= 0
\end{aligned}
$$

Notice that we also don't need to calculate $\ddot{\bmR}_i$ in this approach, even though we need to calculate two "forces".


### Redundant Coordinate Systems and Constrained Motion

Goal: Extend Lagrange’s equations to consider redundant coordinates subject to <u>Pfaffian nonholonomic constraints</u> (which is more general and includes holonomic constraints).

Previously we assumed $n$ was the number of degrees of freedom (which implicitly means all holonomic constraints have been eliminated, and that $\{\qOneToEnd\}$ are a minimal set of independent coordinates.
Under this case, the virtual displacement $\delta q_j$ can be chosen arbitrarily.
This can be expressed as the following principle that the virtual work is always zero for arbitrary $\delta q_j$
$$
\delta W = \sum_{j=1}^{n} \left[ Q_j + \frac{\partial T}{\partial q_j} - \ddt \left( \frac{\partial T}{\partial \dot{q}_j} \right) \right] \delta q_j = 0 
\tag{5.165}
$$

Now, let's assume $\{\qOneToEnd\}$ are not independent and several constraints are present.
Furthermore, let's consider there are $m$ Pfaffian form constraints
$$
\sum_{j=1}^n A_{kj}\dot{q}_j + B_k = 0  \qquad k = \oneTo{m}
\tag{5.166}
$$
For instantaneous admissible virtual displacements under these constraints, we have
$$
\sum_{j=1}^n A_{kj} \delta q_j = 0    \qquad   k = \oneTo{m}
\tag{5.168}
$$
where $A_{kj} = A_{kj}(\qOneToEnd,t)$ and $B_{k}=B_k(\qOneToEnd,t)$ are functions of generalized coordinates $q_j$ and time.

Analogous to the development of the constraint optimization Lagrange multiplier rule, we have
$$
\delta W = \sum_{j=1}^{n} \left[ Q_j +  \sum_{k=1}^m \lambda_k A_{kj}  + \frac{\partial T}{\partial q_j} - \ddt \left( \frac{\partial T}{\partial \dot{q}_j} \right) \right] \delta q_j = 0 
\tag{5.169}
$$
Finally, we get the constrained version of Lagrange’s equations of motion
$$
\begin{aligned}
& \ddt \left( \frac{\partial T}{\partial \dot{q}_j} \right) - \frac{\partial T}{\partial q_j} = Q_j + \sum_{k=1}^{m} \lambda_k A_{kj}  &&j = 1, 2, \dots, n  \\
& \sum_{j=1}^{n} A_{kj} \dot{q}_j + B_k = 0   & &k = 1, 2, \dots, m
\end{aligned}
\tag{5.170 and 171}
$$
^Lagranges-equation-constrained

More conveniently, if there are some conservative forces, we can define the total potential function $V$ and the Lagrangian function $\calL = T-V$, then we get
$$
\begin{aligned}
&\ddt \left( \frac{\partial \mathcal{L}}{\partial \dot{q}_j} \right) - \frac{\partial \mathcal{L}}{\partial q_j} = \bm{Q}_{nc_j} + \sum_{k=1}^{m} \lambda_k A_{kj}    &&  j = 1, 2, \dots, n  \\
& \sum_{j=1}^{n} A_{kj} \dot{q}_j + B_k = 0   & &k = 1, 2, \dots, m
\end{aligned}
\tag{5.172}
$$
^Lagranges-equation-conservative-constrained


### Summarize of All Formats

> [!done] Summary of different forms of Lagrange's equation:
> Fundamental with a minimum set of generalized coordinates:
> ![[#^Lagranges-equation-fundamental]]
> 
> Only conserved forces:
> ![[#^Lagranges-equation-conservative-forces]]
> 
> Both conservative and nonconservative forces:
> ![[#^Lagranges-equation-conservative-and-nonconservative-forces]]
> 
> Redundant generalized coordinates with constraints:
> ![[#^Lagranges-equation-constrained]]
> 
> Ultimate version with everything:
> ![[#^Lagranges-equation-conservative-constrained]]
^Lagranges-equation-summary





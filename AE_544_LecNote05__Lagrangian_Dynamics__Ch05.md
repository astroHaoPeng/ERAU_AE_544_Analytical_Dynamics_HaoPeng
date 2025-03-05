---
date created: 2025-02-09T16:24:50-05:00
date modified: 2025-03-05T15:56:32-05:00
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
> 1. (classical form, Eq. 5.24) $\sum_{i=1}^N m_i \ddot{\bmR}_i \cdot \frac{\partial \bmR_i}{\partial q_i} = Q_j$
> 2. $\sum_{i=1}^N m_i \ddot{\bmR}_i \cdot \bmv_{ij} = Q_j$
> 3. (virtual power form, Eq. 5.30) $\sum_{i=1}^N [\bmf_i - m_i \dot{\bmV}_i] \cdot \bmv_{ij} = 0$
> 
> where $Q_j = \sum_{i=1}^N \bmf_{i}\cdot\pp{\bmR_i}{q_j} = \sum_{i=1}^N \bmf_i \cdot \bmv_{ij}$ and $\bmv_{ij} = \pp{\dot{\bmR}_i}{\dot{q}_k} = \pp{\bmR_i}{q_k}$.
^dalemberts-principle-different-forms

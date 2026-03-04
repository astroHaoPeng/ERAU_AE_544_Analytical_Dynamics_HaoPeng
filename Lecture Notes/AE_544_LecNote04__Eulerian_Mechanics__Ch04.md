---
date created: 2025-01-26T13:42:36-05:00
date modified: 2026-03-04T00:48:50-05:00
---

# AE_544_LecNote04\__Eulerian_Mechanics__Ch04

![[README#Disclaimers]]

The rotational dynamics of a rigid body are often referred to as Eulerian mechanics, because
Euler’s equation $\dot{\bmH} = \bmL$ and Euler’s rotational equation of motion generally govern this field.

But it is actually just Newtonian Mechanics being specialized for the case of rigid body dynamics.

> [!info] Review
> Newton's second law:
> $$
> \bmF = \ddt (m\bmv) = m \bm{a}
> $$
> 
> Euler's rotational equation of motion
> $$
> \dot{\bmH} = \ddt {\large(} \bmt{I} \bmo {\large)} = \bmt{I} ~ \dot{\bmo} + \bmo\times(\bmt{I}~\bmo)
> $$
> 
> Euler’s equation 
> $$
> \dot{\bmH} = \bmL
> $$

## Rigid Body Dynamics

Let the moment be taken either about the center of mass or the inertial coordinate frame origin, see [[AE_544_LecNote02__Newtonian_Mechanics__Ch02#Angular Momentum|Angular Momentum in lecture note 02]]. 
In either case Euler’s equation reduces to
$$
\dot{\bmH} = \bmL
\tag{4.1}
$$
^Euler-equation-general-vector-format


![[fig-4-1_rigid_body_angular_momentum.png|300]]

In the inertial frame $\calN$, \
vector $\bmR$ is the inertial position vector of an infinitesimal mass element $\dm$; \
$\bmR_c$ is the center of mass; \
$\bmr=\bmR-\bmR_c$ is the relative position vector; \
$\bmo$ is the instantaneous angular velocity vector $\bmo_{\calB/\calN}$ of the rigid
body frame $\calB$ relative to the inertial frame $\calN$.

The angular momentum relative to $O$ is then given by
$$
\begin{aligned}
\bm{H}_O &= \int_B \bm{R} \times \dot{\bm{R}} \, \dm \\
&= \int_B (\bm{R}_c + \bm{r}) \times (\dot{\bm{R}}_c + \dot{\bm{r}}) \, \dm \\
&= \int_B \bm{R}_c \times \dot{\bm{R}}_c \, \dm + \int_B \bm{r} \times \dot{\bm{R}}_c\, \dm  + \bm{R}_c \times \int_B \dot{\bm{r}} \, \dm + \int_B \bm{r} \times \dot{\bm{r}} \, \dm \\
&= \left( \int_B \dm \right) \bm{R}_c \times \dot{\bm{R}}_c  +  \left( \int_B \bm{r} \, \dm \right) \times \dot{\bm{R}}_c + \bm{R}_c \times \left( \int_B \dot{\bm{r}} \, \dm \right) + \int_B \bm{r} \times \dot{\bm{r}} \, \dm \\
&= \left( \int_B \dm \right) \bm{R}_c \times \dot{\bm{R}}_c  +  \ccancelto{\bm{0}}{\left( \int_B \bm{r} \, \dm \right)} \times \dot{\bm{R}}_c + \bm{R}_c \times \ccancelto[green]{\bm{0}}{\left( \int_B \dot{\bm{r}} \, \dm \right)} + \int_B \bm{r} \times \dot{\bm{r}} \, \dm \\
&= \bm{R}_c \times M \dot{\bm{R}}_c + \int_B \bm{r} \times \dot{\bm{r}} \, dm \\
\end{aligned}
\tag{4.5}
$$
- The first term is the angular momentum of the mass center about the origin, and its behavior was studied when discussing the dynamics of <u>a single particle</u> (the superparticle). 
- The second term is the angular momentum vector of the rigid body $\calB$ about its mass center $\bmR_c$. 

We define the angular momentum vector $\bmH_c$ of the rigid body $\calB$ about its mass center $\bmR_c$ as  
$$
\bm{H}_c = \int_B \bm{r} \times \dot{\bm{r}} \, \dm 
\tag{4.6}
$$
>[!warning] From here on $\bmH_c$ will be studied.

$$
\begin{align}
\dot{\bmr} &= \ddtN \bmr = \ddtB \bmr + \bmo_{\calB/\calN} \times \bmr    \tag{transport theorem}\\
&= \bmo_{\calB/\calN} \times \bmr    \tag{rigid body}
\end{align}
$$

So,
$$
\bm{H}_c = \int_B \bm{r} \times (\bmo \times \bm{r}) \, \dm 
= \int_B - \bmt{\bm{\tilde{r}}} \bmt{\bm{\tilde{r}}} ~ \bmo \, \dm 
= \left( \int_B - \bmt{\bm{\tilde{r}}} \bmt{\bm{\tilde{r}}} \, \dm  \right) \cdot \bmo 
$$
Express all the coordinates in the body frame $\calB$, 
$$
\begin{aligned}
\bmr &= r_1 \bht1 + r_2 \bht2 + r_3 \bht3 \\
\bmo &= \omega_1\bht1 + \omega_2\bht2 + \omega_3\bht3 \\
\bmH_c &= H_{c_1}\bht1 + H_{c_2}\bht2 + H_{c_3}\bht3
\end{aligned}
$$
and recall the skew-symmetric tilde matrix is defined as
$$
\cdB{[\tilde{\bmr}]} = \skewmt{r}
$$

The component form of $\bmH_c$ is obtained as:
$$
\bm{H}_c =
\cdB{\bmt{H_{c_1} \\ H_{c_2} \\ H_{c_3}}}
=
\left( \int_B
\cdB{\bmt{r_2^2 + r_3^2 & -r_1 r_2 & -r_1 r_3 \\
-r_1 r_2 & r_1^2 + r_3^2 & -r_2 r_3 \\
-r_1 r_3 & -r_2 r_3 & r_1^2 + r_2^2}} \dm  \right)
\cdot \cdB{\bmt{\omega_1 \\ \omega_2 \\ \omega_3}}

$$
**Define the <u>inertia matrix at the center of mass</u> $\cdB{\bmt{I_c}}$ as**
$$
\cdB{\bmt{I_c}} = \int_B
\cdB{\bmt{r_2^2 + r_3^2 & -r_1 r_2 & -r_1 r_3 \\
-r_1 r_2 & r_1^2 + r_3^2 & -r_2 r_3 \\
-r_1 r_3 & -r_2 r_3 & r_1^2 + r_2^2}} \dm
\tag{4.14}
$$
The inertia matrix is **coordinate system-dependent**. If a different coordinate system were assigned to the rigid body, the corresponding inertia matrix would be different.

It will be always assumed that the vectors and inertia matrices are written in the $\calB$ frame and the superscript is dropped. 
The angular momentum vector of a rigid body about its center of mass can then be written in its simplest form as
$$
\bmH = \bmt{I_c} ~ \bmo
\tag{4.15}
$$

**Transformation from center of mass to a different point:** (Parallel axis theorem) Given the moment of inertia matrix $\bmt{I_c}$ of a rigid body $\calB$ about its center of mass and the position vector $\bmR_c$ of this center of mass relative to some fixed point $O$, then the inertia matrix $\calB$ about $O$ is given through the transformation
$$
\bmt{I_O} = \bmt{I_c} + M \bmt{\tilde{\bmR}_c} \bmt{\tilde{\bmR}_c}\trans %\text{\color{red}checked! the transpose is correct.}
\tag{4.19}
$$
All the components must be expressed in the same coordinate system/frame.

$$
\begin{align}
\dot{\bmR_c} &= \ddtB \bmR_c + \bmo \times \bmR_c = \bm{0} + \bmo \times \bmR_c   \tag{4.16}\\

\bmH_O 
&= \bm{R}_c \times M \dot{\bm{R}}_c + \int_B \bm{r} \times \dot{\bm{r}} \, dm    \tag{4.15}\\
&= \bmR_c \times M (\bmo \times \bmR_c) + \bmt{I_c} \\
&= M \bmt{\tilde{\bmR}_c} (\bmo \times \bmR_c) + \bmt{I_c} \\
&= - M \bmt{\tilde{\bmR}_c} \bmt{\tilde{\bmR}_c} \bmo + \bmt{I_c} \tag{4.18} \\
&= M \bmt{\tilde{\bmR}_c} \bmt{\tilde{\bmR}_c}^T \bmo + \bmt{I_c} \tag{skew-symmetric}
\end{align}
$$

**Transformation from one body frame to another:**
Let the reference frames $\calB$ and $\calF$ both be proper body-fixed coordinate systems.
The inertia matrix written in the $\calB$ frame is rewritten into the $\calF$ frame
through the similarity transformation
$$
\cdF{\bmt{I}} = \dcm{FB} \cdot \cdB{\bmt{I}} \cdot \dcm{FB}\trans
\tag{4.24}
$$

If the above $\dcm{FB}\trans$ happens to be the matrix of eigenvectors of $\cdB{\bmt{I}}$, the resulting $\cdF{\bmt{I}}$ will be a diagonal matrix with eigenvalues at the diagonal, which is called **Principal inertias**:
$$
\cdF{\bmt{I_1&0&0 \\ 0&I_2&0 \\ 0&0&I_3}} = \bmt{\bm{\nu}_1&\bm{\nu}_2&\bm{\nu}_3}\trans \cdot \cdB{\bmt{I}} \cdot \bmt{\bm{\nu}_1&\bm{\nu}_2&\bm{\nu}_3},
$$
where $\bm{\nu}_i$ and $I_i$ are the eigenvector and eigenvalue satisfying $\cdB{\bmt{I}} \bm{\nu}_i = I_i~\bm{\nu}_i$ 
This new set of body-fixed coordinate basis $\{\bm{\nu}_1,\bm{\nu}_2,\bm{\nu}_3\}$ are called the **principal axes**.


> [!Question] Will $\cdB{\bmt{I}}$ in an arbitrary body frame $\calB$ be symmetric for an asymmetric rigid body? 

> [!Question] Can the inertia matrix $\cdB{\bmt{I}}$ of an asymmetric rigid body be diagonal?


## Euler's Rotational Equations of Motion

Use transport theorem to expand the rotational equations of motion as:
$$
\begin{align}
\bmL_c &= \dot{\bmH}_c = \ddtB \bmH_c + \textcolor{red}{ \bmo_{\calB/\calN} \times \bmH_c } \\
&= \cancelto{\bm{0}}{\left(\ddtB \bmt{I}\right)} \bmo + \bmt{I} \ddtB \bmo + \textcolor{red}{ \bmo_{\calB/\calN} \times(\bmt{I}\bmo) }     \tag{used $\bmH_c=\bmt{I}\bmo$ in body frame} \\
&= \bmt{I} \ddtB \bmo + \textcolor{red}{ \bmo\times (\bmt{I}~\bmo) }      \tag{$\cdB{\bmt{I}}$ is constant} \\
&= \bmt{I} \ddtB \bmo \textcolor{red}{ + \bmt{\tilde{\bmo}}\bmt{I}~\bmo }      \tag{$\cdB{\bmt{I}}$ is constant} \\
&= \bmt{I} \left( \ddtN\bmo + \cancelto{\bm{0}}{\bmo_{\calN/\calB} \times \bmo} \right) + \bmt{\tilde{\bmo}}\bmt{I}~\bmo \\
&= \bmt{I} ~ \dot{\bmo} + \bmt{\tilde{\bmo}}\bmt{I}~\bmo    \tag{4.32} \\
&= \bmt{I} ~ \dot{\bmo} + \bmo\times(\bmt{I}~\bmo)  \tag{4.32 alternative}
\end{align}
$$
where we have used the fact that $\bmo = \bmo_{\calB/\calN} = - \bmo_{\calN/\calB}$

The derivative of the body angular velocity vector $\bmo$ is the same as seen in the $\calB$ and the $\calN$ frame:
$$
\dot{\bmo} = \ddtN \bmo = \ddtB \bmo + \bmo \times \bmo = \ddtB{\bmo}
\tag{4.30}
$$

In the principal body frame, the Euler's equation reduces to
$$
\begin{aligned}
I_{11} \dot{\omega}_1 &= -(I_{33} - I_{22}) \omega_2 \omega_3 + L_1 \\
I_{22} \dot{\omega}_2 &= -(I_{11} - I_{33}) \omega_3 \omega_1 + L_2 \\
I_{33} \dot{\omega}_3 &= -(I_{22} - I_{11}) \omega_1 \omega_2 + L_3 
\end{aligned}
\tag{4.33}
$$
^Euler-equation-principal-frame

where $\omega_i$ and $L_j$ are components expressed in the body frame of the inertial vectors $\dot{\bmo}$ and $\bmL_c$.

For an axially symmetric body with transverse inertia $I_T = I_{11} = I_{22}$, this can be further simplified to
$$
\begin{aligned}
I_T \dot{\omega}_1 &= - (I_{33}-I_T)\omega_2 \omega_3 \\
I_T \dot{\omega}_2 &= (I_{33}-I_T)\omega_3 \omega_1 \\
I_{33} \dot{\omega}_3 &= 0
\end{aligned}
\tag{4.34}
$$
This can be solved analytically. And with analytical solutions, we can analyze the different procession behaviors of prolate and oblate bodies. (Refer to textbook Sec. 4.2.3)

Later, the same problem will be discussed in a more geometric perspective using Euler angles (refer to textbook Sec. 4.3.3, or lecture note section [[#Special Discussions About Axisymmetric Rigid Body]] later).



## Example 4.4: dual-gimbal gyroscope
![[fig-4-6_dual_gimbal_gyro.png|400]] ![[fig-dual_gimbal_gyro_more_realistic.png|200]]

Inertial frame $\calI: \{\iht1,\iht2,\iht3\}$ \
Gimbal frame $\calG: \{\ght1,\ght2,\ght3\}$ \
Wheel/disk frame $\calW: \{\wht1,\wht2,\wht3\}$

Angular velocities: \
$\bmo_{\calW/\calG} = \omega_s \wht3 = \omega_s \ght3$ \
$\bmo_{\calG/\calI} = \dot{\phi}\iht3 + \dot{\theta}\ght1 = \omega_p\iht3 + \omega_n\ght1$

Since we want to expand $\iht3$ using $\calG$ basis, we need the DCM from $\calI$ to $\calG$, which is obtained by first a rotation of $\phi$ around $\iht1$ and then a rotation around of $\theta$ around $\ght1$:
$$
\begin{aligned}
\dcm{GI} = \dcm{M_1(\theta)} \dcm{M_3(\phi)} &= \dcmOne{\theta} \dcmThree{\phi} \\
%
&= \bmt{\cos \phi & \sin \phi & 0 \\
- \cos\theta \sin \phi & \cos\theta \cos \phi & \sin\theta \\
\sin \phi \sin\theta & - \sin\theta \cos \phi & \cos\theta}
\end{aligned}
$$
Therefore we have 
$$
\iht3 = \sin\theta \ght2 + \cos\theta\ght3
$$
and the gimbal angular velocity is
$$
\bmo_{\calG/\calI} = \omega_n\ght1 + \omega_p \sin\theta\ght2 + \omega_p\cos\theta\ght3
$$
and the wheel angular velocity is
$$
\bmo_{\calW/\calI} = \bmo_{\calW/\calG} + \bmo_{\calG/\calI} = \omega_n\ght1 + \omega_p \sin\theta\ght2 + (\omega_s+\omega_p \cos\theta)\ght3
$$

The wheel inertia in the gimbal frame $\calG$ is diagonal,
$$
\dot{\bmH} = \bmt{I_W} \ddtG \bmo_{\calW/\calI} + \bmo_{\calG/\calI} \times (\bmt{I_W} \bmo_{\calW/\calI})
$$

> [!Notice]- Here, the two angular velocity terms in the second term are not the same. Directly applying Euler's rotational equation of motion will be wrong. 
> See %% the wrong %% derivations below:
> $$
> \begin{align}
> \bmH &= \bmt{I_W} \bmo_{\calW/\calI} \\
> \ddtN \bmH &= \bmt{I_W} \ddtN \bmH = \bmt{I_W} \ddtG \bmo_{\calW/\calI} + \bmt{I_W} \bmo_{\calG/\calI} \times \bmo_{\calW/\calI} \\
> \end{align}
> $$
> 
> The correct one: 
> $$
> \begin{aligned}
> \bmH &= \bmt{I_W} \bmo_{\calW/\calI} \\
> \ddtN \bmH &= \ddtN \left( \bmt{I_W} \bmo_{\calW/\calI} \right) = \ddtG \left( \bmt{I_W} \bmo_{\calW/\calI} \right) + \bmo_{\calG/\calI} \times \left( \bmt{I_W} \bmo_{\calW/\calI} \right)
> \end{aligned}
> $$

The first term without $\bmt{I_W}$ is:
$$
\begin{aligned}
\ddtG \bmo_{\calW/\calI}
&= \ddtG \left( \omega_n\ght1 + \omega_p \sin\theta\ght2 + (\omega_s+\omega_p\cos\theta)\ght3 \right) \\
%
&= \dot{\omega}_n\ght1 + \ddtG(\omega_p \sin\theta)\ght2 + \ddtG(\omega_s+\omega_p\cos\theta)\ght3 \\
%
&= \dot{\omega}_n\ght1 + (\dot{\omega}_p \sin\theta  + \omega_p \dot{\theta} \cos\theta)\ght2 + (\dot{\omega}_s + \dot{\omega}_p\cos\theta-\omega_p \dot{\theta}\sin\theta)\ght3  \\
%
&= \dot{\omega}_n\ght1 + (\dot{\omega}_p \sin\theta + \omega_p \omega_n \cos\theta)\ght2 + (\dot{\omega}_s + \dot{\omega}_p\cos\theta-\omega_p \omega_n\sin\theta)\ght3
\end{aligned}
$$

The second term is:
$$
\begin{aligned}
\bmo_{\calG/\calI} \times (\bmt{I_W} \bmo_{\calW/\calI}) 
&= (\omega_n\ght1 + \omega_p \sin\theta\ght2 + \omega_p\cos\theta\ght3) \times (I_1\omega_n\ght1 + I_2 \omega_p  \sin\theta\ght2 + I_3 (\omega_s+\omega_p\cos\theta)\ght3) \\
&= I_2\omega_n\omega_p \sin\theta\ght3 - I_3\omega_n(\omega_s+\omega_p\cos\theta)\ght2 \\
&\phantom{=,}- I_1\omega_p\omega_n \sin\theta\ght3 + I_3\omega_p(\omega_s+\omega_p\cos\theta) \sin\theta\ght1\\
&\phantom{=,}+ I_1\omega_p\omega_n\cos\theta\ght2 - I_2\omega_p^2\cos\theta \sin\theta\ght1

\end{aligned}
$$

The total torque from all the rotors (along each $\calG$ frame axis) is
$$
\bmL = L_1 \ght1 + L_2 \ght2 + L_3 \ght3
$$

Equating everything gives:
$$
\begin{aligned}
L_1 &= I_1\dot{\omega}_n + I_3\omega_p(\omega_s+\omega_p\cos\theta) \sin\theta - I_2\omega_p^2\cos\theta  \sin\theta \\
L_2 &= I_2( \dot{\omega}_p \sin\theta + \omega_p \omega_n \cos\theta ) - I_3\omega_n(\omega_s+\omega_p\cos\theta) + I_1\omega_p\omega_n\cos\theta \\
L_3 &= I_3( \dot{\omega}_s + \dot{\omega}_p\cos\theta-\omega_p \omega_n\sin\theta ) + I_2\omega_n\omega_p \sin\theta - I_1\omega_p\omega_n \sin\theta
\end{aligned}
$$

Next, solve first-order ODEs numerically. ODE integration omitted here.

## Textbook problem 4.10 (cylinder in gyroscope)

![[fig-p4-10_solid_cylinder_in_gyro.png|500]]

Defining the body frame $\{\bht{}\}$ as shown in the figure:\
![[fig-p4-10_solid_cylinder_in_gyro_with_axis.png|400]] where $\bht{1}$ is pointing towards the back.

### (a) natural frequency around $\theta=\pi/2$
The cylinder's transversal inertias $I_t$ and axial inertia $I_a$ are given by
$$
I_t = \frac{m}{12}(3a^2+l^2) = I_{11} = I_{33}
$$
$$
I_a = \frac{m}{2} a^2 = I_{22}
$$

Angular velocity vector due to the prescribed gimbal motion and the rotation around $B$-$B'$ axle:
$$
\begin{aligned}
\bmo &= &\omega_1 &\bht1 +& \omega_2 &\bht2 +& \omega_3 &\bht3 \\
&= &\sin\theta \Omega &\bht1 +& \cos\theta \Omega &\bht2 +& \dot{\theta}&\bht3
\end{aligned}
$$

Using the Euler equation derived before
![[#^Euler-equation-principal-frame]]
we have,
$$
I_t \dot{\omega}_3 = - (I_a - I_t) \omega_1 \omega_2 + 0
$$
$$
\ddot{\theta} = \frac{I_t-I_a}{I_t} \sin\theta \cos\theta \Omega^2 = \frac{I_t-I_a}{2I_t} \Omega^2 \sin(2\theta)
$$

The frequency of small oscillations at $\theta=\pi/2$ means the linear frequency around the equilibrium $\theta=\pi/2$, so we can do a variationally analysis by plugging in $\theta+\delta\theta$ and expand using Taylor series around $\theta=\pi/2$, which leads to:
$$
\ddot{\delta\theta} = 0 + \left. \frac{I_t-I_a}{2I_t} \Omega^2 2 \cos(2\theta) \right|_{\pi/2} \delta\theta + O(\delta\theta^2) = \frac{I_t-I_a}{I_t} \Omega^2 \delta\theta + O(\delta\theta^2)
$$

Upon checking that $I_t - I_a = \frac{m}{12}(3a^2+l^2) - \frac{m}{2} a^2 = \frac{m}{12}(l^2-3a^2) > 0$, we know that the solution to the first-order approximation will be a trigonometric (harmonic) function with a natural frequency $\omega_n$ of
$$
\omega_n = \sqrt{ \frac{I_t-I_a}{I_t} \Omega^2 } 
=  \Omega \sqrt{\frac{\frac{m}{12}(3a^2+l^2) - \frac{m}{2} a^2}{\frac{m}{12}(3a^2+l^2)}}
=  \Omega \sqrt{ \frac{l^2-3a^2}{l^2+3a^2} }
$$

### (b) final angular velocity starting from $\theta=0$

We will integrate the equations of motion to get the history of the angular motion of $\theta$. 

Multiple $\dot{\theta}$ at both size and do a definite integral:
$$
\begin{aligned}
\text{LHS} &= \int_0^{t} \ddot{\theta} \dot{\theta} dt = \int_\theta^{\theta(t)} \ddot{\theta} d\theta \\
\text{RHS} &= \int_0^{t} \frac{k}{2} \sin(2\theta) \dot{\theta} dt = \int_0^{\theta(t)} \frac{k}{2} \sin(2\theta) d\theta
\end{aligned}
$$
where $k=\omega_n^2={ \frac{l^2-3a^2}{l^2+3a^2} } \Omega^2$ as a shorthand.

So,
$$
\frac{\dot{\theta}^2}{2} \Bigg|_0^{t} = \frac{\dot{\theta}^2(t)}{2} = \frac{k}{4} \cos(2\theta) \Bigg|_0^{\theta(t)} = \frac{k}{4} \left( 1 - \cos(2\theta(t)) \right)
$$ 
$$
\dot{\theta}(t)^2 = \frac{k}{2} ( 1 - \cos(2\theta(t)))
$$

At $\theta_f = \theta(t_f) = \pi/2$, we have
$$
\dot{\theta}_f = \dot{\theta}(t_f) = \sqrt{ \frac{k}{2} } (1 - (-1)) = \sqrt{ k } = \Omega \sqrt{ \frac{l^2-3a^2}{l^2+3a^2} }
$$


> [!Question]- Open question: Why does the problem need the assumption that $l \ge \sqrt{ 3 } a$?
> Hint: It impacts ratio of $I_t$ and $I_a$.







## Rotational Kinetic Energy

The rigid body rotational kinetic energy expression as
$$
T_\text{rot} = \frac{1}{2} \bmo \cdot \bmH_c = \frac{1}{2} \bmo\trans \bmt{I}~\bmo
\tag{4.52}
$$

The work done by the torque $\bmL_c$ onto a rigid body $\calB$
$$
\dot{T}_\text{rot} = \frac{1}{2} \dot{\bmo} \cdot \bmH_c + \frac{1}{2} \bmo \cdot \dot{\bmH}_c
= \frac{1}{2} \dot{\bmo} \cdot \bmH_c + \frac{1}{2} \bmo \cdot \bmL_c
\tag{4.54 and 4.55}
$$
$$
\dot{T}_\text{rot} = \dot{\bmo}\trans[I]\bmo = \bmo \cdot \bmL_c
\tag{4.56}
$$
where $\bmL_c = \dot{\bmH}_c = \bmt{I} ~ \dot{\bmo} + \bmo\times(\bmt{I}~\bmo)$ is the Euler's rotational equation of motion, as given in Eq. (4.32 alternative).



The total kinetic energy of a rigid body B is the sum of translational and rotational energy
$$
T = \frac{1}{2}M \dot{\bmR}_c \cdot \dot{\bmR}_c + \frac{1}{2} \bmo \cdot \bmH_c = \frac{1}{2}M \dot{\bmR}_c \cdot \dot{\bmR}_c + \frac{1}{2} \bmo\trans \bmt{I}~\bmo
\tag{4.53}
$$

The total kinetic energy rate or power is then given by
$$
\dot{\bm{T}} = \bmF \cdot \dot{\bmR}_c + \bmL_c \cdot \bmo
\tag{4.57}
$$




## Torque-Free Rigid Body Rotation (a geometric approach)

If no external torques $\bmL_c$ are acting on a system, the total angular momentum vector $\bmH$ is constant in the inertial frame, and the total rotational kinetic energy $T$ (dropped subscription "rot" from $T_\text{rot}$ as a shorthand) is also a constant.

When expressed in body frame $\calB$, the angular momentum vector $\bmH$ will generally not appear to be constant but rotating. However, the angular momentum magnitude $H$ is still a constant.

**Principal axes assumption**: We always assume that the body-fixed coordinate axes are all aligned with principal inertia axes.

(In the space of $\{\omega_1, \omega_2, \omega_3\}$)
Using coordinates of the angular momentum $\bmH$ and angular velocity $\bmo$ in body frame $\calB$, we have the angular momentum ellipsoid as
$$
H^2 = H_1^2 + H_2^2 + H_3^2 = I_1^2\omega_1^2 + I_2^2\omega_2^2 + I_3^2\omega_3^2
\tag{4.64 and 4.62}
$$
and the energy ellipsoid as
$$
T = \frac{1}{2} (I_1\omega_1^2 + I_2\omega_2^2 + I_3\omega_3^2)
\tag{4.63}
$$
The geometric interpretation of this is that $\bmo(t)$ must lie on the intersection of the momentum and energy ellipsoid surfaces.

(In the space of $\{H_1, H_2, H_3\}$)
To simplify one ellipsoid to a sphere, using $H_i$ as independent coordinates, so we have the momentum sphere 
$$
H^2 = H_1^2 + H_2^2 + H_3^2
\tag{4.64}
$$
and the energy ellipsoid (substituting $\omega_i$ with $H_i/I_i$)
$$
T = \frac{H_1^2}{2I_1} + \frac{H_2^2}{2I_2} + \frac{H_3^2}{2I_3}
\tag{4.65 altered}
$$
![[fig-4-8_intersection_of_ellipsoids.png|400]]
Further requiring
$$
I_1 \ge I_2 \ge I_3
\tag{Important!}
$$
the largest ellipsoid semi-axis occurs along $\bht1$ and the smallest along $\bht3$. 
The overall shape and aspect ratio of the ellipsoid will remain the same for each choice in the energy $T$, and varying $T$ will only uniformly scale the ellipsoid.

For a general rigid body motion as shown in Fig. 4.8, once the initial kinetic energy $T$ and angular momentum vector $\bmH$ are established, the angular velocity vector x will theoretically trace out a particular intersection curve forever.


![[fig-4-9_intersection_of_ellipsoids.png|400]]


- For this minimum kinetic energy case, the rigid body B is spinning purely about its axis of maximum inertia $\bm{b}_1$, and the corresponding kinetic energy is
$$
T_\text{min} = \frac{H^2}{2I_1}
$$

- For the intermediate kinetic energy case, the kinetic energy along the separatrix is
$$
T_\text{intermediate} = \frac{H^2}{2I_2}
$$

- For the maximum kinetic energy case, the rotation is along $\bht3$, and
$$
T_\text{max} = \frac{H^2}{2I_3}
$$


![[fig-4-10_family_of_intersections.png|400]]
All feasible $\bmo(t)$ paths form closed trajectories.
The energy is not conserved in reality and will dissipate, so the motion will wobble along $\bht3$ when the energy is higher than that on the separatrix, then wobble along $\bht2$ after crossing the separatrix, and eventually stabilized and slows down along $\bht1$.

Dancing T-handle in zero-g, HD: https://youtu.be/1n-HMSCDYtM?si=FDVAI-HH0qQMOA9l





## Special Discussions on Axisymmetric Rigid Body

Without loss of generality, assume that $I_2 = I_3$. Then the yaw, pitch, and roll angle rates are given as (see Section 4.3.3 for the derivations)
$$
\begin{aligned}
\dot{\psi} &= - \frac{H}{I_2} \\
\dot{\theta} &= 0 \\
\dot{\phi} &= H \left( \frac{I_2 - I_1}{I_1 I_2} \right) \sin \theta \\
\end{aligned}
\tag{4.77}
$$

![[fig-4-12_angular_velocity_mometum_vectors.png|400]]
![[fig-4-13_space_and_body_cones.png|500]]
Using a (3-2-1) Euler angle set, i.e. yaw-pitch-roll set, the precession motion of oblate (disk) or prolate (stick) bodies.
![[fig-oblate_vs_prolate.png]]

Details omitted, please study the textbook section 4.3.3.


## Dynamics of Dual-Spin Spacecraft (or Reaction Wheels)

### Equations of motion

The dual-spin spacecraft is a simple system where passive attitude stability is achieved by adding a single fly-wheel to the rigid spacecraft.

![[fig-4-15_dual_spin_sc.png|400]]
To develop the dual-spin system equations of motion, assume that the rotating fly-wheel is aligned with the first principal axis $\bht1$ of the main spacecraft component as illustrated in Fig. 4.15. 

Let $\bmo = \bmo_{\calB/\calN}$ be the body angular velocity of the main craft, while $\bmo_{\calW/\calB}= \Omega \bht1$ is the angular velocity of the fly-wheel relative to the spacecraft. 

The total angular momentum is then given by
$$
\bmH = \bmt{I_s} \bmo + \bmt{I_W} (\Omega \bht1 + \bmo)
\tag{4.82}
$$
where $\bmt{I_s}$ is <u>the inertia matrix of the main spacecraft system</u>, while $\bmt{I_W}$ is the inertia of the fly-wheel component. Notice that we haven't specify the coordinate system used to work out inertia matrices yet.

>[!warning] $\bmt{I_s}$ doesn't include $\bmt{I_W}$ in Eq. (4.82).

Using Euler's equation $\dot{\bmH} = \bmL$, we have
$$
\dot{\bm{H}} = \bm{L} = (\bmt{I_s} + \bmt{I_W})\dot{\bmo} + [\bm{\tilde{\omega}}](\bmt{I_s} + \bmt{I_W})\bmo + \bmt{I_W}(\dot{{\Omega}}\bm{\hat{b}}_1) + [\bm{\tilde{\omega}}]\bmt{I_W}({\Omega}\bm{\hat{b}}_1)
\tag{4.83}
$$

<u>Assuming no external torque</u> is present, and the body frame is principal,
$$
\newcommand{\colo}{\bmt{\omega_1\\ \omega_2\\ \omega_3}}
\newcommand{\Ithree}{\bmt{I_1 & 0 & 0 \\ 0 & I_2 & 0 \\ 0 & 0 & I_3}}
\bm{0} = \Ithree \bmt{\dot{\omega}_1\\ \dot{\omega}_2\\ \dot{\omega}_3} + \skewmt{\omega} \Ithree \colo + \diagmt{I_{W_s}}{I_{W_t}}{I_{W_t}} \dot{\Omega} \bmt{1\\0\\0} + \skewmt{\omega} \diagmt{I_{W_s}}{I_{W_t}}{I_{W_t}} \Omega \bmt{1\\0\\0}
$$
Notice that $\bmt{I_s}$ is diagonal because we use the main craft's principal body frame, and $\bmt{I_W}$ is diagonal because its principal body frame happens to be aligned with that of the main craft.

Inspect each components and we have
$$
\begin{aligned}
& I_1 \dot{\omega}_1 - \omega_3 \omega_2 I_2 + \omega_2 \omega_3 I_3 + I_{W_s} \dot{\Omega} = 0  \\
& I_2 \dot{\omega}_2 + \omega_3 \omega_1 I_1 - \omega_1 \omega_3 I_3 + I_{W_s} \omega_3 \Omega = 0 \\
& I_3 \dot{\omega}_3 - \omega_2 \omega_1 I_1 + \omega_1 \omega_2 I_2 - I_{W_s} \omega_2 \Omega = 0
\end{aligned}
$$

Move all the derivatives to the LHS and we have
$$
\begin{aligned}
I_1 \dot{\omega}_1 &= (I_2 - I_3) \omega_2 \omega_3 - I_{W_s} \dot{\Omega}   \\
I_2 \dot{\omega}_2 &= (I_3 - I_1) \omega_1 \omega_3 - I_{W_s} \omega_3 \Omega  \\
I_3 \dot{\omega}_3 &= (I_1 - I_2) \omega_1 \omega_2 + I_{W_s} \omega_2 \Omega 
\end{aligned}
\tag{4.85}
$$

For the dual-spin spacecraft concept, the spin rate $\Omega$ is typically held at a constant value, so we can eliminate $\dot{\Omega}$ and get
$$
\begin{aligned}
I_1 \dot{\omega}_1 &= (I_2 - I_3) \omega_2 \omega_3  \\
I_2 \dot{\omega}_2 &= (I_3 - I_1) \omega_1 \omega_3 - I_{W_s} \omega_3 \Omega  \\
I_3 \dot{\omega}_3 &= (I_1 - I_2) \omega_1 \omega_2 + I_{W_s} \omega_2 \Omega 
\end{aligned}
\tag{4.86 dual-spin S/C}
$$
### Linear stability analysis

The equilibrium point of the system is find by setting $\dot{\bmo}$ to $\bm{0}$. 
It is apparent from Eq. (4.86) that the only equilibrium spin configuration $\bmo_e$ (meaning $\bmo$ is time-invariant) is when both $\omega_2$ and $\omega_3$ are zero
$$
\bmo_e = \omega_{e_1} \bht1
\tag{4.87}
$$


<u>Linear stability analysis</u> around the equilibrium point for a dual-spin S/C.
Let the actual angular velocity be given by
$$
\bmo = \bmo_e + \delta\bmo = \cdB{\bmt{\omega_{e_1}+\delta\omega_1 \\ \delta\omega_2 \\ \delta\omega_3}}
\tag{4.88 expanded}
$$
then substituting into Eq. (4.86) and dropping higher-order (nonlinear) terms to get
$$
\begin{align}
\dot{\delta \omega_1} &= 0   \tag{4.89a} \\
\dot{\delta \omega_2} &= \left( \frac{I_3-I_1}{I_2} \omega_{e_1} - \frac{I_{W_s}}{I_2} \Omega \right) \delta\omega_3  \tag{4.89b} \\
\dot{\delta \omega_3} &= \left( \frac{I_1-I_2}{I_3} \omega_{e_1} + \frac{I_{W_s}}{I_3} \Omega \right) \delta\omega_2 \\
\end{align}
$$

Eq. (4.89a) tells $\delta\omega_1$ is constant, and thus $\omega_{e_1} + \delta\omega_1$ along $\bht1$ is also constant.

Rewrite the two coupled first-order differential equations into two uncoupled second-order differential equations, by taking derivative of Eq. (4.89b):
$$
\begin{aligned}
\ddot{\delta \omega_2} &= \left( \frac{\textcolor{red}{ I_3-I_1 }}{I_2} \omega_{e_1} - \frac{I_{W_s}}{I_2} \Omega \right) \textcolor{blue}{ \dot{\delta \omega_3} }  \\
&= \textcolor{red}{ - } \left( \frac{\textcolor{red}{ I_1 - I_3 }}{I_2} \omega_{e_1} \textcolor{red}{ + } \frac{I_{W_s}}{I_2} \Omega \right) \textcolor{blue}{ \left( \frac{I_1 - I_2}{I_3} \omega_{e_1} + \frac{I_{W_s}}{I_3} \Omega \right) \delta \omega_2 } \\
&= - \frac{\omega_{e_1}^2}{I_2 I_3}   \left( I_1 - I_3 + I_{W_s} \frac{\Omega}{\omega_{e_1}} \right)   \left( I_1 - I_2 + I_{W_s} \frac{\Omega}{\omega_{e_1}} \right)    \delta\omega_2 \\
&= - \frac{\omega_{e_1}^2}{I_2 I_3}   \left( I_1 - I_3 + I_{W_s} \hat{\Omega} \right)   \left( I_1 - I_2 + I_{W_s} \hat{\Omega} \right)    \delta\omega_2 \\
\end{aligned}
\tag{4.92--95 combined}
$$
If and only if the factor is negative, the system is linearly stable (when the solution is a harmonic (trigonometric) function, otherwise it's exponential function).

With that, two critical wheel speeds $\Omega$ are identified as:
$$
\begin{align}
\hat{\Omega}_1 = \frac{I_3 - I_1}{I_{W_s}}  \tag{leads 1st term to 0}  \\
\hat{\Omega}_2 = \frac{I_2 - I_1}{I_{W_s}}  \tag{leads 2nd term to 0}  \\ 
\end{align}
$$

![[fig-4-16_stability_ranges_in_shades.png|400]]
A lot of interesting discussions can be conducted about this results, please check the textbook.
Basically, when the wheel is spinning fast enough and governs the ratio of $H_1, H_2, H_3$, it can change the intersection curve of the energy ellipsoid and momentum sphere. 

>[!info] Revisit Fig. 4.9 
> 
> ![[fig-4-9_intersection_of_ellipsoids.png|400]] \
> 
> For a rigid body, its distribution of $\bmH$ along three principal axes is determined by the inertia $I_1, I_2, I_3$.
> But for a dual-spin S/C, it can increase a particular $H_i$ without affecting the other two components much. 
> Therefore, even for the intermediate energy case in (b), the wheel can spin up fast enough to blow up the ellipsoid along $\bht2$ or $H_2$ direction until it becomes the minimum energy case in (a). 
> Note that when the ellipsoid is being blown up, the energy sphere is also increasing.








## Dynamics of Multiple Control Moment Gyroscopes (CMGs)

Instead of using thrusters to perform precise spacecraft attitude maneuvers, typically control moment gyroscopes (CMGs) or reaction wheels (RWs) are used. Either device can change its internal angular momentum vector and thus, through Euler’s equation, produce an effective torque on the spacecraft. 

<u>A single-gimbal CMG</u> contains a wheel spinning at a constant rate. To exert a torque onto the spacecraft, this wheel is gimbaled or rotated about a fixed axis. A separate feedback control loop is used to spin up the rotor to the required spin rate and maintain it. 
The <u>advantage of a CMG</u> is that a relatively small gimbal torque input is required to produce a large effective torque output on the spacecraft.
The <u>drawback of the single-gimbal CMGs</u> is that their control laws can be fairly complex and that such CMG systems encounter certain singular gimbal angle configurations. At these singular configurations the CMG cluster is unable to produce the required torque exactly, or any torque at all if the required torque is orthogonal to the plane of allowable torques. 
Double-gimbal CMGs have fewer problems with singularities. However, they are also much more costly and complicated devices than the single-gimbal CMGs.

<u>Reaction wheels</u>, on the other hand, have a wheel spinning about a body-fixed axis whose spin speed is variable. Torques are produced on the spacecraft by accelerating or decelerating the reaction wheels. RW systems do not have singular configurations and typically have simpler control laws than CMG clusters. 
<u>Drawbacks to the reaction wheels</u> include a relatively small effective torque being produced on the spacecraft and the possible reaction wheel saturation. To exert a given torque onto a spacecraft, reaction wheels typically require more energy than CMGs.

<u>Variable speed control moment gyroscopes (VSCMGs) combine positive
features of both the single-gimbal CMGs and the RWs.</u> 

%% This section will first develop the equations of motion of a spacecraft containing VSCMGs using Euler’s equation. The result- ing formulation contains the two classical cases of having either pure RWs or CMGs. %%

![[fig-4-17_VSCMG.png|400]]

**Set up frames and their relationship.** \
The reference frame is the spacecraft body frame $\calB$ (usually the principal inertia frame).

Gimbal frame $\calG: \{\ght{s},\ght{t},\ght{g}\}$, where the <u>gimbal axis</u> $\ght{g}$ is fixed in $\calB$, and the spin axis $\ght{s}$ and the transverse axis $\ght{t}$ are time varying in $\calB$ described by the gimbal angle angle $\gamma(t)$. $\calG$ is aligned with the gimbal principal inertia axes.

The wheel frame $\calW: \{\wht{1},\wht2,\ght{s}\}$, where the 3rd axis is aligned with $\calG$.

The spinning angular velocity vector of the wheel is $\bmo_{\calW/\calG}=\Omega\ght{s}$.

The angular velocity vector of the gimbal frame $\calG$ is $\bmo_{\calG/\calB}=\dot{\gamma}\ght{g}$.

The angular velocity vector of the S/C is $\bmo_{\calB/\calN} = \omega_s \ght{s} + \omega_t \ght{t} + \omega_g \ght{g}$, which is expressed in the gimble frame for convenience in the following derivations.

**Determine inertial matrices.** \
Given an initial gimbal angle $\gamma_0$, we have the evolution of spin and transverse axes as
$$
\begin{aligned}
\ght{s}(t) &= \cos(\gamma(t)-\gamma_0)\,\ght{s}(t_0) + \sin(\gamma(t)-\gamma_0)\,\ght{t}(t_0) \\
\ght{t}(t) &= -\sin(\gamma(t)-\gamma_0)\,\ght{s}(t_0) + \cos(\gamma(t)-\gamma_0)\,\ght{t}(t_0)
\end{aligned}
$$
which can be explained as simply a elementary rotation along the 3rd axis, indicating a matrix multiplication using $M_3(\gamma(t)-\gamma_0)$.

Gimbal frame inertial matrix is $\cdG{\bmt{I_G}} = \cdG{\diagmt{I_{G_s}}{I_{G_t}}{I_{G_g}}}$.

The reaction wheel inertia about the same axes is $\cdG{\bmt{I_W}} = \cdG{\diagmt{I_{W_s}}{I_{W_t}}{I_{W_t}}}$.

> In this development the RW and gimbal frame inertias are not combined early on into one overall VSCMG inertia matrix; rather, they are retained as separate entities until later in the development. This will allow for a precise formulation of the actual physical motor torques that drive the RWs or the CMGs.

Assuming that the coordinate of each gimbal frame vector is given in $\calB$, we have the DCM of $\calG$ relative to $\calB$ as
$$
\{\ght{}\} = \dcm{GB} \{\bht{}\} = \bmt{ \cdB{(\ght{s})}\trans \\ \cdB{(\ght{t})}\trans \\ \cdB{(\ght{g}})} \{\bht{}\}
$$
which gives the reversed conversion, i.e., the DCM of $\calB$ relative to $\calG$, as
$$
\dcm{BG} = \bmt{ \cdB{(\ght{s})} & \cdB{(\ght{t})} & \cdB{(\ght{g}})}.
$$

The inertia matrices of the gimbal frame and the reaction wheel in the body frame $\calB$ can be found by transforming the inertia matrices in $\calG$ using the DCM $\dcm{BG}$, as following,
$$
\begin{aligned}
\cdB{\bmt{I_G}} &= \dcm{BG} \cdot \cdG{\bmt{I_G}} \cdot \dcm{BG}\trans = I_{G_s} \ght{s}\ght{s}\trans + I_{G_t} \ght{t}\ght{t}\trans + I_{G_g} \ght{g}\ght{g}\trans  \\
\cdB{\bmt{I_W}} &= \dcm{BG} \cdot \cdG{\bmt{I_W}} \cdot \dcm{BG}\trans = I_{W_s} \ght{s}\ght{s}\trans + I_{W_t} \ght{t}\ght{t}\trans + I_{W_t} \ght{g}\ght{g}\trans
\end{aligned}
\tag{4.105 and 4.106}
$$
^VSCMG-I-body-frame

Notice that $\cdB{\bmt{I_G}}$ and $\cdB{\bmt{I_W}}$ are time-varying now because the gimbal frame $\calG$ is time-varying.

### Part-1, write out total angular momentum $\bmH$
>[!tip] (Part-1) Now, find the total angular momentum as a summation of angular momentums of three parts: 
> - (body) S/C with a mass-point VSCMG, 
> - (gimbal) the gimbal frame of VSCMG, 
> - (wheel) the wheel of VSCMG.

The total angular momentum $\bmH$ of the spacecraft and the VSCMG (frame and wheel) about the spacecraft center of mass is given by
$$
\bmH = \bmH_B + \bmH_G + \bmH_W
\tag{4.107}
$$

^total-H-VSCMG

The angular momentum component $\bmH_B$ of spacecraft and a static VSCMG is
$$
\bmH_B = \bmt{I_s} \, \bmo_{\calB/\calN}
\tag{4.109}
$$
where $\bmt{I_s}$ is the S/C (without VSCMG) inertia matrix and the mass-point VSCMG inertia components.

The component $\bmH_G$ of the gimbal frame is
$$
\begin{align}
\bmH_G &= \bmt{I_G} \, \bmo_{\calG/\calN}    \tag{4.109} \\
&= \bmt{I_G} \cdot (\bmo_{\calG/\calB} + \bmo_{\calB/\calN})     \\
&= (I_{G_s} \ght{s}\ght{s}\trans + I_{G_t} \ght{t}\ght{t}\trans + I_{G_g} \ght{g}\ght{g}\trans) \cdot (\dot{\gamma}\ght{g} + \omega_s \ght{s} + \omega_t \ght{t} + \omega_g \ght{g})    \tag{used 4.105} \\

&= \dot{\gamma}I_{G_g} \ght{g} + \omega_sI_{G_s} \ght{s} + \omega_t I_{G_t} \ght{t} + \omega_g I_{G_g} \ght{g}   \\
&= \omega_sI_{G_s} \ght{s} + \omega_t I_{G_t} \ght{t} + (\omega_g + \dot{\gamma})I_{G_g} \ght{g}   \tag{4.112}
\end{align}
$$
(*Notice*: after the third line above, all vectors must be calculated in the body frame $\calB$, because $\bmt{I_G}$ is assumed to be expressed in $\calB$ now.)

The component $\bmH_W$ of the reaction wheel (RW) is obtained similarly as
$$
\begin{align}
\bmH_W &= \bmt{I_W} \, \bmo_{\calW/\calN}    \tag{4.113}  \\
&= \bmt{I_W} \cdot (\bmo_{\calW/\calG} + \bmo_{\calG/\calB} + \bmo_{\calB/\calN})    \\
&= (I_{W_s} \ght{s}\ght{s}\trans + I_{W_t} \ght{t}\ght{t}\trans + I_{W_t} \ght{g}\ght{g}\trans) \cdot (\Omega\ght{s} + \dot{\gamma}\ght{g} + \omega_s \ght{s} + \omega_t \ght{t} + \omega_g \ght{g})   \tag{used 4.106}  \\
&= \Omega I_{W_s} \ght{s} + \dot{\gamma} I_{W_t} \ght{g} + \omega_s I_{W_s} \ght{s} + \omega_t I_{W_t} \ght{t} + \omega_g I_{W_t} \ght{g}    \\
&= (\Omega + \omega_s) I_{W_s} \ght{s}  + \omega_t I_{W_t} \ght{t} + (\dot{\gamma} + \omega_g) I_{W_t} \ght{g}   \tag{4.114}
\end{align}
$$
(*Notice*: similarly after the third line above, all vectors must be calculated in the body frame $\calB$, because $\bmt{I_G}$ is assumed to be expressed in $\calB$ now.)


### Part-2, find necessary derivatives
>[!tip] (Part-2) Now, find inertial derivatives in order to apply Euler's equation of rigid body rotation.

The equations of motion of a system of rigid bodies follow from Euler’s equation
$$
\dot{\bmH} = \bmL
$$

So, we need to find derivative of each angular momentum part of $\bmH$.
![[#^total-H-VSCMG]]

From previous discussions, we know that in order to find $\dot{\bmH}_B, \dot{\bmH}_G, \dot{\bmH}_W$, we will need to find the time derivatives of the basis vectors of the gimble frame $\calG$, and also the derivatives of components $\omega_s,\omega_t,\omega_g$ of the angular velocity $\bmo$ expressed in the gimble frame $\calG$. 

Using the transport theorem twice, we have
$$
\begin{align}
\dot{\ght{}}_s &= \ddtB \ght{s} + \bmo \times \ght{s}  \tag{$\calN \to \calB$} \\
&= \ccancelto{\bm{0}}{\ddtG \ght{s}} + \bmo_{\calG/\calB} \times \ght{s} + \bmo \times \ght{s}  \tag{$\calB \to \calG$} \\
&= \dot{\gamma}\ght{g}\times\ght{s} + (\omega_s \ght{s} + \omega_t \ght{t} + \omega_g \ght{g}) \times \ght{s} \\
&= (\dot{\gamma}+\omega_g) \ght{t} - \omega_t \ght{g}
\end{align}
$$
and similarly
$$
\begin{aligned}
\dot{\ght{}}_t &= -(\dot{\gamma}+\omega_g) \ght{s} + \omega_s \ght{g} \\
\dot{\ght{}}_g &= \omega_t \ght{s} - \omega_s \ght{t}
\end{aligned}
\tag{4.117}
$$

Next, the time derivatives of the basis are obtained as (we've dropped subscript $\calB/\calN$ from $\bmo_{\calB/\calN}$)
$$
\begin{aligned}
\dot{\omega}_s &= \ddtN (\bmo \cdot \ght{s}) \\
&= \dot{\bmo} \cdot \ght{s} + \bmo \ddtN\ght{s} \\
&= \ght{s}\trans \dot{\bmo} + (\omega_s \ght{s} + \omega_t \ght{t} + \omega_g \ght{g}) \cdot ((\dot{\gamma}+\omega_g) \ght{t} - \omega_t \ght{g})  \\
&= \ght{s}\trans \dot{\bmo} + (\omega_s \ght{s} + \omega_t \ght{t} + \omega_g \ght{g}) \cdot ((\dot{\gamma}+\omega_g) \ght{t} - \omega_t \ght{g})  \\
&= \ght{s}\trans \dot{\bmo} + \omega_t \dot{\gamma}
\end{aligned}
\tag{4.121a explained}
$$
and similarly
$$
\begin{aligned}
\dot{\omega}_t &= -\dot{\gamma}\omega_s + \ght{t}\trans \dot{\bmo} \\
\dot{\omega}_g &= \ght{g}\trans \dot{\bmo}
\end{aligned}
\tag{4.121b and 4.121c}
$$

Regarding other derivatives, $\dot{\Omega}, \dot{\gamma}, \ddot{\gamma}$ are known from the wheel rotor and the gimble rotor, and $\dot{\bmo}$ is obtained from measurement sensors with proper transformations.

### Part-3, wheel's dynamics
>[!tip] (Part-3) Now, isolating the dynamics of RW.

%% Hidden steps to verify the following results in the textbook.
$$
\dot{\bmH}_W = \ddtN \left[ (\Omega + \omega_s) I_{W_s} \ght{s} + \omega_t I_{W_t} \ght{t} + (\dot{\gamma} + \omega_g) I_{W_t} \ght{g} \right]
$$
Apply product rule to each term:
$$
= (\dot{\Omega}+\dot{\omega}_s)I_{W_s}\ght{s} + (\Omega + \omega_s) I_{W_s} \dot{\ght{}}_s 
+\dot{\omega}_t I_{W_T}\ght{t} + \omega_tI_{W_t}\dot{\ght{}}_t 
+(\ddot{\gamma}+\dot{\omega}_g)I_{W_t}\ght{g} + (\dot{\gamma} + \omega_g) I_{W_t} \dot{\ght{}}_g
$$

Substitute each derivatives we found in part-2:
$$
= (\dot{\Omega}+\ght{s}\trans \dot{\bmo} + \omega_t \dot{\gamma})I_{W_s}\ght{s} 
+ (\Omega + \omega_s) I_{W_s} ((\dot{\gamma}+\omega_g) \ght{t} - \omega_t \ght{g})
+ (-\dot{\gamma}\omega_s + \ght{t}\trans \dot{\bmo}) I_{W_T}\ght{t} 
+ \omega_t I_{W_t} (-(\dot{\gamma}+\omega_g) \ght{s} + \omega_s \ght{g}) 
+ (\ddot{\gamma}+\ght{g}\trans \dot{\bmo})I_{W_t}\ght{g} 
+ (\dot{\gamma} + \omega_g) I_{W_t} (\omega_t \ght{s} - \omega_s \ght{t})
$$

Copy and paste the above line, and organize terms by eliminating everything not containing $\ght{s}$ (paying attention to how the source code is organized to write product in one line to make this process less error-prone.)
$$
\text{(terms with $\ght{s}$)} = (\dot{\Omega}+\ght{s}\trans \dot{\bmo} + \omega_t \dot{\gamma})I_{W_s}\ght{s} 
+ \omega_t I_{W_t} (-(\dot{\gamma}+\omega_g) \ght{s} ) 
+ (\dot{\gamma} + \omega_g) I_{W_t} (\omega_t \ght{s} )

= I_{W_s}(\dot{\Omega} + \hat{\bm{g}}_s^T \dot{\bmo} + \dot{\gamma} \omega_t) \cdot \ght{s}
$$
%%

The inertial derivative of $\bmH_W$ is
$$
\begin{aligned}
\dot{\bm{H}}_W
&= \phantom{+}\hat{\bm{g}}_s \left[ I_{W_s}(\dot{\Omega} + \hat{\bm{g}}_s^T \dot{\bmo} + \dot{\gamma} \omega_t) \right] \\
%
&\phantom{=\,} + \hat{\bm{g}}_t \left[ I_{W_s}(\dot{\gamma}({\omega}_s + {\Omega}) + {\Omega} {\omega}_g) + I_{W_t} \hat{\bm{g}}_t^T \dot{\bmo} + (I_{W_s} - I_{W_t}){\omega}_s {\omega}_g - 2 I_{W_t} \omega_s \dot{\gamma} \right] \\
%
&\phantom{=\,} + \hat{\bm{g}}_g \left[I_{W_s}(\hat{\bm{g}}_g^T \dot{\bmo} + \ddot{\gamma})] + (I_{W_t} - I_{W_s})\omega_s{\omega}_t - I_{W_s} {\Omega} {\omega}_t \right] \\
%
&= u_s \ght{s} + u_t \ght{t} + u_g \ght{g}
\end{aligned}
\tag{4.122}
$$

**Resolve the control torque $u_s$:**
Let $\bmL_W$ be the torque the gimbal frame exerts on the RW, <u>applying Euler’s equation only to the RW itself</u> gives:
$$
\dot{\bmH}_W = \bmL_W
$$
Use the auxiliary results derived above in Eq. (4.122), only the spin torque $u_s$ is provided by the RW torque motor which is expressed as
$$
u_s = I_{W_s}(\dot{\Omega} + \hat{\bm{g}}_s^T \dot{\bmo} + \dot{\gamma} \omega_t)
\tag{4.123}
$$
and the other two torques $u_t$ and $u_g$ are produced by the gimbal frame.

Notice: This expression of $u_s$ in Eq. (4.123) actually gives a way to compute the torque applied by the gimble frame rotor and wheel motor.

### Part-4, wheel and gimbal combined dynamics
>[!tip] (Part-4) Now, isolating the RW and the gimbal frame as a whole

The inertial derivative $\dot{\bmH}_G$ is calculated as
$$
\begin{aligned}
\newcommand{\ig}[1]{I_{G_#1}}
\dot{\bmH}_G &= \phantom{+} \ght{s} \left[ (\ig{s}-\ig{t}+\ig{g})\dot{\gamma}\omega_t + \ig{s}\ght{s}\trans\dot{\bmo} + (\ig{g}-\ig{t})\omega_t\omega_g \right] \\
&\phantom{=\,} + \ght{t} \left[ (\ig{s}-\ig{t}-\ig{g})\dot{\gamma}\omega_s + \ig{t}\ght{t}\trans\dot{\bmo} + (\ig{s}-\ig{g}\omega_s\omega_g) \right] \\
&\phantom{=\,} + \ght{g} \left[ \ig{g}(\ght{g}\trans \dot{\bmo} + \ddot{\gamma}) + (\ig{t}-\ig{s})\omega_s\omega_t \right]
\end{aligned}
\tag{4.124}
$$

**Resolve the control torque $u_g$:**
Let $\bmL_G$ be the torque vector that spacecraft exerts on the VSCMG system, <u>applying Euler's equation to the gimble frame and RW as a whole</u> gives:
$$
\dot{\bmH}_G + \dot{\bmH}_W = \bmL_{G}
$$
where $\dot{\bmH}_W$ is given in Eq. (4.122) and $\dot{\bmH}_G$ is given in Eq. (4.124). The torque component of $\bmL_G$ along $\ght{g}$ is produced by the gimbal torque motor, so, adding Eqs. (4.122) and (4.124) and equating the components along $\ght{g}$ gives
$$
u_g = J_g \left( \ght{g}\trans \dot{\bmo} + \ddot{\gamma} \right) - (J_s-J_t) \omega_s \omega_t - I_{W_s} \Omega \omega_t
\tag{4.126}
$$
where we have <u>combined the inertia matrices of RW and the gimbal frame</u> into a single matrix $\bmt{J}$
$$
\cdG{\bmt{J}} = \cdG{\bmt{I_G}} + \cdG{\bmt{I_W}} = \cdG{\diagmt{I_{G_s}+I_{W_s}}{I_{G_t}+I_{W_t}}{I_{G_g}+I_{W_t}}} = \cdG{\diagmt{J_s}{J_t}{J_g}}.
$$

Notice: This expression of $u_g$ in Eq. (4.126) actually gives a way to compute the torque applied by the gimble frame rotor.

### Part-5, S/C and VSCMG combined dynamics
>[!tip] (Part-5) Now, combine everything into Euler's equation.

The inertial derivative $\dot{\bmH}_B$ of the spacecraft with the VSCMG as mass point is calculated easily as
$$
\dot{\bmH}_B = \bmt{I_s} \dot{\bmo} + \bmo \times \bmt{I_s} \bmo
\tag{4.127}
$$

![[#^total-H-VSCMG]]
![[#^Euler-equation-general-vector-format]]

Now, we can plugin all the derivates to the derivative of total angular momentum (spacecraft, gimble, and RW), apply the general Euler's equation, and get the full express as
$$
\begin{align}
&\phantom{=\,} \bmt{I_s} \dot{\bmo} + \bmo \times \bmt{I_s} \bmo   \tag{from $\dot{\bmH}_B$} \\
%
&+ \ght{s} \left[ (\ig{s}-\ig{t}+\ig{g})\dot{\gamma}\omega_t + \ig{s}\ght{s}\trans\dot{\bmo} + (\ig{g}-\ig{t})\omega_t\omega_g \right] \\
& + \ght{t} \left[ (\ig{s}-\ig{t}-\ig{g})\dot{\gamma}\omega_s + \ig{t}\ght{t}\trans\dot{\bmo} + (\ig{s}-\ig{g}\omega_s\omega_g) \right] \\
& + \ght{g} \left[ \ig{g}(\ght{g}\trans \dot{\bmo} + \ddot{\gamma}) + (\ig{t}-\ig{s})\omega_s\omega_t \right]       \tag{from $\dot{\bmH}_G$} \\
%
&+ \hat{\bm{g}}_s \left[ I_{W_s}(\dot{\Omega} + \hat{\bm{g}}_s^T \dot{\bmo} + \dot{\gamma} \omega_t) \right] \\
&+ \hat{\bm{g}}_t \left[ I_{W_s}(\dot{\gamma}({\omega}_s + {\Omega}) + {\Omega} {\omega}_g) + I_{W_t} \hat{\bm{g}}_t^T \dot{\bmo} + (I_{W_s} - I_{W_t}){\omega}_s {\omega}_g - 2 I_{W_t} \omega_s \dot{\gamma} \right] \\
&+ \hat{\bm{g}}_g \left[I_{W_s}(\hat{\bm{g}}_g^T \dot{\bmo} + \ddot{\gamma})] + (I_{W_t} - I_{W_s})\omega_s{\omega}_t - I_{W_s} {\Omega} {\omega}_t \right]    \tag{from $\dot{\bmH}_W$} \\
%
&= \bmL   \tag{External torque}
\end{align}
$$

To simplify the equations of motion, the total spacecraft inertia matrix $\bmt{I}$ is defined as
$$
\cdB{\bmt{I}} = \cdB[{I_s}] + \cdB{\bmt{J}} = \cdB{I_s} + \dcm{BG} \cdot \cdG{\bmt{J}} \cdot \dcm{BG}\trans
\tag{4.128 altered}
$$
which is time-varying in the body frame $\calB$.

<u>**The final equations of motion of a rigid spacecraft with a single VSCMG**</u> are
$$
\begin{aligned}
\bmt{I} \dot{\bmo} = - \bmo \times \bmt{I} \bmo &- \ght{s}\left[ J_s \dot{\gamma} \omega_t + I_{W_s} \dot{\Omega} - (J_t-J_g)\omega_t \dot{\gamma} \right] \\
&- \ght{t} \left[ (J_s\omega_s+I_{W_s}\Omega) \dot{\gamma} - (J_t+J_g) \omega_s \dot{\gamma} + I_{W_s} \Omega \omega_g \right] \\
&- \ght{g} \left[ J_g \ddot{\gamma} - I_{W_s} \Omega \omega_t \right] \\
&+ \bmL
\end{aligned}
\tag{4.129}
$$
(*Notice*: We can verify again that, $\dot{\bmo}$ and $\bmo$ will be expressed in the body frame $\calB$; $\ght{s}, \ght{t}, \ght{g}$ are specified in $\calB$; and $\bmL$ should be given in $\calB$ as well. These are all consistent with the determination of $\bmt{I}, \bmt{I_G}, \bmt{I_W}, \bmt{J}$ in $\calB$.)

**Introducing additional simplifications to simplify the dynamics:**
A common assumption/fact is that the gimbal frame inertial $I_{G_s}$ about the spin axis is negligible. 
Because the frame is usually designed as lightweight as possible to avoid interfering with the spinning wheel.
The magnitude of difference can be 2 to 3 magnitudes.
$\hspace{5em}$ ![[fig-4-17_VSCMG.png|200]]


With this assumption that $J_s = I_{G_s} + I_{W_s} \approx I_{W_s}$ and we have the common equations of motion of a spacecraft equipped with one VSCMG as follows (replacing all $I_{W_s}$ with $J_s$ in Eq. (4.129)),
$$
\begin{aligned}
\bmt{I} \dot{\bmo} 
= - \bmo \times \bmt{I} \bmo &- \ght{s}\left[ J_s (\dot{\gamma} \omega_t + \dot{\Omega}) - (J_t-J_g)\omega_t \dot{\gamma} \right] \\
%
&- \ght{t} \left[ J_s(\omega_s+\Omega) \dot{\gamma} - (J_t+J_g) \omega_s \dot{\gamma} + J_s \Omega \omega_g \right] \\
%
&- \ght{g} \left[ J_g \ddot{\gamma} - J_s \Omega \omega_t \right] \\
%
&+ \bmL
\end{aligned}
\tag{4.131}
$$
>[!notice] 
>$\bmt{I}$ is a time-varying quantity in Eq. 4.131 because there is relative motion between the gimbal and RW in the spacecraft body frame $\calB$. \
>But $J_s, J_t, J_g$ are constants, because they are calculated in the gimble frame $\calG$.



**Reduce VSCMG to CMG only:**
If we set $\dot{\Omega}=0$, it means the RW spin speed is constant, thus<u> the equations of motion becomes those of a single-gimbal CMG (not varying-speed)</u>, which is
$$
\begin{aligned}
\bmt{I} \dot{\bmo} 
= - \bmo \times \bmt{I} \bmo &- \ght{s}\left[ J_s (\dot{\gamma} \omega_t + \ccancelto{0}{\dot{\Omega}}) - (J_t-J_g)\omega_t \dot{\gamma} \right] \\
%
&- \ght{t} \left[ J_s(\omega_s+\Omega) \dot{\gamma} - (J_t+J_g) \omega_s \dot{\gamma} + J_s \Omega \omega_g \right] \\
%
&- \ght{g} \left[ J_g \ddot{\gamma} - J_s \Omega \omega_t \right] \\
%
&+ \bmL
\end{aligned}
\tag{Example 4.8}
$$

**Reduce VSCMG to RW only:**
If we set the gimbal to be fixed, thus $\dot{\gamma}=\ddot{\gamma}=0$, we get <u>the equations of motion for RW</u> as
$$
\begin{aligned}
\bmt{I} \dot{\bmo} 
= - \bmo \times \bmt{I} \bmo &- \ght{s}\left[ J_s (\ccancelto{0}{\dot{\gamma}} \omega_t + \dot{\Omega}) - (J_t-J_g)\omega_t \ccancelto{0}{\dot{\gamma}} \right] \\
%
&- \ght{t} \left[ J_s(\omega_s+\Omega) \ccancelto{0}{\dot{\gamma}} - (J_t+J_g) \omega_s \ccancelto{0}{\dot{\gamma}} + J_s \Omega \omega_g \right] \\
%
&- \ght{g} \left[ J_g \ccancelto[magenta]{0}{\ddot{\gamma}} - J_s \Omega \omega_t \right] \\
%
&+ \bmL \\
&\hspace{-5em} = - \bmo \times \bmt{I} \bmo - \ght{s} J_s \dot{\Omega} \textcolor{blue}{ - \ght{t} J_s \Omega \omega_g + \ght{g} J_s \Omega \omega_t } + \bmL \\
&\hspace{-5em} = - \bmo \times \bmt{I} \bmo - \ght{s} J_s \dot{\Omega} \textcolor{blue}{ - \bmo \times J_s\Omega \ght{s} } + \bmL
\end{aligned}
\tag{Example 4.8}
$$

After-class practice: Verify this RW only equations of motion with that of the dual-spin S/C, in Eq. (4.83), where the gimble frame spin axis $\ght{s}$ will be assumed to align the body frame axis $\bht{1}$.

### Part-6, include multiple VSCMGs
>[!tip] (Part-6) Now, extend to multiple VSCMGs.

The essential is to notice that all the above derivations are the same and will be repeated for each VSCMG introduced to the spacecraft, but the only difference is how the DCM $\dcm{BG}_i$ is defined for the $i$-th VSCMG.

![[#^VSCMG-I-body-frame]]

Refer to Sec. 4.5.2 for detailed derivations for multiple VSCMGs.


---
<center>(End of LecNote04)</center>


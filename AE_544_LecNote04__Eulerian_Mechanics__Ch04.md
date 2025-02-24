---
date created: 2025-01-26T13:42:36-05:00
date modified: 2025-02-24T12:34:27-05:00
---
# AE_544_LecNote04\__Eulerian_Mechanics__Ch04

![[README#Disclaimers]]

The rotational dynamics of a rigid body are often referred to as Eulerian mechanics, because
Euler’s equation $\dot{\bmH} = \bmL$ and Euler’s rotational equation of motion generally govern this field.

But it is actually just Newtonian Mechanics being specialized for the case of rigid body dynamics.

> [!info] Review
> Newton's second law:
> $$
> \bmF = m \bm{a}
> $$
> 
> Euler's rotational equation of motion
> $$
> \bmL = \dot{\bmH} = \ddt {\large(} \bmt{I} \bmo {\large)} = \bmt{I} ~ \dot{\bmo} + \bmo\times(\bmt{I}~\bmo)
> $$

## Rigid Body Dynamics

Let the moment be taken either about the center of mass or the inertial coordinate frame origin, see [[AE_544_LecNote02__Newtonian_Mechanics__Ch02#Angular Momentum|Angular Momentum in lecture note 02]]. 
In either case Euler’s equation reduces to
$$
\dot{\bmH} = \bmL
\tag{4.1}
$$


![[fig-4-1_rigid_body_angular_momentum.png|300]]

In the inertial frame $\calN$, \
vector $\bmR$ is the inertial position vector of an infinitesimal mass element $\dm$; \
$\bmR_c$ is the center of mass; \
$\bmr=\bmR-\bmR_c$ is the relative position vector.

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

We define the angular momentum vector $\bmH_c$ of the rigid body $\calB$ about its mass center $\bmR_c$  
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
\bm{H}_c = \int_B \bm{r} \times (\bm{\omega} \times \bm{r}) \, \dm 
= \int_B - \bmt{\bm{\tilde{r}}} \bmt{\bm{\tilde{r}}} ~ \bm{\omega} \, \dm 
= \left( \int_B - \bmt{\bm{\tilde{r}}} \bmt{\bm{\tilde{r}}} \, \dm  \right)~ \bm{\omega} 
$$
Express all the coordinates in the body frame $\calB$, 
$$
\begin{aligned}
\bmr &= r_1 \bht1 + r_2 \bht2 + r_3 \bht3 \\
\bmo &= \omega_1\bht1 + \omega_2\bht2 + \omega_3\bht3 \\
\bmH_c &= H_{c_1}\bht1 + H_{c_2}\bht2 + H_{c_3}\bht3
\end{aligned}
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
Define the <u>inertia matrix at the center of mass</u> $\cdB{\bmt{I_c}}$ as
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
\bmt{I_O} = \bmt{I_c} + M \bmt{\tilde{\bmR}_c} \bmt{\tilde{\bmR}_c}\trans
\tag{4.19}
$$
All the components must be expressed in the same coordinate system/frame.

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


## Euler's Rotational Equations of Motion

Using transport theorem
$$
\begin{align}
\bmL_c &= \dot{\bmH}_c = \ddtB \bmH_c + \textcolor{red}{ \bmo_{\calB/\calN} \times \bmH_c } \\
&= \cancelto{\bm{0}}{\left(\ddtB \bmt{I}\right) \bmo} + \bmt{I} \ddtB \bmo + \textcolor{red}{ \bmo_{\calB/\calN} \times(\bmt{I}\bmo) }     \tag{used $\bmH_c=\bmt{I}\bmo$ in body frame} \\
&= \bmt{I} \ddtB \bmo + \textcolor{red}{ \bmo\times (\bmt{I}~\bmo) }      \tag{$\cdB{\bmt{I}}$ is constant} \\
&= \bmt{I} \ddtB \bmo \textcolor{red}{ + \bmt{\tilde{\bmo}}\bmt{I}~\bmo }      \tag{$\cdB{\bmt{I}}$ is constant} \\
&= \bmt{I} \left( \ddtN\bmo + \bmo_{\calN/\calB} \times \bmo \right) + \bmt{\tilde{\bmo}}\bmt{I}~\bmo \\
&= \bmt{I} ~ \dot{\bmo} + \bmt{\tilde{\bmo}}\bmt{I}~\bmo    \tag{4.32} \\
&= \bmt{I} ~ \dot{\bmo} + \bmo\times(\bmt{I}~\bmo)  \tag{4.32 alternative}
\end{align}
$$
where we have used the fact that $\bmo = \bmo_{\calB/\calN} = - \bmo_{\calN/\calB}$


In the principal body frame, the Euler's equation reduces to
$$
\begin{aligned}
I_{11} \dot{\omega}_1 &= -(I_{33} - I_{22}) \omega_2 \omega_3 + L_1 \\
I_{22} \dot{\omega}_2 &= -(I_{11} - I_{33}) \omega_3 \omega_1 + L_2 \\
I_{33} \dot{\omega}_3 &= -(I_{22} - I_{11}) \omega_1 \omega_2 + L_3 
\end{aligned}
\tag{4.33}
$$

For an axially symmetric body with transverse inertia $I_T = I_{11} = I_{22}$, this can be further simplified to
$$
\begin{aligned}
I_T \dot{\omega}_1 &= - (I_{33}-I_T)\omega_2 \omega_3 \\
I_T \dot{\omega}_2 &= (I_{33}-I_T)\omega_3 \omega_1 \\
I_{33} \dot{\omega}_3 &= 0
\end{aligned}
\tag{4.34}
$$
which can be solved analytically. Then we can analyze the different procession behaviors of prolate and oblate bodies. (Refer to textbook Sec. 4.2.3)

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
&- I_1\omega_p\omega_n \sin\theta\ght3 + I_3\omega_p(\omega_s+\omega_p\cos\theta) \sin\theta\ght1\\
&+ I_1\omega_p\omega_n\cos\theta\ght2 - I_2\omega_p^2\cos\theta \sin\theta\ght1

\end{aligned}
$$

The torque acting on the rotor is
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

Next, solve first-order ODEs numerically.

## Rotational Kinetic Energy

The rigid body rotational kinetic energy expression as
$$
T_\text{rot} = \frac{1}{2} \bmo \cdot \bmH_c = \frac{1}{2} \bmo\trans \bmt{I}~\bmo
\tag{4.52}
$$

%% The total kinetic energy of a rigid body B is the sum of translational and rotational energy
$$
T = \frac{1}{2}M \dot{\bmR}_c \cdot \dot{\bmR}_c + \frac{1}{2} \bmo \cdot \bmH_c = \frac{1}{2} \bmo\trans \bmt{I}~\bmo
\tag{4.53}
$$ %%

The work done by the torque $\bmL_c$ onto a rigid body $\calB$
%% $$
\dot{T}_\text{rot} = \frac{1}{2} \dot{\bmo} \cdot \bmH_c + \frac{1}{2} \bmo \cdot \dot{\bmH}_c
= \frac{1}{2} \dot{\bmo} \cdot \bmH_c + \frac{1}{2} \bmo \cdot \bmL_c
\tag{4.54 and 4.55}
$$ %%
$$
\dot{T}_\text{rot} = \dot{\bmo}\trans[I]\bmo = \bmo \cdot \bmL_c
$$
where $\bmL_c = \bmt{I} ~ \dot{\bmo} + \bmo\times(\bmt{I}~\bmo)$, as given in Eq. (4.32 alternative).



## Torque-Free Rigid Body Rotation (a geometric approach)

If no external torques are acting on a system,  the total angular momentum vector $\bmH$ is constant in the inertial frame, and the total rotational kinetic energy is also a constant.

When expressed in body frame $\calB$, the angular momentum vector $\bmH$ will generally not appear to be constant but rotating. However, the angular momentum magnitude $H$ is still a constant.

**Principal axes assumption**: We always assume that the body-fixed coordinate axes are all aligned with principal inertia axes.

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
The energy is not conserved in reality, so the motion will wobble along $\bht3$ when the energy is higher than that on the separatrix, then wobble along $\bht2$ after crossing the separatrix, and eventually stabilized and slows down along $\bht1$.


## Special Discussions on Axisymmetric Rigid Body

Without loss of generality, assume that $I_2 = I_3$. Then the yaw, pitch, and roll angle rates are given as
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

Details omitted, please refer to the textbook section 4.3.3.


## Dynamics of Dual-Spin Spacecraft (or Reaction Wheels)

The dual-spin spacecraft is a simple system where passive attitude stability is achieved by adding a single fly-wheel to the rigid spacecraft.

![[fig-4-15_dual_spin_sc.png|400]]
To develop the dual-spin system equations of motion, assume that the rotating fly-wheel is aligned with the first principal axis $\bht1$ of the main spacecraft component as illustrated in Fig. 4.15. 

Let $\bmo = \bmo_{\calB/\calN}$ be the body angular velocity of the main craft, while $\bmo_{\calW/\calB}= \Omega \bht1$ is the angular velocity of the fly-wheel relative to the spacecraft. 

The total angular momentum is then given by
$$
\bmH = \bmt{I_s} \bmo + \bmt{I_W} (\Omega \bht1 + \bmo)
\tag{4.82}
$$
where $\bmt{I_s}$ is <u>the inertia matrix of the main spacecraft system</u>, while $\bmt{I_W}$ is the inertia of the fly-wheel component.

>[!warning] $\bmt{I_s}$ doesn't include $\bmt{I_W}$ in Eq. (4.82).

Using Euler's equation $\dot{\bmH} = \bmL$, we have
$$
\dot{\bm{H}} = \bm{L} = (\bmt{I_s} + \bmt{I_W})\dot{\bm{\omega}} + [\bm{\tilde{\omega}}](\bmt{I_s} + \bmt{I_W})\bm{\omega} + \bmt{I_W}(\dot{{\Omega}}\bm{\hat{b}}_1) + [\bm{\tilde{\omega}}]\bmt{I_W}({\Omega}\bm{\hat{b}}_1)
\tag{4.83}
$$

> Skew-symmetric tilde operator:
> $$
> \bmt{\tilde{\bmx}} = \skewmt{x}
> $$

Assuming no external torque is present, and the body frame is principal,
$$
\newcommand{\colo}{\bmt{\omega_1\\ \omega_2\\ \omega_3}}
\newcommand{\Ithree}{\bmt{I_1 & 0 & 0 \\ 0 & I_2 & 0 \\ 0 & 0 & I_3}}
\bm{0} = \Ithree \bmt{\dot{\omega}_1\\ \dot{\omega}_2\\ \dot{\omega}_3} + \skewmt{\omega} \Ithree \colo + \diagmt{I_{W_s}}{I_{W_t}}{I_{W_t}} \dot{\Omega} \bmt{1\\0\\0} + \skewmt{\omega} \diagmt{I_{W_s}}{I_{W_t}}{I_{W_t}} \Omega \bmt{1\\0\\0}
$$
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

It is apparent that the only equilibrium spin configuration (meaning $\bmo$ is time-invariant) is when both $\omega_2$ and $\omega_3$ are zero
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
\dot{\delta \omega}_1 &= 0   \tag{4.89a} \\
\dot{\delta \omega}_2 &= \left( \frac{I_3-I_1}{I_2} \omega_{e_1} - \frac{I_{W_s}}{I_2} \Omega \right) \delta\omega_3  \tag{4.89b} \\
\dot{\delta \omega}_3 &= \left( \frac{I_1-I_2}{I_3} \omega_{e_1} + \frac{I_{W_s}}{I_3} \Omega \right) \delta\omega_2 \\
\end{align}
$$

Eq. (4.89a) tells $\delta\omega_1$ is constant, and thus $\omega_{e_1} + \delta\omega_1$ along $\bht1$ is also constant.

Rewrite the two coupled first-order differential equations into two uncoupled second-order differential equations, by taking derivative of Eq. (4.89b):
$$
\begin{aligned}
\delta \ddot{\omega}_2 &= \left( \frac{\textcolor{red}{ I_3-I_1 }}{I_2}R \omega_{e_1} - \frac{I_{W_s}}{I_2} \Omega \right) \textcolor{blue}{ \delta\dot{\omega}_3 }  \\
&= \textcolor{red}{ - } \left( \frac{\textcolor{red}{ I_1 - I_3 }}R{I_2} \omega_{e_1} \textcolor{red}{ + } \frac{I_{W_s}}{I_2} \Omega \right) \textcolor{blue}{ \left( \frac{I_1 - I_2}{I_3} \omega_{e_1} + \frac{I_{W_s}}{I_3} \Omega \right) \delta \omega_2 } \\
&= - \frac{\omega_{e_1}^2}{I_2 I_3}   \left( I_1 - I_3 + I_{W_s} \frac{\Omega}{\omega_{e_1}} \right)   \left( I_1 - I_2 + I_{W_s} \frac{\Omega}{\omega_{e_1}} \right)    \delta\omega_2 \\
&= - \frac{\omega_{e_1}^2}{I_2 I_3}   \left( I_1 - I_3 + I_{W_s} \hat{\Omega} \right)   \left( I_1 - I_2 + I_{W_s} \hat{\Omega} \right)    \delta\omega_2 \\
\end{aligned}
\tag{4.92--95 combined}
$$
If and only if the factor is negative, the system is linearly stable (when the solution is trigonometric function, otherwise it's exponential function).
Two critical wheel speeds are:
$$
\begin{align}
\hat{\Omega}_1 = \frac{I_3 - I_1}{I_{W_s}}  \tag{leads 1st term to 0}  \\
\hat{\Omega}_2 = \frac{I_2 - I_1}{I_{W_s}}  \tag{leads 2nd term to 0}  \\ 
\end{align}
$$

![[fig-4-16_stability_ranges_in_shades.png|400]]
A lot of interesting discussions can be conducted about this results. 
Basically, when the wheel is spinning fast enough and governs the ratio of $H_1, H_2, H_3$, it can change the intersection curve of the energy ellipsoid and momentum sphere. 
(Omitted here and refer to the textbook)

>[!info]- Revisit Fig. 4.9 
> 
> ![[fig-4-9_intersection_of_ellipsoids.png|400]]
> For a rigid body, its distribution of $\bmH$ along three principal axes is determined by the inertia $I_1, I_2, I_3$.
> But for a dual-spin S/C, it can increase a particular $H_i$ without affecting the other two components much. 
> Therefore, even for the intermediate energy case in (b), the wheel can spin up fast enough to blow up the ellipsoid along $\bht2$ or $H_2$ direction until it becomes the minimum energy case in (a). 
> Note that when the ellipsoid is being blown up, the energy sphere is also increasing.


















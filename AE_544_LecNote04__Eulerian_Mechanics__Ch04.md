---
date created: 2025-01-26T13:42:36-05:00
date modified: 2025-02-21T02:38:08-05:00
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


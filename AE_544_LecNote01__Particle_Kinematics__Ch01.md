---
date created: 2025-01-12T15:56:32-05:00
date modified: 2025-02-06T22:17:43-05:00
---

# AE_544_LecNote01\__Particle_Kinematics__Ch01

![[README#Disclaimers]]

**Kinematics** is to use vectors and matrices to describe positions, velocities, and accelerations of particles and rigid bodies, as viewed from various reference frames.
The key points here are:
- Vector
- Frame
- Coordinate system

>[!question]- Reference frame vs. coordinate system?
> *Coordinate system*: A mathematical construct/concept. The direction matters more than the origin. Example: velocity vector $\bm{v}$ and acceleration vector $\bm{a}$.
> 
> The transformation from one coordinate system to another is kind of "static", where no physics are involved.
>  
> *Frame, or reference frame*: A physics-involved concept. The origin matters more than the direction. Example: position vector $\bm{r}$.
> 
> The transformation from one frame to another is kind of "dynamic", which usually involves the transport theorem.

*<u>Particle</u> Kinematics* means the physical dimensions and properties are not concerned.

## Particle Position Description

In any give frame, two things are important: magnitude (quantity) and unit.

A coordinate system is defined by two items. 
First, a coordinate *system origin* $O$ must be established to specify its position in space. 
Second, the *orientation* of the coordinate system must be chosen.

Three perpendicular (or orthogonal) right-hand unit vectors are traditionally used to denote unit displacement directions along the orthogonal axes.
The basis triad is $\left\{ \eht{1}, \eht{2}, \eht{3} \right\}$.

![[fig-1-1__Cartesian_frame.png|300]]

More generally, think of a reference frame as a rigid body. For example, although the Earth is a rigid body, there is an infinite set of coordinate systems that could be embedded in the Earth-fixed reference frame. For the present, we will usually associate only one coordinate system with a reference frame (rigid body).

$$
\bm{r} = x \eht{1} + y \eht{2} + z \eht{3}
\tag{1.1}
$$

$$
^\mathcal{E} \bm{r} = \prescript{\mathcal{E}}{}{\pmatrix{x \\ y \\ z}}
\tag{1.2}
$$

The vector notation is abstract, which doesn't depend on any coordinate system. For vectors $\bm{r}$ and $\bm{p}$ given in the same frame, vector operations can be performed, such as 
$$
\bm{q} = \bm{r} + \bm{p}
$$
which is more useful for theoretical or analytical derivations.

When resolving them to coordinates for numerical calculations, a coordinate system (let's say $\mathcal{E}$) must be specified first, then we have
$$
\prescript{\color{blue}\mathcal{E}}{}{\pmatrix{q_{1} \\ q_{2} \\ q_{3}}}
= 
\prescript{\color{blue}\mathcal{E}}{}{\pmatrix{r_{1} \\ r_{2} \\ r_{3}}}
+ 
\prescript{\color{blue}\mathcal{E}}{}{\pmatrix{p_{1} \\ p_{2} \\ p_{3}}}
\tag{correct}
$$


> [!error] 
> Operating coordinates in different coordinate systems is a common mistake in calculation and coding.
> $$
> \prescript{\color{blue}\mathcal{E}}{}{\pmatrix{q_{1} \\ q_{2} \\ q_{3}}}
> = 
> \prescript{\color{blue}\mathcal{E}}{}{\pmatrix{r_{1} \\ r_{2} \\ r_{3}}}
> + 
> \prescript{\color{pink}\mathcal{B}}{}{\pmatrix{p_{1} \\ p_{2} \\ p_{3}}}
> \tag{{\color{red}WRONG!}}
> $$

Coordinate transformation and matrix operation are naturally induced to solve the above problem, to unify all the vectors in the same coordinate system.



For many situations the Cartesian coordinate system is the most intuitive and straightforward one. 
But for many other times, using different coordinate systems can make the problem easy. 

>[!hint] 
>This is also one motivation that Lagrange mechanics introduces *generalized coordinates* and accommodate constraints. We will discuss this later.



---


A cylindrical coordinate system $\mathcal{C}$ is shown below:

![[fig-1-2__cylindrical_frame.png|300]]

The basis triad of $\mathcal{C}$ is $\left\{ \cht{d}, \cht{\theta}, \cht{3} \right\}$:
- $\cht{d}$: tracks the heading of the projection of the $\bm{r}$ vector in the plane
- $\cht{\theta}$: always normal to $\cht{d}$
- $\cht{3}$: normal to the plane of $\cht{d}$ and $\cht{\theta}$.

Two unit orientation vectors of the cylindrical coordinate system are varying as seen from $\mathcal{N}$.

The position vector and coordinates in $\mathcal{C}$ are
$$
\begin{aligned}
\bm{r} &= d \cht{d} + z \cht{3} \\
^{\mathcal{C}}\bm{r} &= \prescript{\mathcal{C}}{}{\pmatrix{d \\ 0 \\ z}}
\end{aligned}
\tag{1.3}
$$

For a large number of problems having rotational symmetry of force fields or constraint surfaces, cylindrical coordinates would be an attractive choice.
The second entry of the cylindrical coordinate system column vector in Eq. (1.3) will always be zero. <u>Any particle position vector expressed in a cylindrical coordinate system</u>[^why-zero-2nd-entry] will never have a component along the $\cht{\theta}$ direction. 

[^why-zero-2nd-entry]: It is tricky here because only when a vector $\bm{r}$ is expressed in a $\mathcal{C}$ defined by itself, then it has no second entry. If $\mathcal{C}$ is used to describe another vector $\bm{a}$, $^{\mathcal{C}}\bm{a}$ will have a nonzero second entry in general case.

$$
\begin{alignat}{3}
\cht{d} &= & \cos\theta \, \eht{1} &+ \sin\theta \, \eht{2} \\
\cht{\theta} &= & -\sin\theta \, \eht{1} &+ \cos\theta \, \eht{2}
\end{alignat}
\tag{1.4}
$$

>[!question]- Do we must define a Cartesian coordinate system first before a Cylindrical Coordinate system?
> Both yes and no.
> ![[fig-1-2__cylindrical_frame.png|300]]
> 
> For no: Seemingly in Fig. 1.2 that we need $\{ \eht{1}, \eht{2}, \eht{3} \}$ to define $\left\{ \cht{d}, \cht{\theta}, \cht{3} \right\}$.
> But in fact, we can directly define $\mathcal{C}$ using $\bm{r}$ by picking an arbitrary $\cht{d}$-$\cht{\theta}$ plane. Then, this $\mathcal{C}$ can be used to describe other vectors.
> 
> For yes: Without a Cartesian system, we cannot specify the $\theta$ angle. 
> Even in the above rationale, a Cartesian system is implied when using $\mathcal{C}$ to describe other vectors.



---

A spherical coordinate system $\mathcal{S}$ is illustrated in Fig. 1.3 with its orientation defined through the basis triad $\{ \sht{r}, \sht{\theta}, \sht{\phi} \}$.

![[fig-1-3__spherical_frame.png|300]]

The position vector and coordinates in $\mathcal{S}$ are
$$
\begin{aligned}
\bm{r} &= r \sht{r} \\
^{\mathcal{S}}\bm{r} &= \prescript{\mathcal{S}}{}{\pmatrix{r \\ 0 \\ 0}}
\end{aligned}
\tag{1.3}
$$


All three unit orientation vectors are time varying for the spherical coordinate system as seen from $\mathcal{N}$:
$$
\begin{alignat*}{5}
\sht{r} &= &  \cos\phi \cos\theta \, &\eht{1} &+  \cos\phi \sin\theta \, &\eht{2} + \sin\phi \, \eht{3} \\ 
\sht{\theta} &= & -\sin\theta \, &\eht{1} &+  \cos\theta \, &\eht{2} \\ 
\sht{\phi} &= & -\sin\phi \cos\theta \, &\eht{1} &-  \sin\phi \sin\theta \, &\eht{2} + \cos\phi \, \eht{3} 
\end{alignat*}
$$

>[!question] Similarly, do we must define a Cartesian coordinate system first before a Spherical Coordinate system?
>No answer is provided.


---


## Angular Velocity Vector

The angular velocity vector $\bm{\omega}$ of a rigid body or coordinate system $\mathcal{B}$ relative to another coordinate system $\mathcal{N}$ is typically expressed in $\mathcal{B}$ frame components:
$$
\bm{\omega} = \omega_{1} \bht{1} + \omega_{2} \bht{2} + \omega_{3} \bht{3}
\tag{1.11}
$$

>[!hint] 
>Especially when dealing with attitude dynamics, or rigid body rotation, it is convenient to express $\bm{\omega}$ in the body frame. We will see this in later discussions.

>[!warning] 
>*Textbook convention*: Always use rad/s for angular velocity. Note that any time numerical values of $\bm{\omega}$ are used that units of <u>radians per second</u> must be used. Otherwise any formulas that use x will not yield correct results.


## Rotation About a Fixed Axis

Assumed a fixed rotational axis:
![[fig-1-6__rigid_body_rotation_fixed_axis.png|300]]

The speed of $P$, which is also the magnitude, is given by
$$
|\dot{\bm{r}}| = (r\, \sin\theta) \, \omega
\tag{1.12}
$$

The direction of $\dot{\bm{r}}$, due to the assumption of rigidness, is given by
$$
\hat{\dot{\bm{r}}} = \frac{\bm{\omega} \times \bm{r}} {|\bm{\omega} \times \bm{r}|}
$$

So the transport velocity of a point $P$ in/on a rigid body is
$$
\dot{\bm{r}} = (r \sin\theta) \cdot \omega \cdot \frac{\bm{\omega} \times \bm{r}} {|\bm{\omega} \times \bm{r}|} = \bm{\omega} \times \bm{r}
\tag{1.13 and 1.14}
$$

>[!question]- Are $\textcolor{red}{ \hat{\dot{\bm{r}}} }$ and $\textcolor{blue}{ \dot{\hat{\bm{r}}} }$ the same (the order of uniformization and derivative is flipped)?
> **No.** An obvious reason is that, one of them is a unit vector with always a magnitude of 1, but the other is not guaranteed to have a magnitude of 1.
> For more in-depth details, as shown in the derivation of the two quantities:
> $$
> \begin{aligned}
> \bm{r} &= r \hat{\bm{r}} \\
> \dot{\bm{r}} &= \frac{d}{dt} (\bm{r}) = \frac{d}{dt} ( r \hat{\bm{r}} ) = \left(  \frac{d}{dt} r  \right) \hat{\bm{r}} +  r \left( \textcolor{blue}{ \frac{d}{dt} \hat{\bm{r}} } \right) = \dot{r}\hat{\bm{r}} + r \textcolor{blue}{ \dot{\hat{\bm{r}}} } \\
> \textcolor{red}{ \hat{\dot{\bm{r}}} } &= \frac{\dot{\bm{r}}}{|\dot{\bm{r}}|} = \frac{\dot{r}\hat{\bm{r}} + r \textcolor{blue}{ \dot{\hat{\bm{r}}} }}{|\dot{r}\hat{\bm{r}} + r \textcolor{blue}{ \dot{\hat{\bm{r}}} }|} \\
> \end{aligned}
> $$
> Up to here, it's already clear that they are related to each other but different. 
> Even under the assumption of rigid body, which implies $\dot{r} = 0$, they are still different, as shown below:
> $$
> \textcolor{red}{ \hat{\dot{\bm{r}}} } = \frac{\dot{r}\hat{\bm{r}} + r \textcolor{blue}{ \dot{\hat{\bm{r}}} }}{|\dot{r}\hat{\bm{r}} + r \textcolor{blue}{ \dot{\hat{\bm{r}}} }|} = \frac{ \textcolor{blue}{ \dot{\hat{\bm{r}}} }}{| \textcolor{blue}{ \dot{\hat{\bm{r}}} }|}
> $$
> They are along the same direction, but the magnitude is different in general case.
> 
> After all, it's all about *rigorous definitions and calculations using a consistent symbolic system*.

> The above result would also hold if we are finding the velocity vector fixed to any reference frame that is rotating relative to another; as is evident in the following section, this easily generalizes for three-dimensional motion.


## Transport Theorem (*Proof required*)

Let $\mathcal{N}$ be an inertially fixed reference frame with a corresponding triad of $\mathcal{N}$-fixed orthogonal base vectors $\{ \nht{1}, \nht{2}, \nht{3} \}$. 
Let $\mathcal{B}$ be another reference frame with the B-fixed base vectors $\{ \bht{1}, \bht{2}, \bht{3} \}$.
For simplicity, let the origins of the two frames be coincident.

Given the position vector and angular velocity vector as following:
$$
\bm{r} = r_1 \bht{1} + r_2 \bht{2} + r_3 \bht{3}
\tag{1.15}
$$

$$
\bm{\omega}_{\Bcal/\Ncal} = \omega_1 \bht{1} + \omega_2 \bht{2} + \omega_3 \bht{3}
\tag{1.16}
$$

By calculating the derivative of your position vector within $\Bcal$, you are determining how quickly this vector changes direction and/or magnitude as seen from the $\Bcal$ system. 
To indicate that a derivative is taken of a generic vector $\bm{x}$ as seen in the $\Bcal$ frame, we write
$$
\ddtB (\bm{x})
$$

Calculating the derivative of your position vector in the $\Ncal$ frame, you wish to know how fast this vector is changing with respect to the fixed coordinate system $\Ncal$.
Similarly, the derivative in $\Ncal$ frame is written as
$$
\ddtN (\bm{x})
$$

The derivative of the position vector $\bm{r}$ in the $\Bcal$ frame is given by
$$
\ddtB(\bm{r}) = \ddtB \left( r_1 \bht{1} + r_2 \bht{2} + r_3 \bht{3} \right)
= \dot{r}_1 \bht{1} + \dot{r}_2 \bht{2} + \dot{r}_3 \bht{3}
\tag{1.17}
$$
where $\dot{r}_i = \ddtB (r_i)$.

>[!note]
>This is also referred to as *relative velocity* sometimes in different books.

The derivative in the $\Ncal$ frame is given by
$$
\ddtN(\bm{r}) = \ddtN \left( r_1 \bht{1} + r_2 \bht{2} + r_3 \bht{3} \right)
= \dot{r}_1 \bht{1} + \dot{r}_2 \bht{2} + \dot{r}_3 \bht{3} 
+ r_1 \ddtN (\bht{1}) + r_2 \ddtN (\bht{2}) + r_3 \ddtN (\bht{3}) 
\tag{1.18}
$$
where $\dot{r}_i$ is defined as previous.
Using Eq. (1.14) (copied here), the derivatives of the basis vectors can be found as
$$
\dot{\bm{r}} = \bm{\omega} \times \bm{r}
\tag{1.14}
$$
$$
\ddtN(\bht{i}) = \bm{\omega}_{\Bcal/\Ncal} \times \bht{i}
\tag{1.19}
$$

Finally, we have the transport theorem:
>[!theorem 1.1]
>(Transport Theorem): (... omitted details of symbols and assumptions ...)
> $$
> \ddtN(\bm{r}) = \ddtB(\bm{r}) + \bm{\omega}_{\Bcal/\Ncal} \times \bm{r}
> \tag{1.21}
> $$

> Notice that $\Bcal$ and $\Ncal$ are arbitrarily moving reference frames. This permits one to relate the derivative of $\bm{r}$ as it would be seen from the $\Ncal$ frame to the analogous rate of change of $\bm{r}$ as seen in the $\Bcal$ frame.

> It is a very fundamental and important result that is used almost every time kinematic equations are derived.

Simplify the notation using the following shorthand notation:
$$
\ddtN(\bm{x}) \equiv \dot{\bm{x}}
\tag{1.22}
$$

>[!hint] 
>It can be confusing by not specifying the underlying frame or coordinate system used to express vectors. 




## Example 1.3 Satellite relative motion

![[fig-1-8_example-1-3_satellite_relative_motion.png|300]]

Satellites A and B are in the same orbit plane. So, the relative motion is planar.
 
Cylindrical frames are used here: 

- Common inertial frame: $\mathcal{N}: \{ \nht{1}, \nht{2}, \nht{3} \}$
- Satellite A associated body frame: $\mathcal{A}: \{ \iht{r_A}, \iht{\theta_A}, \iht{h} \}$
- Satellite B associated body frame: $\mathcal{B}: \{ \iht{r_B}, \iht{\theta_B}, \iht{h} \}$

Position vectors expressed in each frame are 
$$
\bm{r}_A = r_A \, \iht{r_A} \qquad \text{and} \qquad \bm{r}_B = r_B \, \iht{r_B}
$$

Relative angular velocity 
$$
\bm{\omega}_{\Bcal/\Acal} 
= \bm{\omega}_{\Bcal/\Ncal} + \bm{\omega}_{\Ncal/\Acal} 
= \bm{\omega}_{\Bcal/\Ncal} - \bm{\omega}_{\Acal/\Ncal} = (\dot{\theta}_B - \dot{\theta}_A) \, \iht{h}
$$

The relative position vector is given by $\bm{\rho} = \bm{r}_B - \bm{r}_A$. Now we can calculate the relative velocity of B relative to A, as seen in the $\Acal$ frame:
$$
\ddtA (\bm{\rho}) = \ddtA (\bm{r}_B) - \ddtA (\bm{r}_A)
\tag{Distributive rule.}
$$


*Calculate second term:*
$$
\ddtA (\bm{r}_A) = \dot{r}_A \iht{r_A} + r_A \ddtA \left( \iht{r_A} \right) = \dot{r}_A \iht{r_A}
\tag{Body frame $\Acal$}
$$

*Calculate first term:*
$$
\begin{align}
\ddtA (\bm{r}_B)
&= \ddtB (\bm{r}_B)\textcolor{red}{  + \bm{\omega}_{\Bcal/\Acal} \times \bm{r}_B } \tag{Transport theorem} \\
&= \textcolor{red}{ \dot{r}_B \iht{r_B} } + (\dot{\theta}_B - \dot{\theta}_A) \, \iht{h} \times (r_B\,\iht{r_B}) \\
&= \dot{r}_B \iht{r_B} + (\dot{\theta}_B - \dot{\theta}_A) r_B \, \iht{h} \times \iht{r_B} \\
&= \dot{r}_B \iht{r_B} + (\dot{\theta}_B - \dot{\theta}_A) r_B \, \iht{\theta_B}
\end{align}
$$
> [!info]- Another way to verify the above derivation, by switching the order of expanding $\bmr_B$ and applying the transport theorem.
> Derivation:
> $$
> \begin{aligned}
> \ddtA (\bm{r}_B) 
> &= \ddtA (r_B \iht{r_B}) = \ddtA (r_B) \iht{r_B} + r_B \ddtA (\iht{r_B}) \\
> &= \ddtA (r_B) \iht{r_B} + r_B \bm{\omega}_{\Bcal/\Acal} \times \iht{r_B} \\
> &= \textcolor{blue}{ \ddtA (r_B) \iht{r_B} } + \bm{\omega}_{\Bcal/\Acal} \times \bm{r}_B \\
> &= \textcolor{red}{ \dot{r}_B \iht{r_B} + \bm{\omega}_{\Bcal/\Acal} \times \bm{r}_B }
> \end{aligned}
> $$
> A critical step here is how to resolve the blue term, $\textcolor{black}{ \ddtA (r_B) }$ to $\textcolor{black}{ \dot{r}_B}$. 
> For a scalar, $r_B$ here, which is the distance between $B$ and the Earth center, the derivative is always the same whichever frame the derivative is taken in. This is because, the scalar $r_B$ is not dependent on the choice of frame. As an opposite instance, the vector $\bmr_B$ is dependent on the frame, so $\ddtA \bmr_B$ and $\ddtB \bmr_B$ are obviously different. 
> 
> >[!done] The following definition was used to justify this during the class
> >$$
> >\ddt(*) = \lim_{ t_2 \to t_1 } \frac{*(t_2) - *(t_1)}{t_2 - t_1}
> >$$
> >Then I tried to show the difference that when $*$ is a scalar and when $*$ is a vector, the increments are different.

*Finally*, substitute the two parts back into the original relative velocity, we have
$$
\begin{aligned}
\ddtA (\bm{\rho}) 
&= \ddtA (\bm{r}_B) - \ddtA (\bm{r}_A) \\
&= \dot{r}_B \iht{r_B} + (\dot{\theta}_B - \dot{\theta}_A) r_B \, \iht{\theta_B} - \dot{r}_A \iht{r_A} \\
%\dot{r}_B \iht{r_B} + (\dot{\theta}_B - \dot{\theta}_B) r_B \, \iht{\theta_B} - \dot{r}_A \iht{r_A}
\end{aligned}
$$



>[!note] Body frames are defined without using an inertial frame.
> > Note that this relative velocity solution is computed using general vector expressions and without specifying how the A and B frame unit direction vectors are oriented relative to some inertial frame.
> 
> The orbit plane is chosen as a reference plan to define the two body frames. 

To obtain the relative acceleration as seen in the $\Acal$ frame, the preceding differentiation process is repeated to yield
$$
\dddttA (\bm{\rho}) = \ddtA \left[ \dot{r}_B \iht{r_B} + (\dot{\theta}_B - \dot{\theta}_A) r_B \, \iht{\theta_B} - \dot{r}_A \iht{r_A} \right]
$$

First term:
$$
\begin{aligned}
\ddtA \left[ \dot{r}_B \iht{r_B} \right] 
&= 
\ddtB \left[ \dot{r}_B \iht{r_B} \right] + \bm{\omega}_{\Bcal/\Acal} \times \left[ \dot{r}_B \iht{r_B} \right] \\
%
&= \ddot{r}_B \, \iht{r_B} + (\dot{\theta}_B - \dot{\theta}_A) \dot{r}_B \, \left[ \iht{h} \times \iht{r_B} \right] \\
&= \ddot{r}_B \, \iht{r_B} + (\dot{\theta}_B - \dot{\theta}_A) \dot{r}_B \, \iht{\theta_B} 
\end{aligned}
$$

Second term:
$$
\begin{aligned}
\ddtA \left[ (\dot{\theta}_B - \dot{\theta}_A) r_B \, \iht{\theta_B} \right] 
%
&= 
%
\ddtB \left[ (\dot{\theta}_B - \dot{\theta}_A) r_B \, \iht{\theta_B} \right] + \bm{\omega}_{\Bcal/\Acal} \times \left[ (\dot{\theta}_B - \dot{\theta}_A) r_B \, \iht{\theta_B} \right] \\
%
&= \ddtB \left[ (\dot{\theta}_B - \dot{\theta}_A) r_B \right] \, \iht{\theta_B} + \left[ (\dot{\theta}_B - \dot{\theta}_A) r_B \right] \ddtB (\iht{\theta_B}) + (\dot{\theta}_B - \dot{\theta}_A) \, \iht{h} \times \left[ (\dot{\theta}_B - \dot{\theta}_A) r_B \, \iht{\theta_B}\right] \\
%
&= \left[ (\ddot{\theta}_B - \ddot{\theta}_A) r_B + (\dot{\theta}_B - \dot{\theta}_A) \dot{r}_B \right] \, \iht{\theta_B} + \bm{0} + (\dot{\theta}_B - \dot{\theta}_A) (\dot{\theta}_B - \dot{\theta}_A) r_B \, \left[ \iht{h} \times \iht{\theta_B} \right] \\
%
&= \left[ (\ddot{\theta}_B - \ddot{\theta}_A) r_B + (\dot{\theta}_B - \dot{\theta}_A) \dot{r}_B \right] \, \iht{\theta_B} + \bm{0} + (\dot{\theta}_B - \dot{\theta}_A)^2 r_B \, \left[ - \iht{r_B} \right] \\
%
&= \left[ (\ddot{\theta}_B - \ddot{\theta}_A) r_B + (\dot{\theta}_B - \dot{\theta}_A) \dot{r}_B \right] \, \iht{\theta_B} - (\dot{\theta}_B - \dot{\theta}_A)^2 r_B \, \iht{r_B}
\end{aligned}
$$

Third Term:
$$
\ddtA \left[ - \dot{r}_A \iht{r_A} \right] = - \ddot{r}_A \iht{r_A} - \dot{r}_A \ddtA (\iht{r_A}) = - \ddot{r}_A \iht{r_A}
$$

Finally, we will have
$$
\dddttA (\bm{\rho}) = 
\ddot{r}_{B} \iht{r_B} 
- \ddot{r}_{A} \iht{r_A}
+ \left[ 2 \dot{r}_B (\dot{\theta}_B - \dot{\theta}_A) + r_B (\ddot{\theta}_B - \ddot{\theta}_A) \right] \, \iht{\theta_B} - r_B (\dot{\theta}_B - \dot{\theta}_A)^2 \, \iht{r_B}
\tag{From textbook}
$$

>[!hint] Both frame coordinate systems are involved in the final results.
> We've been used to express everything in one common frame, let's say an inertial frame $\Ncal$. 
> Here we see that without using any inertial frame, we can get an ODE of the relative dynamics.

> [!question] Open Question
> Up to this point, can you propagate this ODE to get the relative trajectory of the satellite B relative to A?


## Particle Kinematics with Moving Frames

$\mathcal{A}: \{ O, \aht{1}, \aht{2}, \aht{3} \}$

$\mathcal{B}: \{ O', \bht{1}, \bht{2}, \bht{3} \}$

![[fig-1-10_two_moving_frames.png|300]]

**New notation**: The velocity vector of the particle $P$ with the derivative taken relative to the $\Bcal$ frame:
$$
(v^P)_\Bcal \equiv \ddtB( \bm{\rho} )
\tag{1.26}
$$

The velocity vector of $P$ relative to the $\Acal$ frame is given as
$$
(v^P)_A \equiv \ddtA (\bm{r}) = \ddtA (\bm{R}+\bm{\rho}) = \ddtA (\bm{R}) + \ddtA (\bm{\rho})
\tag{1.27}
$$
$$
= \cood{\bm{v}^{O'}}{\Acal} + \ddtB (\bm{\rho}) + \bm{\omega}_{\Bcal/\Acal} \times \bm{\rho}
\tag{Transport theorem}
$$
$$
= \cood{\bm{v}^{O'}}{\Acal} + \cood{\bm{v}^P}{\Bcal} + \bm{\omega}_{\Bcal/\Acal} \times \bm{\rho}
\tag{1.29}
$$

Next, the acceleration $\cood{\bm{a}^P}{\Acal}$ of the particle $P$ in the $\Acal$ frame is given by
$$
\cood{\bm{a}^P}{\Acal} = \ddtA\left( \cood{\bm{v}^{O'}}{\Acal} + \cood{\bm{v}^P}{\Bcal} + \bm{\omega}_{\Bcal/\Acal} \times \bm{\rho} \right)
$$
$$
= \cood{\bm{a}^{O'}}{\Acal} + \cood{\bm{a}^P}{\Bcal} + \bm{\alpha}_{\Bcal/\Acal} \times \bm{\rho} + 2\bm{\omega}_{\Bcal/\Acal} \times \cood{v^P}{\Bcal} + \bm{\omega}_{\Bcal/\Acal} \times \left( \bm{\omega}_{\Bcal/\Acal} \times \bm{\rho} \right)
\tag{1.35}
$$
where $\bm{\alpha}_{\Bcal/\Acal} = \ddtA(\bm{\omega}_{\Bcal/\Acal})$ is the angular acceleration vector of the $\Bcal$ frame relative to the $\Acal$ frame.

- Coriolis acceleration: $2\bm{\omega}_{\Bcal/\Acal} \times \cood{v^P}{\Bcal}$
- Centrifugal acceleration: $\bm{\omega}_{\Bcal/\Acal} \times \left( \bm{\omega}_{\Bcal/\Acal} \times \bm{\rho} \right)$
- Euler acceleration: $\bm{\alpha}_{\Bcal/\Acal} \times \bm{\rho}$

>[!note]
> Note that Eq. (1.35) holds between any two reference frames. It is not necessary that $\Acal$ or $\Bcal$ be inertially fixed. 

> [!important] 
> The vector components used in the various terms on the right-hand side of Eq. (1.35) can be taken along any choice of unit vectors. It is important that we recognize the complete freedom we have to use any basis vectors we wish to express components of any vector in Eq. (1.35).

> [!info]- There is some ambiguity about `centrifugal/centripetal acceleration`, but no ambiguity about `centrifugal force`.
> >[!warning] Read with caution. My understanding could be wrong.
> 
> In the textbook we are using, particularly, under Eq. (1.36) on page 20, there are both mentioning of `centrifugal` and `centripical` (a typo for `centripetal`). In my opinion, it is indeed a confusing expression, and there is no easy correction to that.
> 
> Additionally, I find the usage of the terms `centrifugal acceleration` and `centripetal acceleration` is kind of inconsistent through different textbook and online resources. 
> 
> Alternatively, my suggestion is to try to discuss `centrifugal force` instead of `centrifugal acceleration`. 
> 
> Resort to these Wikipedia links for some good explanations of these fictitious forces, which are more or less consistent with each other:
> - https://en.wikipedia.org/wiki/Centrifugal_force?useskin=vector#Force
> - https://en.wikipedia.org/wiki/Fictitious_force?useskin=vector#General_derivation
> - https://en.wikipedia.org/wiki/Coriolis_force?useskin=vector#Formula
> 
> My conclusion is that language interpretation can be confusing with a specific background, but the mathematical derivation is straightforward and unambiguous.

## Example 1.5 Rolling disk inside a tube

What is the inertial acceleration $\ddot{\bm{r}}$ of point $P$ expressed in $\mathcal{E}$ frame components?\
![[fig-1-12_example-1-5_rolling_disk.png|300]]

Three frames are defined and involved: 
- $\mathcal{N}: \{ O, \nht{1}, \nht{2}, \nht{3} \}$, Cartesian
- $\mathcal{E}: \{ O, \eht{L}, \eht{\theta}, \eht{3} \}$, cylindrical
- $\mathcal{B}: \{ O', \bht{r}, \bht{\phi}, \bht{3} \}$, cylindrical

The logics are:
1. Find $\bm{\omega}_{\Bcal/\Ncal}$ and $\bm{\omega}_{\mathcal{E}/\Ncal}$.
2. Express $\bm{r}$ and $\bm{L}+\bm{\rho}$.
3. Using transport theorem repeatedly to find $\dot{\bm{r}}$ and then $\ddot{\bm{r}}$. During process, resolving $\bm{L}$ and $\bm{\rho}$ to coordinates to simplify the problem.
4. Change/unify coordinate system under the required $\mathcal{E}$ frame.

> [!info] 
> Through this example, it is expected to understand:
> > Although the result in Eq. (1.35) can be quite useful at times, when more than two frames are present, it is typically easier to derive the acceleration terms by differentiating the position vector twice, as in this example.

## Textbook problem 1.8 (Rotating disk on train)
![[fig-p1-8_rotating_disk_on_train.png|600]]

The rail is straight.

Inertial frame $\calN:\{\nht{}\}$ not shown in the figure, assume $v(t)$ is measured in this frame, doesn't really matter. 

Cartesian frame $\calD:\{\dht1,\dht2,\dht3\}$ centered at the disk

Polar frame $\calE: \{\eht{r},\eht{\theta},\dht3\}$ at the same center

Train is moving in a constant/fixed direction, which is $\dht1$ in the figure.

Disk's constant rotation vector is $\bmo = \omega_{\calE/\calD} \dht3$

Position vector is
$$
\bmr = r \eht{r}
$$

The vector measured in $\calE$ is
$$
\ddtD{\bmr} = r \ddtE\eht{r} = r \bmo\times\eht{r} = r\omega_{\calE/\calD}\dht3\times\eht{r} = r\omega\eht{\theta} = r\omega (-\sin\theta\dht1 + \cos\theta\dht2)
$$
The inertial velocity is then
$$
\dot{\bmr} = \ddtN \bmr = v(t)\dht{1} + \ddtD \bmr = v(t)\dht1 + r\omega (-\sin\theta\dht1 + \cos\theta\dht2)
$$
$$
= (v-r\omega\sin\theta)\dht1 + r\omega \cos\theta\dht2
$$

The inertial acceleration can be directly got as
$$
\begin{aligned}
\ddot{\bmr} &= \ddtN [(v-r\omega\sin\theta)\dht1 + r\omega \cos\theta\dht2] \\
&= (\dot{v}-r\omega\dot{\theta}\cos\theta)\dht1 - r\omega\dot{\theta}\sin\theta \dht2
\end{aligned}
$$


## Textbook problem 1.9 (Rotating disk on train variant)
![[fig-p1-8_rotating_disk_on_train.png|600]]
Repeat problem 1.8, but this time assume that the particle P is free to move radially on the disk. Again find the corresponding inertial velocity and acceleration.

Inertial frame $\calN:\{\nht{}\}$ not shown in the figure, assume $v(t)$ is measured in this frame.

Cartesian frame $\calD:\{\dht1,\dht2,\dht3\}$ centered at the disk

Polar frame $\calE: \{\eht{r},\eht{\theta},\dht3\}$ at the same center

Train is moving in a constant/fixed direction, which is $\dht1$ in the figure.

Disk's constant rotation vector is $\bmo = \omega_{\calE/\calD} \dht3$

Position vector is
$$
\bmr = r \eht{r}
$$

The vector measured in $\calE$ is
$$
\begin{aligned}
\ddtD{\bmr} &= \dot{r}\eht{r} + r \ddtE\eht{r} \\
&= \dot{r}\eht{r} + r \bmo\times\eht{r} = \dot{r}\eht{r} + r\omega_{\calE/\calD}\dht3\times\eht{r} \\
&= \dot{r}\eht{r} + r\omega\eht{\theta} \\
&= \dot{r}(\cos\theta\dht1 + \sin\theta\dht2) + r\omega (-\sin\theta\dht1 + \cos\theta\dht2)\\
&=  (\dot{r}\cos\theta - r\omega\sin\theta)\dht1 + (\dot{r}\sin\theta + r\omega\cos\theta)\dht2
\end{aligned}
$$
The inertial velocity is then
$$
\begin{aligned}
\dot{\bmr} &= \ddtN \bmr = v(t)\dht{1} + \ddtD \bmr \\
&= v(t)\dht1 + (\dot{r}\cos\theta - r\omega\sin\theta)\dht1 + (\dot{r}\sin\theta + r\omega\cos\theta)\dht2 \\
&= (v(t) + \dot{r}\cos\theta - r\omega\sin\theta)\dht1 + (\dot{r}\sin\theta + r\omega\cos\theta)\dht2
\end{aligned}
$$

The inertial acceleration can be directly got as
$$
\begin{aligned}
\ddot{\bmr} &= \ddtN [(v(t) + \dot{r}\cos\theta - r\omega\sin\theta)\dht1 + (\dot{r}\sin\theta + r\omega\cos\theta)\dht2] \\
&= (\dot{v} -\ddot{r}\cos\theta-\dot{r}\dot{\theta}\sin\theta - \dot{r}\omega\sin\theta + r\omega\dot{\theta}\cos\theta)\dht1 + (\ddot{r}\sin\theta + \dot{r}\dot{\theta}\cos\theta + \dot{r}\omega\cos\theta - r\omega\dot{\theta}\sin\theta) \dht2 \\
&= (\dot{v} -\ddot{r}\cos\theta - 2\dot{r}\omega\sin\theta + r\omega^2\cos\theta)\dht1 + (\ddot{r}\sin\theta + 2\dot{r}\omega\cos\theta - r\omega^2\sin\theta) \dht2 \\
\end{aligned}
$$

>[!question]- What if the ball is free to move not just radially but in all directions? 
>Then we need to make assumptions about the friction and forces, introduce another frame to describe the relative motion between the ball and the disk.



## Textbook problem 1.14 (Grinding disk and missile)
![[fig-p1-14_grinding_disk.png|600]]

Inertial frame $\calN:\{\nht1,\nht2,\nht3\}$

Polar frame $\calE:\{\eht{r},\eht{\phi},\eht{3}\}$, centered at the center of the grind.

Polar frame $\calS:\{\sht{r},\sht{\theta},\sht{3}\}$, centered at the grind, pointing to $P$.

Constants: $R$, $r$, $h$

Time-varying variables: $\dot{\phi}$, $\dot{\theta}$

Rotation velocity vectors: 

$\bmo_{\calE/\calN} = \dot{\phi}\nht3$

$\bmo_{\calS/\calE} = - \dot{\theta}\eht{r}$ (Notice this is in the negative direction!)

$\bmo_{\calS/\calN} = \dot{\phi}\nht3 - \dot{\theta}\eht{r}$

### (a) inertial v and a
$$
\bmr = r \sht{r} + R \eht{r}
$$

$$
\begin{aligned}
\dot{\bmr} &= \dot{r}\sht{r} + r\ddtN \sht{r} + R \ddtN\eht{r} \\
&= \bm{0} + r\bmo_{\calS/\calN}\times\sht{r} + R\bmo_{\calE/\calN}\times\eht{r} \\
&= r(\dot{\phi}\nht3 - \dot{\theta}\eht{r})\times\sht{r} + R(\dot{\phi}\nht3)\times\eht{r} \\
&= r(\dot{\phi}\nht3\times\sht{r} - \dot{\theta}\eht{r}\times\sht{r}) + R(\dot{\phi}\eht{\phi}) \\
&= r(\dot{\phi}(\cos\theta\sht{r}-\sin\theta\sht{\theta})\times\sht{r} - \dot{\theta}(-\sht{\theta})) + R(\dot{\phi}\eht{\phi}) \\
&= r(\dot{\phi}(\sin\theta\sht{3} + \dot{\theta}\sht{\theta})) + R(\dot{\phi}\eht{\phi}) \\
%&\\
%&= r(\dot{\phi}\nht3 - \dot{\theta}\eht{r})\times(\cos\theta\eht{\phi}+\sin\theta\eht{3}) + R(\dot{\phi}\eht{\phi}) \\
%&= r[\dot{\phi}\nht3\times(\cos\theta\eht{\phi}+\sin\theta\eht{3}) - \dot{\theta}\eht{r}\times(\cos\theta\eht{\phi}+\sin\theta\eht{3})] + R(\dot{\phi}\eht{\phi}) \\
%&= r[\dot{\phi}\nht3\times\cos\theta\eht{\phi} + \dot{\phi}\nht3\times\sin\theta\eht{3} - \dot{\theta}\eht{r}\times\cos\theta\eht{\phi} - \dot{\theta}\eht{r}\times\sin\theta\eht{3}] + R(\dot{\phi}\eht{\phi}) \\
%&= r[-\dot{\phi}\cos\theta\eht{r} + \bm{0} - \dot{\theta}\cos\theta\eht{e} + \dot{\theta}\sin\theta\eht{\phi}] + R(\dot{\phi}\eht{\phi}) \\
\end{aligned}
$$

$$
\ddot{r} = \dots
$$

### (b) as seen by point P
A new frame $\cal{M}:\{\nht1,\nht2,\nht3\}$, which is non-rotating and non-accelerating but just moving along a straight line.

$$
\bm{\rho} = \bmr - \bmr_M
$$

$$
\begin{aligned}
\ddtM \bm{\rho} &= \ddtM \bmr - \ddtM \bmr_M \\
&= \ddtN \bmr + \bmo_{\calM/\calN}\times\bmr - \ddtN\bmr_M + \bmo_{\calM/\calN}\times\bmr_M \\
&= \ddtN \bmr - \ddtN\bmr_M \\
&= r(\dot{\phi}(\sin\theta\sht{3} + \dot{\theta}\sht{\theta}) + R(\dot{\phi}\eht{\phi})   - (-\nht2) \\
&= r(\dot{\phi}(\sin\theta\sht{3} + \dot{\theta}\sht{\theta}) + R(\dot{\phi}\eht{\phi})   + \nht2 \\
\end{aligned}
$$

$$
\ddtM \left(\ddtM \bm{\rho}\right) = \ddtN \left(\ddtN \bmr - \ddtN\bmr_M\right) = \ddot{\bmr} - \ddot{\bmr}_M = \ddot{\bmr}
$$

Alternatively, noticing that $\calM$ is non-rotating and non-accelerating, we can directly calculate the relative velocity and acceleration without taking derivatives using $\ddtM$.


## Textbook problem 1.10 (Two rotating disks)
![[fig-p1-10_two_rotating_disks.png|600]]
### (a) inertial relative between B and A
Relative position $\bmr = r_B\bht{r} - r_A\aht{r}$.

Relative velocity $\dot{\bmr}=r_B\bmo_{\calB/\calN}\times\bht{r} - r_A\bmo_{\calA/\calN}\times\aht{r}=r_B\omega_{\calB/\calN}\bht{t}-r_A\omega_{\calA/\calN}\aht{r}$ 

Relative acceleration $\ddot{\bmr}=(r_B\dot{\omega}_{\calB/\calN}\bht{t}-r_B\omega_{\calB/\calN}^2\bht{r}) - (r_A\dot{\omega}_{\calA/\calN}\aht{t}-r_A\omega_{\calA/\calN}^2\aht{r})$

### (b) B as seen from A
$$
\begin{aligned}
\ddtA \bmr &= \ddtA (r_B\bht{r} - r_A\aht{r}) = \ddtA (r_B\bht{r}) \\
&= r_B \bmo_{\calB/\calA} \times \bht{r} \\
&= r_B (\omega_{\calB/\calN} - \omega_{\calA/\calN}) \bht{3} \times \bht{r} \\
&= r_B (\omega_{\calB/\calN} - \omega_{\calA/\calN}) \bht{t} \\
\end{aligned}
$$
$$
\begin{aligned}
\ddtA \left(\ddtA \bmr\right) &= \ddtA \left(r_B (\omega_{\calB/\calN} - \omega_{\calA/\calN}) \bht{t}\right) \\
&= \left(r_B (\dot{\omega}_{\calB/\calN} - \dot{\omega}_{\calA/\calN}) \bht{t}\right) + \left(r_B (\omega_{\calB/\calN} - \omega_{\calA/\calN})^2 \bht{3} \times \bht{t}\right)\\
&= \left(r_B (\dot{\omega}_{\calB/\calN} - \dot{\omega}_{\calA/\calN}) \bht{t}\right) - \left(r_B (\omega_{\calB/\calN} - \omega_{\calA/\calN})^2 \bht{r}\right)\\
\end{aligned}
$$


## Textbook problem 1.12 (rotating disk on a telescoping rod)
![[fig-p1-12_rotating_disk_telescoping_rod.png|600]]

Inertial Cartesian frame $\calN$

Rod polar frame $\calE$

Disk polar/spherical frame $\calS$

Constants: $\dot{L}$, $\dot{\theta}$, $\dot{\alpha}$, $r$

$$
\bmr = L\eht{L} + r \sht{r}
$$
$$
\begin{aligned}
\dot{\bmr} &= \dot{L}\eht{L} + L \bmo_{\calE/\calN}\times\eht{L} + r \ddtN \sht{r} \\
&= \dot{L}\eht{L} + L \dot{\theta}\eht{\theta} + r \ddtE \sht{r} + r \bmo_{\calE/\calN} \times \sht{r} \\
&= \dot{L}\eht{L} + L \dot{\theta}\eht{\theta}  + r \bmo_{\calS/\calE} \times \sht{r} + r \bmo_{\calE/\calN} \times \sht{r} \\
&= \dot{L}\eht{L} + L \dot{\theta}\eht{\theta}  + r \dot{\alpha} \sht{\alpha} + r \dot{\theta} \sht{\alpha} \\
\end{aligned}
$$
$$
\begin{aligned}
\ddot{\bmr} &= \ddtN \left( \dot{L}\eht{L} + L \dot{\theta}\eht{\theta}  + r \dot{\alpha} \sht{\alpha} + r \dot{\theta} \sht{\alpha} \right) \\
&= \ddot{L}\eht{L} + \dot{L}\dot{\theta}\eht{\theta}   +   \dot{L}\dot{\theta}\eht{\theta} + L \ddot{\theta}\eht{\theta} + L\dot{\theta}\ddtN\eht{\theta}   +    r \ddot{\alpha}\sht{\alpha} + r\dot{\alpha}\ddtN\sht{\alpha}   +    r \ddot{\theta} \sht{\alpha} + r\dot{\theta}\ddtN\sht{\alpha} \\
&= \dot{L}\dot{\theta}\eht{\theta}   +   \dot{L}\dot{\theta}\eht{\theta} + L\dot{\theta}\bmo_{\calE/\calN}\times\eht{\theta}   +   r\dot{\alpha}\bmo_{\calS/\calN}\times\sht{\alpha}   +  r\dot{\theta}\bmo_{\calS/\calN}\times\sht{\alpha} \\
&= \dot{L}\dot{\theta}\eht{\theta}   +   \dot{L}\dot{\theta}\eht{\theta} - L\dot{\theta}^2\eht{L}   -   r\dot{\alpha}(\dot{\alpha}+\dot{\theta})\sht{r}   -  r\dot{\theta}(\dot{\alpha}+\dot{\theta})\sht{r} \\
&= 2\dot{L}\dot{\theta}\eht{\theta}    - L\dot{\theta}^2\eht{L}   -   r(\dot{\alpha}+\dot{\theta})^2\sht{r} \\
\end{aligned}
$$

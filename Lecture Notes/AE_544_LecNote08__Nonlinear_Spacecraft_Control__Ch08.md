---
date created: 2025-03-03T09:54:12-05:00
date modified: 2026-04-13T02:38:12-04:00
---

# AE_544_LecNote08\__Nonlinear_Spacecraft_Control__Ch08
![[README#Disclaimers]]


Naturally, any real system will not be modeled perfectly and unmodeled dynamics and external influences will cause the spacecraft to drift from the desired trajectory or final state, i.e., the inverse solution for the open loop contains modeling approximations.

Designing spacecraft attitude control laws combines the skills of rigid body kinematics and kinetics, as well as control methodology. 
In fact, the proper choice of attitude coordinates can be crucial to the usability of the resulting control law. 
If large, arbitrary rotations are to be performed, clearly any set of the Euler angle family would be a poor choice because of their small nonsingular rotation range. 


It is not intended as a complete study of nonlinear stability and control theory. 
Students are assumed to be already familiar with basic linear control concepts, and of course also linear algebra.


## Stabilities of System

A state vector point $\bmx_e$ is said to be an <u>equilibrium state</u> (or equilibrium point) of a dynamical system described by $\dot{\bmx} = \bmf(\bmx, t)$ at time $t_0$ if
$$
\bmf(\bmx_e, t) = 0 \qquad \forall\, t > t_0
$$

This definition indicates that once the system reaches the state $\bmx_e$ , it will remain there for all time. 
However, this definition does not imply the stability of the equilibrium point.


![[fig-v4-8-1_different_stabilities.png|420]]

Given $\delta>0$, a state vector $\bmx$ is said to be in the <u>neighborhood</u> $B_\delta(\bmx_r)$ of the reference state $\bmx_r$, i.e. $\bmx(t) \in B_\delta(\bmx_r)$, if
$$
\|\bmx(t) - \bmx_r(t)\| < \delta 
$$
This definition has used the standard Euclidean norm, which is a $n$-dimensional sphere around the reference state. 
But it can generate to different norms in more complicated discussions.


**<u>Lagrange Stability</u>**: The motion $\bmx(t)$ is said to be Lagrange stable (or bounded) relative to $\bmx_r(t)$ if there exists a $\delta>0$ such that
$$
\bmx(t) \in B_\delta(\bmx_r(t)) \qquad \forall t>t_0
$$
This essentially means the motion won't diverge and there is a upper boundary for the deviation.

**<u>Lyapunov Stability</u>**: The motion $\bmx(t)$ is said to be Lyapunov stable (or stable) relative to $\bmx_r(t)$ for each $\epsilon>0$ there exists a $\delta(\epsilon)$ > 0 such that
$$
\bmx(t_0) \in B_\delta(\bmx_r(t_0))  \quad \Longrightarrow \quad \bmx(t)\in B_\epsilon(\bmx_r(t)) \qquad \forall t>t_0
$$
It can be as close as one desires: for any desired error in the future, one can find a suitable initial error.


**<u>Asymptotic Stability</u>**: The motion $\bmx(t)$ is asymptotically stable relative to $\bmx_r(t)$ if $\bmx(t)$ is Lyapunov stable and there exists a $\delta>0$ such that
$$
\bmx(t_0) \in B_\delta(\bmx_r(t_0)) \quad \Longrightarrow \quad \lim_{ t \to \infty } \bmx(t) = \bmx_r(t)
$$
It will eventually become the same thing, but may take a very long time.


**<u>Exponential Stability</u>**: The motion $\bmx(t)$ is said to be exponentially stable relative to $\bmx_r(t)$ if $\bmx(t)$ is asymptotically stable and there exists a $\delta>0$ such and corresponding $\alpha(\delta)>0$ and $\lambda(\delta)>0$ such that
$$
\bmx(t_0) \in B_\delta(\bmx_r(t_0)) \quad \Longrightarrow \quad \|\bmx(t)-\bmx_r(t)\| \leq \alpha e^{\lambda t} \|\bmx(t_0) - \bmx_r(t_0)\|
$$


<u>Global Stability</u>: The motion $\bmx(t)$ is said to be globally stable (asymptotically stable or exponentially stable) relative to $\bmx_r(t)$ if $\bmx(t)$ is stable (asymptotically stable or exponentially stable) for any initial state vector $\bmx(t_0)$.



Of all the stability definitions presented, the concept of Lagrange stability is clearly the weakest, while exponential stability is the strongest statement. Unfortunately, proving exponential stability is also the most challenging.


## Lyapunov Indirect Method (Linearization by Truncating Taylor's Expansion)

For a controlled system
$$
\dot{\bmx} = \bmf(\bmx, \bmu, t)
$$
with the reference motion $\bmx_r(t)$ and $\bmu_r(t)$, the dynamics of the difference $\delta\bmx=\bmx-\bmx_r$ can be expanded as
$$
\begin{aligned}
\delta\dot{\bmx} &= \dot{\bmx} - \dot{\bmx}_r \\
&= \bmf(\bmx_r,\bmu_r, t) + \left[\pp{\bmf(\bmx_r,\bmu_r, t)}{\bmx}\right]\trans \delta \bmx + \left[\pp{\bmf(\bmx_r,\bmu_r, t)}{\bmu}\right]\trans \delta\bmu + \pp{\bmf(\bmx_r,\bmu_r, t)}{t} \delta t + O(\|(\bmx,\bmu,t))\|^2) - \bmf(\bmx_r,\bmu_r, t)
\end{aligned}
$$
where $\delta\bmu=\bmu-\bmu_r$.
If we ignore the higher-order terms and set $\delta t = 0$, then we have the linearized system
$$
\delta \dot{\bmx} = \left[\pp{\bmf(\bmx_r,\bmu_r, t)}{\bmx}\right]\trans \delta \bmx + \left[\pp{\bmf(\bmx_r,\bmu_r, t)}{\bmu}\right]\trans \delta\bmu 
\equiv [A]\delta \bmx + [B] \delta\bmu
$$
which becomes a typical linear system.


<u>Lyapunov’s Linearization/Indirect Method</u>: Assume the linearized dynamical system is found to be \
(1) <u>strictly stable</u>; then the nonlinear system is <u>locally asymptotically stable</u>. \
(2) <u>unstable</u>; then the nonlinear system is <u>unstable</u>. \
(3) <u>marginally stable</u>; then one cannot conclude anything about the stability of the nonlinear system without further analysis. (<u>nonlinear stability undertermined</u>)

The theorem makes intuitive sense. 
If the linearized system is either strictly stable or unstable, then one would expect that a neighborhood would exist where the nonlinear system would also be either stable or unstable. 
However, if the linearized system is only marginally stable, then the neglected second and higher order terms could render the nonlinear system either stable or unstable.


## Lyapunov Direct Method (Using a Lyapunov Function)

Proving stability of nonlinear systems with the basic stability definitions and without resorting to local linear approximations can be quite tedious and difficult. 
Lyapunov’s direct method provides a tool to make rigorous, analytical stability claims of nonlinear systems by <u>studying the behavior of a scalar, energy-like Lyapunov function</u>. 

A **major benefit** of this method is that this can be done without having to solve the nonlinear differential equations. 

### Lyapunov Function

<u>Positive Definite (or Semidefinite) Function</u>: 
A scalar continuous
function $V(\bmx)$ is said to be locally positive definite (or semidefinite) about $\bmx_r$ if 
$$
\bmx = \bmx_r  \Longrightarrow V(\bmx) = 0
$$
and there exists a $\delta>0$ such that
$$
\forall \bmx \in B_\delta(\bmx_r) \Longrightarrow V(\bmx) > 0 \quad (\text{or } \ge 0)
$$

<u>Positive Definite (or Semidefinite) Matrix</u>: 
A matrix $[K]$ is said to be positive definite (or semidefinite) if ro arbitrary state vector $\bmx$, it guarantees
$$
\bmx\trans \, [K] \, \bmx > 0 \quad (\text{or } \ge 0)
$$


**<u>Lyapunov Function</u>**: 
The scalar function $V(\bmx)$ is a Lyapunov function for the dynamical system $\dot{\bmx} = \bmf(\bmx)$ if it is continuous and there exists a $\delta > 0$ such that for any $\bmx\in B_\delta(\bmx_r)$: \
(1) $V(\bmx)$ is a positive definite function about $\bmx_r$. \
(2) $V(\bmx)$ has continuous partial derivatives. \
(3) $\dot{V}(\bmx)$ is negative semidefinite. 

The Lyapunov function $V(\bmx)$ is generally time-varying because $\bmx(t)$ is time-varying.

The derivative of the Lyapunov function $\dot{V}(\bmx)$ is a directional derivative of $V$ along the system trajectory, because
$$
\dot{V} = \left[\pp{V}{\bmx}\right]\trans \dot{\bmx} = \left[\pp{V}{\bmx}\right]\trans \bmf(\bmx)
$$

![[fig-8-2_Lyapunov_function_as_a_bowl.png|350]]


### Lyapunov Theorems (Criteria for Stabilities)

All the criteria below are sufficient conditions, meaning that one cannot conclude that the system is unstable if they are not fulfilled.

**<u>Criterion of Lyapunov Stability</u>**: 
If a Lyapunov function $V(\bmx)$ exists for the dynamical system $\dot{\bmx}=\bmf(\bmx)$, then this system is stable about the origin.


**<u>Criterion of Asymptotic Stability</u>**:
Assume $V(\bmx)$ is a Lyapunov function about $\bmx_r(t)$ for the dynamical system $\dot{\bmx}=\bmf(\bmx)$; the system is asymptotically stable if \
(1) the system is stable about $\bmx_r(t)$. \
(2) $\dot{V}(\bmx)$ is negative definite about $\bmx_r(t)$.


**<u>Criterion of Exponential Stability</u>**:
Assume $V(\bmx)$ is a Lyapunov function about $\bmx_r(t)$ of the dynamical system $\dot{\bmx}=\bmf(\bmx)$ and the system is asymptotically stable if, then the system is exponentially stable if there exists scalar constants $c_2 \geq c_1 >0$ and $\lambda>0$, $k>0$ such that \
(1) $\dot{V} \leq -\lambda V$. \
(2) $c_1 \|\bmx\|^k \leq V(\bmx) \leq c_2\|\bmx\|^k$.

>[!question] What if the system converges quicker than an exponential speed?

These one are just basic ones based on the definition. 
There are more criteria for the Lyapunov stability theory which are omitted for the class and some are not even covered in the textbook.


## Generating Lyapunov Functions

Lyapunov’s stability theory provides a very elegant method to guarantee stability characteristics of nonlinear dynamical systems without having to actually solve the corresponding equations of motion.

~~A drawback to these Lyapunov methods is that~~ the process of finding appropriate Lyapunov functions is not always obvious.

There are two common categories of elemental Lyapunov functions that measure velocity or functions that measure position state errors. 
Separate elemental Lyapunov functions can be linearly combined to provide the desired system Lyapunov function.


### Elemental Velocity–Based Lyapunov Functions (Hamiltonian $\calH$ used)

The reference velocity vector $\bmq_r(t)$ is generally non-zero. 
The Lyapunov function $V$ is defined in terms of the velocity state error vector $\delta\bmq$
$$
\delta \dot{\bmq} = \dot{\bmq} - \dot{\bmq}_r
$$
as the kinetic-energy-like function expressed as
$$
V(\dot{\bm{q}}) = \tfrac{1}{2} \, \delta \dot{\bm{q}}{\trans} [M(\bm{q})] \, \delta \dot{\bm{q}}
\tag{8.26}
$$
where, in general, the mass matrix $[M(\bmq)]$ is positive definite and symmetric.

The derivative of Lyapunov function $V$ is
$$
\dot{V} = \delta \dot{\bm{q}}{\trans} \left( [M] \, \delta \ddot{\bm{q}} + \tfrac{1}{2} [\dot{M}] \, \delta \dot{\bm{q}} \right)
\tag{8.27}
$$

The standard Lagrange equations of motion for a natural unconstrained system are given in the matrix format as
$$
[M(\bm{q})] \ddot{\bm{q}} = -[\dot{M}(\bm{q}, \dot{\bm{q}})] \dot{\bm{q}} + \tfrac{1}{2} \textcolor{red}{ \dot{\bm{q}}{\trans} [M_q(\bm{q})] \dot{\bm{q}} } + \bm{Q}
\tag{8.19}
$$
with 
$$
\textcolor{red}{ \dot{\bm{q}}{\trans} [M_q(\bm{q})] \dot{\bm{q}} } 
=
\begin{pmatrix}
\dot{\bm{q}}{\trans} \left[ \pp{M}{q_1} \right] \dot{\bm{q}} \\
\vdots \\
\dot{\bm{q}}{\trans} \left[ \pp{M}{q_N} \right] \dot{\bm{q}}
\end{pmatrix}
\tag{8.20}
$$

Substituting into $\dot{V}$ and we have
$$
\begin{aligned}
\dot{V} &= \delta \dot{\bm{q}}{\trans} \left( [M] \, \delta \ddot{\bm{q}} + \tfrac{1}{2} [\dot{M}] \, \delta \dot{\bm{q}} \right) \\
&= \delta\dot{\bm{q}}{\trans} \left( \textcolor{blue}{ [M] \, \ddot{\bm{q}} } - [M] \, \ddot{\bmq}_r + \tfrac{1}{2} [\dot{M}] \,  (\dot{\bm{q}} - \dot{\bm{q}}_r) \right) \\
&= \delta\dot{\bm{q}}{\trans} \left( \textcolor{blue}{ -[\dot{M}] \dot{\bm{q}} + \tfrac{1}{2} \dot{\bm{q}}{\trans} [M_q] \dot{\bm{q}} + \bm{Q} } - [M] \ddot{\bmq}_r + \tfrac{1}{2} [\dot{M}] \,  (\dot{\bm{q}} - \dot{\bm{q}}_r) \right) \\
&= \delta\dot{\bm{q}}{\trans} \left( - \tfrac{1}{2} [\dot{M}] \,  (\dot{\bm{q}} + \dot{\bm{q}}_r) + \tfrac{1}{2} \dot{\bm{q}}{\trans} [M_q] \dot{\bm{q}} + \bm{Q} - [M] \ddot{\bmq}_r  \right)
\end{aligned}
\tag{8.28}
$$
When tracking a time varying reference state, the elemental velocity-measure
Lyapunov function rates no longer simplify to the classical power form of the
work-energy equation in Eq. (8.25).


> Notice that here $\ddot{\bmq}_r$ is kept because it requires evaluations at $\bmq_r$ instead of $\bmq$, which is
> $$
> [M(\bm{q}_r)] \ddot{\bm{q}}_r = -[\dot{M}(\bm{q}_r, \dot{\bm{q}}_r)] \dot{\bm{q}}_r + \tfrac{1}{2} \dot{\bm{q}}_r{\trans} [M_q(\bm{q}_r)] \dot{\bm{q}_r}
> $$


Because most mechanical systems are natural systems, the Hamiltonian specializes for this case to the total system energy. This motivates the alternative use of the Hamiltonian as a more general Lyapunov function candidate, which is
$$
\calH(\bmq,\bmp) = \bmp\trans \dot{\bmq} - \calL(\bmq, \dot{\bmq})
$$

$$
\begin{aligned}
\dot{\calH} &= \dot{\bm{p}}\trans \dot{\bm{q}} + \bm{p}\trans \ddot{\bm{q}} 
- \pp{\calL}{t} 
- \left(\pp{\calL}{\bm{q}}\right)\trans \dot{\bm{q}} 
- \left(\pp{\calL}{\dot{\bm{q}}}\right)\trans \ddot{\bm{q}} \\
&= \dot{\bm{p}}\trans \dot{\bm{q}} + \bm{p}\trans \ddot{\bm{q}} 
- \pp{\calL}{t} 
- \left(\pp{\calL}{\bm{q}}\right)\trans \dot{\bm{q}} 
- \left(\pp{\calL}{\dot{\bm{q}}}\right)\trans \ddot{\bm{q}}
\end{aligned}
\tag{8.42}
$$

After setting the Lyapunov function $V$ equal to $\calH$ and using the canonical equations
$$
\begin{aligned}
\dot{\bmq} &= \pp{\calH}{\bmp} \\
\dot{\bmp} &= \pp{\calH}{\bmq} + \bmQ
\end{aligned}
$$
and the relationship (notice: recall the difference between these two partial derivatives on LHS and RHS)
$$
\pp{\calH}{\bmq} = - \pp{\calL}{\bmq}
$$
the Lyapunov time rate $\dot{V}$ can be written as
$$
\dot{V} = 
\left(- \pp{\calL}{\bmq}+\bmQ\right)\trans \dot{\bm{q}} + \bm{p}\trans \ddot{\bm{q}} 
- \pp{\calL}{t} 
- \left(\pp{\calL}{\bm{q}}\right)\trans \dot{\bm{q}} 
- \bmp\trans \ddot{\bm{q}} = \bmQ^T \dot{\bmq} - \pp{\calL}{t}
$$

For natural systems, $\calL(\bmq,\dot{\bmq})$ is not an explicit function time, and the Hamiltonian rate reduces to
$$
\dot{V} = \dot{\calH}(\bmq,\bmp) = \bmQ\trans \dot{\bmq}
\tag{8.44}
$$

Two benefits of using Hamiltonian as Lyapunov functions:
1. $V$ is not explicitly required because $\dot{V} = \dot{\calH}$ is available directly in Eq. (8.44). 
2. A stabilizing control vector $\bmQ$ for the regulator control problem will remain stabilizing even in the presence of model errors. This is a direct consequence of the $V$ expression being independent of the system dynamics (depends only on forces, moments, and velocities of the points to which forces are applied).

>[!info] The second point will be verified in the Programming Project 02.


### Elemental Position–Based Lyapunov Functions

This section provides elemental position-based Lyapunov functions that allow us to control the position of a body.
Thought $\bmq$ is of interest, $\dot{\bmq}$ is still treated as the control variable.

For a Lyapunov function
$$
V(\bmq) = \frac{1}{2} \bmq\trans \bmq
$$
where the position vector $\bmq$ is assumed to be measured relative to the target state $\bmq_r$. 

The derivative of the Lyapunov function $V$ is 
$$
\dot{V} = \dot{\bmq}\trans \bmq
$$

Defining the steering law $\dot{\bmq}$ to be 
$$
\dot{\bmq} = - [K] \bmq
$$
where the symmetric matrix $[K]$ must be positive definite to guarantee that the Lyapunov function is positive definite.

This steering law guarantees the rate of Lyapunov function is negative definite, which is
$$
\dot{V} = -\bmq\trans [K] \bmq < 0
$$

When extended to rigid-body control, the choice of attitude representation matters a lot and usually it depends on the application.


## Summary

The energy-like function Hamiltonian $\calH$ can be used as a starting point to generate a Lyapunov function for the design of a continuous control law.
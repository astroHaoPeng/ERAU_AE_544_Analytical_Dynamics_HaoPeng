---
date created: 2025-02-09T16:24:50-05:00
date modified: 2025-04-04T02:42:21-04:00
---
# AE_544_LecNote06\__Variational_Methods__Ch06
![[README#Disclaimers]]

In this chapter, we begin by developing basic concepts from variational calculus and then turn to the development of the most important results in variational mechanics:
1. A family of variational principles due to Hamilton that hold for the motion of very general systems, including distributed parameter systems.
2. Hamilton's principal function $\calS \equiv \int_{t_0}^{t_f} \calL \dt$, which has several important properties.
3. Extensions of Lagrange's equations for the case of distributed parameter systems.


## Fundamentals of Variational Calculus

![[fig-6-1_path_and_time_variations.png|500]]

We seek to determine a space time trajectory or path $\bmx\in\fkR^n$ that causes a given <u>functional</u> $\calJ(\bmx(t),t_0,t_f)$ to achieve a local minimum (or maximum). 
$\calJ$ is considered a functional because its argument list contains a vector of unknown functions $\bmx(t) = (x_1(t), x_2(t), \dots, x_n(t))\trans$.

Let us consider the special case that $\calJ(\bmx(t),t_0,t_f)$ is expressible as a path integral:
$$
\calJ = \calJ(\bmx(t), t_0, t_f) = \int_{t_0}^{t_f} \calF(\bmx(t), \dot{\bmx}(t), t) \, dt
\tag{6.1}
$$

Suppose $\calF$ and $\bmx$ are continuous functions and twice differentiable with respect to all argument (functions of class $C_2$), and $\bmx(t)$ is the minimal solution from $t_0$ to $t_f$. 
Denote a neighboring path and times as $\{\tilde{\bmx}(t), \tilde{t}_0, \tilde{t}_f\}$, then the first path variation is
$$
\delta\bmx(t) \equiv \tilde{\bmx}(t) - \bmx(t)
\tag{6.2}
$$

$$
\delta \dot{\bmx}(t) = \dot{\tilde{\bmx}}(t) - \dot{\bmx}(t) \equiv \ddt (\delta\bmx)
\tag{6.3}
$$
Thus the variational operator $\delta(\,)$ and the differential operator ${\rm d/d}t(\,)$ are interchangeable.

The varied state vector and its time derivative are
$$
\begin{aligned}
\tilde{\bmx}(t) &= \bmx(t) + \delta \bmx(t) \\
\dot{\tilde{\bmx}}(t) &= \dot{\bmx}(t) + \delta \dot{\bmx}(t)
\end{aligned}
\tag{6.5}
$$

The varied path integral of $\tilde{\calJ}$ is
$$
\tilde{\calJ} = \calJ(\tilde{\bmx}(t), \tilde{t}_0, \tilde{t}_f) = \int_{\tilde{t}_0}^{\tilde{t}_f} \calF(\bmx(t) + \delta \bmx(t), \dot{\bmx}(t) + \delta \dot{\bmx}(t), t) \, dt
\tag{6.6}
$$

The variation $\delta\calJ$ is obtained as
$$
\begin{aligned}
\delta \calJ &\equiv \tilde{\calJ} - \calJ \\
&= \textcolor{red}{ \int_{t_0 + \delta t_0}^{t_f + \delta t_f} \calF(\bmx(t) + \delta \bmx(t), \dot{\bmx}(t) + \delta \dot{\bmx}(t), t) \, dt } - \int_{t_0}^{t_f} \calF(\bmx(t), \dot{\bmx}(t), t) \, dt
\end{aligned}
\tag{6.7}
$$

Express the first integral using Taylor series, and truncate at the first-order terms, we have
$$
\begin{aligned}
&\phantom{=\,} \textcolor{red}{ \int_{t_0 + \delta t_0}^{t_f + \delta t_f} \calF(\bmx(t) + \delta \bmx(t), \dot{\bmx}(t) + \delta \dot{\bmx}(t), t) \, dt } \\
%
&\boxed{\approx} \int_{t_0}^{t_f} \calF(\bmx(t), \dot{\bmx}(t), t) \, dt 
+ \left[ \pp{}{\bmx} \left( \int_{t_0}^{t_f} \calF(\bmx(t), \dot{\bmx}(t), t) \, dt  \right) \right]\trans \delta \bmx \\
&\phantom{=\,} + \left[ \pp{}{\dot{\bmx}} \left( \int_{t_0}^{t_f} \calF(\bmx(t), \dot{\bmx}(t), t) \, dt  \right)\right]\trans \delta \dot{\bmx} 
+ \pp{}{t_0} \left( \int_{t_0}^{t_f} \calF(\bmx(t), \dot{\bmx}(t), t) \, dt  \right) \delta t_0 \\
&\phantom{=\,} + \pp{}{t_f} \left( \int_{t_0}^{t_f} \calF(\bmx(t), \dot{\bmx}(t), t) \, dt  \right) \delta t_f \\
%
&\boxed{=} \int_{t_0}^{t_f} \calF(\bmx(t), \dot{\bmx}(t), t) \, dt 
+ \int_{t_0}^{t_f} \left( \pp{}{\bmx} \calF(\bmx(t), \dot{\bmx}(t), t) \cdot\delta \bmx \right)\, dt \\
&\phantom{=\,} + \int_{t_0}^{t_f} \left( \pp{}{\dot{\bmx}} \calF(\bmx(t), \dot{\bmx}(t), t) \cdot\delta \dot{\bmx} \right)\, dt 
+ \Big[ - \calF(\bmx(t_0), \dot{\bmx}(t_0), t_0)  \cdot\delta t_0 \Big] \\
&\phantom{=\,} + \calF(\bmx(t_f), \dot{\bmx}(t_f), t_f) \cdot \delta t_f \\
\end{aligned}
\tag{1st term in 6.7}
$$

>[!info] Taylor expansion for multi-variable function $K(\bmx, \dot{\bmx}, t_0, t_f)$ is
> $$
> K = \left(\pp{K}{\bmx}\right)\trans d\bmx + \left(\pp{K}{\dot{\bmx}}\right)\trans d \dot{\bmx} + \pp{K}{t_0} dt_0 + \pp{K}{t_f} dt_f + O(\|d\bmx, d \dot{\bmx}, dt_0, dt_f\|^2)
> $$

Plug the 1st order Taylor expansion back into Eq. (6.7) and we have
$$
\begin{aligned}
\delta \calJ &= 
\int_{t_0}^{t_f} \left[ \left( \pp{\calF(\ast)}{\bmx(t)} \right) \trans \delta \bmx(t) \right] dt 
+ \textcolor{blue}{ \int_{t_0}^{t_f} \left[ \left( \pp{\calF(\ast)}{\dot{\bmx}(t)} \right) \trans \delta \dot{\bmx}(t) \right] dt  } \\
&\phantom{=\,}+ \calF(\bmx(t_f), \dot{\bmx}(t_f), t_f) \delta t_f 
- \calF(\bmx(t_0), \dot{\bmx}(t_0), t_0) \delta t_0
\end{aligned}
\tag{6.8}
$$

If $\calJ$ is minimized, a necessary condition is that for arbitrary $\delta\bmx$, $\delta t_0$, $\delta t_f$, 
the variation $\delta\calJ$ has to vanish, or in other words, be equal to 0.

Notice that we can do integral by parts for the second term in Eq. (6.8), which is
$$
\int_{t_0}^{t_f} \left[ \pp{\calF(\ast)}{\dot{\bmx}(t)} \right] \trans \delta \dot{\bmx}(t) \, dt 
=
\textcolor{blue}{ \left( \left[ \pp{\calF(\ast)}{\dot{\bmx}(t)} \right] \trans \delta \bmx(t) \right) \Bigg|_{t_0}^{t_f} - \int_{t_0}^{t_f} \ddt \left[ \pp{\calF(\ast)}{\dot{\bmx}(t)} \right] \trans \delta \bmx(t) \, dt }
\tag{6.10}
$$
This finally gives us an expression of the variation as a function of just $\delta\bmx$ and terminal times $t_0$ and $t_f$, which is
$$
\begin{aligned}
\delta \calJ &= \int_{t_0}^{t_f} \left[ \left( \pp{\calF(\ast)}{\bmx(t)} \right) \trans \delta \bmx(t) \right] dt 
+ \textcolor{blue}{ \left( \left[ \pp{\calF(\ast)}{\dot{\bmx}(t)} \right] \trans \delta \bmx(t) \right) \Bigg|_{t_0}^{t_f} - \int_{t_0}^{t_f} \ddt \left[ \pp{\calF(\ast)}{\dot{\bmx}(t)} \right] \trans \delta \bmx(t) \, dt } \\
&\phantom{=\,}+ \calF(\bmx(t_f), \dot{\bmx}(t_f), t_f) \delta t_f 
- \calF(\bmx(t_0), \dot{\bmx}(t_0), t_0) \delta t_0 \\
%
&= \int_{t_0}^{t_f} \left[ \pp{\calF(\ast)}{\bmx(t)}      -    \ddt \left( \pp{\calF(\ast)}{\dot{\bmx}(t)} \right) \right] \trans \delta \bmx(t) dt 
+ \left( \left[ \pp{\calF(\ast)}{\dot{\bmx}(t)} \right] \trans \delta \bmx(t) \right) \Bigg|_{t_0}^{t_f} \\
&\phantom{=\,}+ \calF(\bmx(t_f), \dot{\bmx}(t_f), t_f) \delta t_f 
- \calF(\bmx(t_0), \dot{\bmx}(t_0), t_0) \delta t_0
\end{aligned}
\tag{6.11}
$$

>[!info] The reason we prefer Eq. (6.11) over Eq. (6.8) is that usually we have constraints on the initial and final state $\bmx(t_0)$ or $\bmx(x_f)$ instead of their derivatives. 

![[fig-6-1_path_and_time_variations.png|500]]

Notice that $\delta\bmx(t), \delta\bmx(t_0), \delta\bmx(t_f), \delta t_0, \delta t_f$ are all independent and shall be considered independently. 
This leads to the necessary conditions below: \
<u>Euler-Lagrange equations:</u>
$$
\pp{\calF(\ast)}{\bmx(t)}      -    \ddt \left( \pp{\calF(\ast)}{\dot{\bmx}(t)} \right) = 0
\tag{6.12}
$$
^Euler-Lagrange-equations

and <u>transversality conditions:</u>
$$
\begin{aligned}
\left[ \pp{\calF(\bmx(t_0),\dot{\bmx}(t_0),t_0)}{\dot{\bmx}(t_0)} \right] \trans \cdot \delta \bmx(t_0) = 0 \\
\left[ \pp{\calF(\bmx(t_f),\dot{\bmx}(t_f),t_f)}{\dot{\bmx}(t_f)} \right] \trans \cdot \delta \bmx(t_f) = 0 \\
\calF(\bmx(t_f), \dot{\bmx}(t_f), t_f) \cdot \delta t_f = 0 \\
\calF(\bmx(t_0), \dot{\bmx}(t_0), t_0) \cdot \delta t_0 = 0
\end{aligned}
\tag{6.13}
$$

>[!warning] The fact they are independent does NOT necessarily imply that they can be chosen arbitrarily. 
>They still depends on the available initial conditions or terminal constraints. (Distinguish the variation from the virtual displacements in d`Alembert's Principle.)

An important special case is the ‘‘fixed endpoint problem'' in which the boundary conditions $\delta\bmx(t), \bmx(t_0), \bmx(t_f),  t_0, t_f$ are all given and fixed, rendering the variations $\delta\bmx(t_0), \delta\bmx(t_f), \delta t_0, \delta t_f$ all zeros.
In this case, all the transversality conditions are satisfied naturally, and the Euler-Lagrange equations are the only necessary conditions for an extreme $\calJ$.


## Hamilton's Principal Function $\calS$

Recall the Lagrange's Equations with all potential forces:
![[AE_544_LecNote05__Lagrangian_Dynamics__Ch05#^Lagranges-equation-conservative-forces]]
which is exactly in the form of Euler-Lagrange equation we just obtained:
![[#^Euler-Lagrange-equations]]

Therefore, we can conclude that the <u>Hamilton's principal function</u> $\calS$
$$
\calS = \int_{t_0}^{t_f} \calL \, dt
\tag{6.16}
$$
is an extremum for dynamical motions with zero generalized forces on the right side of Eq. (6.15), and for this class of systems we have the simplest version of Hamilton's variational principle
$$
\delta \calS = 0.
\tag{6.17}
$$


%% Add the example of cycloid here if time permits. %%


## Hamilton's Variational Principles

### Virtual Displacements vs Path Variations

 Consider a "true trajectory" (one satisfying Newton's laws or Lagrange's equations) $\bmR_i(t)$. 

![[fig-6-2_virtual_displacement.png|500]] \
At each give epoch $t_j$, there is an arbitrary virtual displacement $\delta\bmR_i(t_j)$, so the entire arbitrary differential virtual displacement locates an infinite set of neighboring points.
The virtual displacements $\delta\bmR_i(t_j)$ and $\delta\bmR_i(t_k)$ bear no relationship to each other; they are arbitrary and independent as long as they are of differential magnitude. 

![[fig-6-2_path_variations.png|500]] \
Differently, in Fig. 6.2b, the arbitrary variational path $\tilde{\bmR}_i(t)$ is another $C_2$ smooth path nearly the true trajectory, and the variation $\delta\bmR_i(t) = \tilde{\bmR}_i(t) - {\bmR}_i(t)$ is also a $C_2$ function.
So, two displacements $\delta\bmR_i(t_j)$ and $\delta\bmR_i(t_k)$ at different epochs are dependent.
It $t_j$ and $t_k$ are close enough, this indicates they must satisfy the $C_2$ smooth condition. 

Both ${\bmR}_i(t)$ and $\tilde{\bmR}_i(t)$ satisfy all system constraints, but <u>only ${\bmR}_i(t)$ are true paths
satisfying the system equations of motion</u>.

As a consequence of the fact that the general virtual displacements contain path variations as a special case, variational results obtained using virtual displacements typically hold for the special case of path variations as well.

>[!done] Virtual displacement $\supset$ Path variation



### Hamilton's Principle Derived from D'Alembert's Principle

Let $\bmF_i$ include all virtually working forces, recall that the d'Alembert's principle is obtained by combining
![[AE_544_LecNote05__Lagrangian_Dynamics__Ch05#^virtual-work-definition]] 
and
![[AE_544_LecNote05__Lagrangian_Dynamics__Ch05#^dalemberts-principle-most-general-form]]
such that we have
$$
\sum_{i=1}^{N} \left( \bm{F}_i - m_i \ddot{\bm{R}}_i \right) \cdot \delta \bm{R}_i = 0
\tag{6.18}
$$

>[!question] Relation to other versions of d'Alembert's principle?
>![[AE_544_LecNote05__Lagrangian_Dynamics__Ch05#^dalemberts-principle-different-forms]]


Although d'Alembert's principle was derived for the most general case that $\delta\bmR_i$ are instantaneous virtual displacements, this condition also holds for the special case that $\delta\bmR_i(t)$ are path variations with $\tilde{\bmR}_i(t) = \bmR_i(t) + \delta\bmR_i(t)$ locating an infinite family of neighboring varied paths. 




The total kinetic energy definition of a system of $N$ particles along the true path $\bmR_i(t)$ is
$$
T = \frac{1}{2} \sum_{i=1}^N m_i \dot{\bmR}_i \cdot \dot{\bmR}_i
\tag{6.19}
$$
and the total kinetic energy function evaluated at the same moment but on the differentially displaced varied motion $\tilde{\bmR}_i(t)$ is
$$
\tilde{T} = \frac{1}{2} \sum_{i=1}^N m_i \dot{\tilde{\bmR}}_i \cdot \dot{\tilde{\bmR}}_i
\tag{6.20}
$$

Thus, we have the path variation of kinetic energy as
$$
\begin{aligned}
\delta T &= \tilde{T} - T \\
&= \frac{1}{2} \sum_{i=1}^N m_i \dot{\bmR}_i \cdot \dot{\bmR}_i - \frac{1}{2} \sum_{i=1}^N m_i \dot{\tilde{\bmR}}_i \cdot \dot{\tilde{\bmR}}_i \\
&= \frac{1}{2} \sum_{i=1}^N m_i \dot{\bmR}_i \cdot \dot{\bmR}_i - \frac{1}{2} \sum_{i=1}^N m_i (\dot{\bmR}_i + \delta\dot{\bmR}_i) \cdot (\dot{\bmR}_i + \delta\dot{\bmR}_i) \\
&\approx\sum_{i=1}^N m_i \dot{\bmR}_i \cdot \delta\dot{\bmR}_i
\end{aligned}
\tag{6.21}
$$

We can get the following relationship by applying the chain rule of the time derivative to a special summation :
$$
\ddtN\left( \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \delta \bm{R}_i \right) = \sum_{i=1}^{N} m_i \ddot{\bm{R}}_i \cdot \delta \bm{R}_i + \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \delta \dot{\bm{R}}_i
\tag{6.22}
$$
Notice that we have switch the order of derivatives and variations to get the above expression.
The <u>first term on RHS is the virtual work</u> $\delta W$, 
and the <u>second term on RHS is the just defined variation of kinetic energy</u> $\delta T$.

Therefore, what we get is actually
$$
\ddtN\left( \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \delta \bm{R}_i \right) = \delta W + \delta T
\tag{6.24}
$$

Integrate the above equation and get the **most general from of Hamilton's principles**:
$$
\int_{t_0}^{t_f} (\delta W + \delta T) \, dt = \left.\left( \sum_{i=1}^{N} m_i \dot{\bm{R}}_i \cdot \delta \bm{R}_i \right)\right|_{t_0}^{t_f} 
\tag{6.25}
$$
^hamiltons-principle-most-general

It holds for the case of 1) arbitrary forces, 2) general constraints, and 3) general initial and final boundary conditions.


If the virtually working forces are conservative, then $\delta W = - \delta V$, and if attention is restricted to fixed endpoint problems, then $\delta\bmR_i(t_0) = \delta\bmR_i(t_f) = 0$, the the above general form specializes to
$$
\int_{t_0}^{t_f} (\delta T - \delta V )\, dt 
= \int_{t_0}^{t_f} \delta(T-V) \, dt 
= \int_{t_0}^{t_f} \delta\calL \, dt 
= \delta \int_{t_0}^{t_f} \calL \, dt 
= 0
\tag{6.26}
$$
Note that the interchangeability of variation operator and integral is generally true, even under holonomic constraints.

Use examples, we will show that Hamilton's principle of varying action can provide a direct path to determine the system motion that does not "pass through" Lagrange's equations. 


## Example 6.5: motion in a constant gravity field

![[fig-5-19_constant_gravity_field.png|300]]

**(Example 5.18) Lagrange's equations**: 

$\calL = \frac{1}{2} m ( \dot{x}^2 + \dot{y}^2 ) - m g y$

$\pp{\calL}{{x}} = 0$, $\pp{\calL}{{y}}=-mg$

$\pp{\calL}{\dot{x}} = m \dot{x}$, $\pp{\calL}{\dot{y}}=m \dot{y}$

$\ddt \pp{\calL}{\dot{x}} - \pp{\calL}{{x}} = m \ddot{x} = 0$

$\ddt \pp{\calL}{\dot{y}} - \pp{\calL}{{y}} = m \ddot{y} + mg = 0$

So, $\dot{x} = \dot{x}_0 = \text{constant}$, $y=y_0+\dot{y}_0 t - \frac{1}{2} g t^2$.

**Hamilton's principle:** (Let's look at just vertical motion for simplicity.)

$T=\frac{1}{2} m \dot{y}^2$, $V=mgy$

$\delta T = m \dot{y} \delta \dot{y}$, $\delta V = -\delta W=mg\delta y$

$\pp{T}{\dot{y}} = m \dot{y}$

Recall
![[#^hamiltons-principle-most-general]]

Since $\delta y(0) = 0$ and $\delta y(f) = 0$, \
$\int_{t_0}^{t_f} (mg\delta q + m \dot{q} \delta \dot{q}) \, dt = 0$ \
Simplified to: \
$\int_{t_0}^{t_f} (g\delta q + \dot{q} \delta \dot{q}) \, dt = 0$

Since $dt$ is arbitrary, there must be $g\delta y + \dot{y} \delta \dot{y} = 0$

Assume the solution has the form of infinite power series: \
$y(t) = a_0 + a_1 t + a_2 t^2 + a_3 t^3 + \cdots$ \
$\dot{y}(t) = a_1 + 2a_2 t + 3a_3 t^2 + \cdots$

Then the variations are: \
$\delta y(t) = \delta a_0 + \delta a_1 t + \delta a_2 t^2 + \cdots$ \
$\delta \dot{y}(t) = \delta a_1 + 2 \delta a_2 t + 3\delta a_3 t^2 + \cdots$ \
(Notice this is variations of functions, so no $\delta t$ appears.)

Plug in 
$$
\begin{aligned}
\left\{ (2a_2 + g) t + 3 a_3 t^2 + \cdots \right\} &\delta a_0 \\
+ \left\{ \left( a_2 + \frac{g}{2} \right) t^2 + 2 a_3 t^3 + \cdots \right\} &\delta a_1 \\
+ \left\{ \frac{1}{3} (2a_2 + g) t^3 + \frac{3}{2} a_3 t^4 + \cdots \right\} &\delta a_2 \\
+ &\cdots = 0
\end{aligned}
$$

Again since $t$ is arbitrary, all coefficients must vanish, thus
$a_2 = -\frac{1}{2}g$,
and $a_3 = a_4 = \dots = 0$

So, the solution is
$y(t) = a_0 + a_1 t - \frac{1}{2}g t^2$

>[!question] Can $a_0$ and $a_1$ be determined? How?


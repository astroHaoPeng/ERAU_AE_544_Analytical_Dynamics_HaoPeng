---
date created: 2025-02-09T16:24:50-05:00
date modified: 2025-04-02T08:40:34-04:00
---
# AE_544_LecNote06\__Variational_Methods__Ch06
![[README#Disclaimers]]

In this chapter, we begin by developing basic concepts from variational calculus and then turn to the development of the most important results in variational mechanics:
1. A family of variational principles due to Hamilton that hold for the motion of very general systems, including distributed parameter systems.
2. Hamilton’s principal function $\calS \equiv \int_{t_0}^{t_f} \calL \dt$, which has several important properties.
3. Extensions of Lagrange’s equations for the case of distributed parameter systems.


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

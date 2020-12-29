---
 
title: 'Numerical simulation: ode/pde solver and spin-up'
date: '2017-08-31T23:08:00.000-07:00'
author: Chang Liao
tags:
- PDE
- ODE
- Optimization
- CLM
- MODFLOW
modified_time: '2019-07-26T17:52:23.651-07:00'
thumbnail: https://1.bp.blogspot.com/-LD0HEvQu9QQ/WcLj4D5riDI/AAAAAAAAaVs/VW3YM3Nuh9kiFF3Rpg6jzDiedBpbQFGgwCLcBGAs/s72-c/cube.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7020523642961670330
blogger_orig_url: https://changliao.blogspot.com/2017/09/numerical-simulation-001.html
---

For Earth Science model development, I inevitably have to deal with ODE and 
PDE equations. I also have come across some discussion related to this topic, 
i.e., 


[https://www.researchgate.net/post/What_does_one_mean_by_Model_Spin_Up_Time](https://www.researchgate.net/post/What_does_one_mean_by_Model_Spin_Up_Time) 

In an attempt to answer this question, as well as redefine the problem I am 
dealing with, I decided to organize some materials to illustrate our current 
state on this topic. 

Models are essentially equations. In Earth Science, these equations are 
usually ODE or PDE. So I want to discuss this from a mathematical perspective. 

Ideally, we want to solve these ODE/PDE with initial condition (IC) and 
boundary condition (BC) using various numerical methods. 

[https://en.wikipedia.org/wiki/Initial_value_problem](https://en.wikipedia.org/wiki/Initial_value_problem) 

[https://en.wikipedia.org/wiki/Boundary_value_problem](https://en.wikipedia.org/wiki/Boundary_value_problem) 

Because of the nature of geology, everything is similar to its neighbors. So 
we can construct a system of equations which may have multiple equation for 
each single grid cell. Now we have an array of equations with the same number 
of knowns and unknowns. We can solve them simultaneously using numerical 
methods. In this case, we are not using “spin-up” at all. In fact, lots of 
models do not use spin-up to reach steady state, e.g., three-dimensional 
groundwater model MODFLOW. 

For example, let's imagine a single cube and corresponding model in space as 
below: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="419" data-original-width="538" height="311" 
src="https://1.bp.blogspot.com/-LD0HEvQu9QQ/WcLj4D5riDI/AAAAAAAAaVs/VW3YM3Nuh9kiFF3Rpg6jzDiedBpbQFGgwCLcBGAs/s400/cube.png" 
width="400" 
/>](https://1.bp.blogspot.com/-LD0HEvQu9QQ/WcLj4D5riDI/AAAAAAAAaVs/VW3YM3Nuh9kiFF3Rpg6jzDiedBpbQFGgwCLcBGAs/s1600/cube.png)<div 
class="separator" style="clear: both; text-align: center;">Figure 1<div 
class="separator" style="clear: both; text-align: center;">\begin{equation} 
\frac{ \partial Q }{ \partial t } = f(Q) + f(w) + ... + Source - Sink 
\end{equation} 
where $Q$ is unknown system state variable, i.e., storage; 
$f(Q)$ is storage related process; 
$f(w)$ is other processes; 
$Source$ is source; 
and $Sink$ is sink. 

In most cases, the $f(Q)$ depends on local gradient, which means that: 
\begin{equation} 
f(Q) = f(Q_{i,j}, Q_{i-1,j}, ...) 
\end{equation} 

With certain boundary condition (BC), we can write an array of equations: 

\begin{equation} \label{equ:matrix} 
\begin{bmatrix} 
      \frac{ \partial Q_{0,0} }{ \partial t }  \\[0.3em] 
      \frac{ \partial Q_{1,0} }{ \partial t }  \\[0.3em] 
      \frac{ \partial Q_{2,0} }{ \partial t }  \\[0.3em] 
      \frac{ \partial Q_{i,j} }{ \partial t } 
     \end{bmatrix} = 
     \begin{bmatrix} 
       f(Q_{0,0}) + f(w_{0,0}) + ... + Source_{0,0} - Sink_{0,0} \\[0.3em] 
       f(Q_{1,0}) + f(w_{1,0}) + ... + Source_{1,0} - Sink_{1,0} \\[0.3em] 
       f(Q_{2,0}) + f(w_{2,0}) + ... + Source_{2,0} - Sink_{2,0} \\[0.3em] 
       f(Q_{i,j}) + f(w_{i,j}) + ... + Source_{i,j} - Sink_{i,j} 
     \end{bmatrix} 
\end{equation} 

In some simple scenarios, we can solve the equations above directly. For 
example, when $Q_{i,j}$ is the only unknown, the total unknowns and number of 
equations are the same. In this case, we might be able to solve the equations 
using a direct solver ([MUMPS](http://mumps.enseeiht.fr/), etc.). 

However, as our models grow more complicated, e.g., CESM. Our ODE and PDE are 
getting more complex when all the terms on the right hand side are more 
complicated. Existing direct solver methods may not suit for the equation 
solving any more. So instead of solving the equation directly, we can solve 
the equation using iterations ([PETSc](https://www.mcs.anl.gov/petsc/), etc.). 

However, even for iterative solver, it can take a long computing time to find 
a "solution". So we have another "solution", we can let the system to evolve 
through time naturally. And this process is often called “spin-up”. In this 
scenario, we can use spin-up to approximate $Q_{i,j}$ with initial condition 
(IC). 

Regardless of the initial condition, the system will gradually converge to 
"steady state". For example, regardless how much water is stored in the tank 
initially, the water will reach the same level after certain time when inflow 
equals outflow. 

<div class="separator" style="clear: both; text-align: center;"><div 
class="separator" style="clear: both; text-align: center;">[<img border="0" 
data-original-height="675" data-original-width="909" height="473" 
src="https://3.bp.blogspot.com/-IbUTnNR3Hgs/WcLsWusrmhI/AAAAAAAAaV8/JzpLsayRQJsFUyVoue0H_S8Y9W2Tkqz-gCLcBGAs/s640/water_tank.png" 
width="640" 
/>](https://3.bp.blogspot.com/-IbUTnNR3Hgs/WcLsWusrmhI/AAAAAAAAaV8/JzpLsayRQJsFUyVoue0H_S8Y9W2Tkqz-gCLcBGAs/s1600/water_tank.png)<div 
class="separator" style="clear: both; text-align: center;">Figure 2<div 
class="separator" style="clear: both; text-align: left;">You can easily setup 
much complicated scenarios similar to:<div class="separator" style="clear: 
both; text-align: center;">[<img border="0" data-original-height="626" 
data-original-width="847" height="472" 
src="https://2.bp.blogspot.com/-EPum9_A_0zM/WxhyrKs4eqI/AAAAAAAAh1o/BCAms_xJ6TgbVlCBqucZ_RELs_RJuRjAQCLcBGAs/s640/ode-pde.png" 
width="640" 
/>](https://2.bp.blogspot.com/-EPum9_A_0zM/WxhyrKs4eqI/AAAAAAAAh1o/BCAms_xJ6TgbVlCBqucZ_RELs_RJuRjAQCLcBGAs/s1600/ode-pde.png)<div 
class="separator" style="clear: both; text-align: center;">Figure 3<div 
class="separator" style="clear: both; text-align: left;">When you have 
multiple pools and flux terms, the system may become very sensitive to certain 
parameters.<div class="separator" style="clear: both; text-align: 
center;">[<img border="0" data-original-height="757" data-original-width="955" 
height="505" 
src="https://1.bp.blogspot.com/-Cq5r5vQlwOE/XTufsDhPxBI/AAAAAAAA2RA/jfeBeH1JnkEM1QcaYuYOAxeKIn5d23nCwCEwYBhgL/s640/ode_good.gif" 
width="640" 
/>](https://1.bp.blogspot.com/-Cq5r5vQlwOE/XTufsDhPxBI/AAAAAAAA2RA/jfeBeH1JnkEM1QcaYuYOAxeKIn5d23nCwCEwYBhgL/s1600/ode_good.gif)<div 
class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: center;"><div 
class="separator" style="clear: both; text-align: left;">Figure 4. 
Illustration of ODE with 8 buckets. Each bucket is contributing water into 
other buckets at different rates. Each bucket has different storage capacity 
and radius.<div class="separator" style="clear: both; text-align: left;"> 

Besides, if you take a close look at most numerical methods, they usually use 
iteration/time step to reach solution. Therefore, they are actually very 
similar to spin-up but with different time steps. 

The criteria which is used to determine whether the system is in "steady 
state" is also critical. More often we expect a state variable does not change 
significantly with time, then we say this system is in "steady state". 
However, any threshold has a limit, needless to say that seldom a system is in 
absolute steady state. 

Because of the complexity of the system, a spin-up can be trapped inside a 
local valley/hilltop similar to: 


<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="296" data-original-width="366" height="322" 
src="https://4.bp.blogspot.com/-TvaaRJ9_kWE/WcLiqDZordI/AAAAAAAAaVg/FMV60jjPwiAIil4oyidb4_5lm6GQ-_GrgCLcBGAs/s400/global.png" 
width="400" 
/>](https://4.bp.blogspot.com/-TvaaRJ9_kWE/WcLiqDZordI/AAAAAAAAaVg/FMV60jjPwiAIil4oyidb4_5lm6GQ-_GrgCLcBGAs/s1600/global.png) 
In this case, our "criteria" must be carefully defined, but that is out of the 
scope of this discussion. 

Getting back the equation, even though we may list as many as equations in the 
matrix, there are no more than 27 equations associated with each cube in a 3D 
space because there are only 26 neighbors for each cube. As a result, after we 
estimated the system state variable using spin-up, we no longer need to solve 
a matrix of equations anymore and we can directly calculate all terms just 
like spin-up process. 

So here comes the question: when do we still need numerical methods to solve 
ODE/PDE equations? 

I believe a side by side comparison will make it easier to understand the 
fundamental idea behind different approaches. 

Let's start with the classical heat equation: 


[https://en.wikipedia.org/wiki/Heat_equation](https://en.wikipedia.org/wiki/Heat_equation) 

There is also a very nice program online to demonstrate the equation: 

[http://people.sc.fsu.edu/~jburkardt/cpp_src/fd1d_heat_explicit/fd1d_heat_explicit.html](http://people.sc.fsu.edu/~jburkardt/cpp_src/fd1d_heat_explicit/fd1d_heat_explicit.html) 
If you compare the formula with above discussion, then we should realize that 
this method is very similar to "spin-up". 

But as the title implies, this is an explicit method, specifically, an 
explicit finite difference method, which is widely used in numerical 
simulation. 


[https://en.wikipedia.org/wiki/Finite_difference_method](https://en.wikipedia.org/wiki/Finite_difference_method) 

"In mathematics, finite-difference methods (FDM) are numerical methods for 
solving differential equations by approximating them with difference 
equations, in which finite differences approximate the derivatives. FDMs are 
thus discretization methods. Today, FDMs are the dominant approach to 
numerical solutions of partial differential equations" 

However, how we approximate the derivatives determines the accuracy of the 
method and explicit apparently has least accuracy compared with implicit and 
other methods. 

In general, "the implicit scheme is always numerically stable and convergent 
but usually more numerically intensive than the explicit method as it requires 
solving a system of numerical equations on each time step.", that is why we 
seldom use implicit methods on large modeling system such as CESM. 

To summarize, "spin-up" is an explicit Euler forward finite difference method 
and most linear/nonlinear matrix solvers are implicit finite difference 
methods. 
You can find the advantage and disadvantage of both methods easily. 
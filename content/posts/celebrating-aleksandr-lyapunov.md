---
title: "Celebrating Aleksandr Lyapunov"
date: 2021-06-06T16:04:16-05:00
draft: true
tags:
  - Manim
  - dynamical systems
---

| {{< rawhtml >}} <video controls width="80%"><source src="/Lyapunov.mp4"></video> {{< /rawhtml >}} |
|:--:|
| Happy 164th birthday, Aleksandr Lyapunov! |

I recently participated in the first annual [Manim](https://www.manim.community/) math animation engine hackathon! The theme was aniversaries, so I created the above animation to celebrate the 164t anniversary of mathematician Aleksandr Lyapunov's birth. This extended some ideas I presented from [Steven Strogatz's nonlinear dynamics textbook](http://www.stevenstrogatz.com/books/nonlinear-dynamics-and-chaos-with-applications-to-physics-biology-chemistry-and-engineering) at the University of Minnesota's [math directed reading program](https://www-users.math.umn.edu/~mahrud/drp/) symposium.

# The math

Consider the system

<div class='math'>
$$
\begin{align}
	\frac{dx}{dt} &= y-x^3 \\\\\\\\
	\frac{dy}{dt} &= -x-y^3.
\end{align}
$$
</div>

$$
\begin{aligned}
	a=&b+c \newline
	=&e+f
\end{aligned}
$$

$$
foo \newline
bar
$$

| ![Our dynamical system](/DSImage.png) |
|:--:|
| Our dynamical system |

We can't use linearization about the fixed point at the origin to determine its stability; the Jacobian has pure imaginary eigenvalues, so the linearization is not robust to small nonlinear terms.

However, Lyapunov showed that finding a Lyapunov function \\(V\\) which is locally positive definite and has a locally negative definite time derivative implies stability. This is simimlar to an energy function as the trajectories move monotonically down the basis of \\(V\\). Let's try \\(V = x^2 + y^2\\) for the system.

| ![The chosen Lyapunov function](/ParabImage.png) |
|:--:|
| The chosen Lyapunov function |

$$\begin{align*}
	\frac{dV}{dt} &= \frac{dV}{dx} \frac{dx}{dt} + \frac{dV}{dy} \frac{dy}{dt} \\
	&= 2x(y-x^3) + 2y(-x-y^3) \\
	&= 2xy -2x^4 - 2yx -2y^4 \\
	&= -2x^4 - 2y^4
\end{align*}$$

$V$ is nonnegative and $\frac{dV}{dt}$ is nonpositive, so it truly is a Lyapunov function. Its existence implies that the system is aysmptototically stable; trajectories all eventually converge to the origin. 

Outside of this toy example, Lyapunov functions are used in the engineering of nonlinear control systems.

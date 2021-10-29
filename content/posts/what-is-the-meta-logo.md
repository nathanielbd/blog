---
title: "What is the Meta logo?"
date: 2021-10-28T17:33:48-06:00
images:
tags: 
  - parametric equations
---

Today, the Facebook company rebranded itself as Meta. PR aside, what mathematically describes its new Lemniscate-like loop logo (try saying that quickly three times)?

| ![](https://photos5.appleinsider.com/gallery/45329-88208-Meta-Logo-xl.jpg) |
|:--:|
| The logo in question |

The icon is a [Bowditch curve](https://en.wikipedia.org/wiki/Lissajous_curve) (also called a Lissajous curve), part of a family of parametric equations where the \\(x\\) and \\(y\\) coordinates are sinusoids.

$$
x = A\sin(at + \delta), \quad y = B\sin(bt).
$$

| {{< rawhtml >}} <iframe src="https://www.desmos.com/calculator/zun1gs45wi" width="100%" style="min-height:300px"></iframe> {{< /rawhtml >}} |
|:--:|
| Here is the equation for the logo (\\(A=3, a=1, \\delta=5\\pi/9, B=2, b=2\\)). Try tweaking the parameters and see how it changes! |

After tweaking around or refreshing your high school algebra knowledge, you can find that \\(A\\) and \\(B\\) control the width and height of the curve. The ratio of \\(\\frac{a}{b}\\) determines the number of lobes in the figure. Lastly, \\(\\delta\\) is called the 'phase difference.' If we consider the Bowditch curve to be image of a three-dimensional wireframe, then \\(\\delta\\) controls the angle at which we view it.

| {{< rawhtml >}} <video controls width="80%"><source src="/Bowditch3D.mp4"></video> {{< /rawhtml >}} |
|:--:|
| Interpretation of \\(\\delta\\) being the angle at which we view a 3D wireframe. Ignoring that closer parts of the wireframe appear larger, this is precisely our original curve in 2D. |

The wireframe has the parameters

$$
x = A\cos(t), \quad y = A\sin(t), \quad z=B\sin\left(\frac{b}{a}t\right).
$$

A good mathematical exercise would be to show that the projection of this onto a plane through the \\(z\\)-axis indeed results in the original Bowditch curve! Given that the company has the augmented reality 'metaverse' in mind, they certainly chose Bowditch curves as a figure that lives simultaneously in [two and three dimensions](https://design.facebook.com/stories/designing-our-new-company-brand-meta/).
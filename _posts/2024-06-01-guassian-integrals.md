---
layout: post
title: Gaussian Integrals
subtitle: Note to self
tags: [Math]
comments: true
mathjax: true
full-width: true
author: Sérgio Carrôlo
---

This is a note I always keep with me because there are not many integrals that I can do besides Gaussian Integrals, so might as well know how to do them to their full extent. Nothing that I am writing here is either new/ground breaking/surprising, it's just a compilation of ideas about Gaussian integrals that I find useful every once in a while, and that I had fun deriving.

## 1 dimension

Let's warm-up by deriving the usual 1-dimensional gaussian integral, 
\begin{equation}
  I_1(a) = \int_{-\infty}^\infty  e^{-ax^2} dx \, , 
\end{equation}
by instead calculating a, much harder, 2-dimensional version, 
\begin{equation}
  I_1(a)^2 = \int_{-\infty}^\infty \int_{-\infty}^\infty e^{-a (x^2 + y^2)} dx dy = \int_0^\infty \int_0^{2 \pi} e^{-a r^2} r d\theta dr = 2\pi \int_0^\infty \frac{d}{dr} \left(\frac{e^{-ar^2}}{2a}\right) dr = \frac{\pi}{a} \, .
\end{equation}

Thus, we now know

\begin{equation}
	I_1 = \sqrt{\frac{\pi}{a}}
\end{equation}

## Still 1D but even more tedious

Take a gaussian-like with a general quadratic exponent,

$$\begin{equation}
	I_1(a,b,c) = \int_{-\infty}^{\infty} e^{-(ax^2+bx+c)}  dx\, .
\end{equation}$$

The trick here is what people call "complete the square". This is just because that's basically the only integral I know how to do, therefore I want to turn this awful one into a friendly one.

Completing the square means

$$\begin{equation}
	ax^2 + bx +c = a\left( x^2 + \frac{b}{a}x\right) + c = a\left( x + \frac{b}{2a}\right)^2 - \frac{ b^2}{4a} + c \, ,
\end{equation}$$

which implies

$$\begin{equation}
	I_ 1(a,b,c) = \int_ {-\infty}^{\infty} e^{-(ax^2+bx+c)} dx = e^{\frac{ b^2}{4a} - c}\int_ {-\infty}^{\infty} e^{-a\left( x + \frac{b}{2a}\right)^2} dx = e^{\frac{ b^2}{4a} - c} \sqrt{\frac{\pi}{a}}
\end{equation}$$

In the last equality, we used the fact that shifting $\pm \infty$ by $-\frac{b}{2a}$ is still $\pm \infty$.


## n dimensional Gaussian integrals


A natural generalization of the 1D gaussian integral above to n dimensions is 

$$\begin{equation}
	I_ n(A_ {ij}) = \int_ {-\infty}^\infty e^{- x_ i A_ {ij}x_ j} d^n x \, , 
\end{equation}$$

where $A$ is a $n\times n$ matrix. Calculating this one just amounts to reducing it to a bunch (actually n) of separated gaussian integrals - because this is the only one we know how to do. 



$$\begin{equation}
	A_{ij} x_i x_j = \frac{1}{2}( \underbrace{A_{ij} + A_{ji}}_ { 2 A_{(ij)} } + \underbrace{A_{ij} - A_{ji}}_ {2A_{ [ij] }})x_i x_j = A_{(ij)}x_i x_j + 0 \, ,
\end{equation}$$

then, if $A_ {(ij)}$ is non-singular, then it is diagonalizable using orthogonal matrices, which means 

$$\begin{equation}
	\delta_ {ij}\lambda_ i = (U^T)_ {ik} A_ {(kl)} U_ {lj} \, ,
\end{equation}$$

where $U$ is such that $U^T U = \mathbb{1}$. Note that, on the LHS, there is no sum implied over repeated indices, while on the RHS there is a sum over $k$ and $l$. Plugging this back into the equation above we get

$$\begin{equation}
	A_{(ij)}x_i x_j = x_i U_{ik} \delta_{kl} \underbrace{(U^T)_ {lj} x_ j}_ {y_l} \lambda_ {k} = y_ k^2 \lambda_ k \, ,
\end{equation}$$

which is the desired gaussian exponent. Now, just recall that doing a linear change of variables in a multiple integral introduces a determinant factor of the matrix that does the transformation,

$$\begin{align}
	I_n(A_{ij}) &= \int_{\mathbb{R}^n} e^{- x_iA_{ij}x_j} d^nx = \int_{\mathbb{R}^n}e^{- y_i^2 \lambda_i} \left|\frac{1}{\det(U)}\right|d^ny \\
	&\text{Use} \quad U^TU = \mathbb{1} \Rightarrow (\det{U})^1 = 1 \Rightarrow |\det{U}| = 1 \\
	&= \int_{\mathbb{R}^n} \prod_{i=1}^n (e^{- y_i^2 \lambda_i}dy_i) = \prod_{i=1}^n\sqrt{\frac{\pi}{\lambda_i}} = \sqrt{\frac{\pi^n}{\det(A_{(ij)})}}
\end{align}$$


## Completing squares is still boring

The most general Gaussian-like integral in n dimensions is given by

$$\begin{equation}
	I_n(A,b,c)	= \int_{\mathbb{R}^n}e^{-(x^TAx + b^Tx+c)} d^nx \, ,
\end{equation}$$

where now we assume that $A$ is symmetric, if not, just take the symmetric part of the matrix you have.
To compute this awful integral, complete the square to turn it into a beautiful n-dimensional gaussian integral, 

$$\begin{align}
	x^T A x +  x^T b + c &= x^T A(x + A^{-1}b) +c = (x+ A^{-1}b)^T A\underbrace{(x + A^{-1}b)}_ {y} - b^T \underbrace{(A^{-1})^T}_{A^T = A} A A^{-1}b +c \\
 &= y^T A y - b^T A^{-1} b +c
\end{align}$$

with this change of variables, the integral reduces to

$$\begin{equation}
	I_n(A,b,c) = e^{- b^T A^{-1} b +c}\int_{\mathbb{R}^n}e^{-y^TAy} d^ny = e^{- b^T A^{-1} b +c} \sqrt{\frac{\pi^n}{\det(A)}}
\end{equation}$$


This result is different from wikipedia's result, because they like the $1/2$ factor in front of $A$, and I am not a huge fan, so if you prefer the $1/2$ put a $2^{n/2}$ in front of the above expression to agree with [wikipedia](https://en.wikipedia.org/wiki/Gaussian_integral)





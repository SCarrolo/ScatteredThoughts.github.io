---
layout: post
title: Gaussian Integrals
subtitle: Note to self
tags: [Math]
comments: true
mathjax: true
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

### Still 1D but even more tedious

Sometimes, we (and by we I mean "I") are not smart enough while parameterising the problem, and end up with a unfriendlier gaussian-cousin,

\begin{equation}
	I_1(a,b,c) = \int_{-\infty}^{\infty} e^{s}
\end{equation}

Here's a table:

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |

You can use [MathJax](https://www.mathjax.org/) to write LaTeX expressions. For example:
When \\(a \ne 0\\), there are two solutions to \\(ax^2 + bx + c = 0\\) and they are $$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

How about a yummy crepe?

![Crepe](https://beautifuljekyll.com/assets/img/crepe.jpg)

It can also be centered!

![Crepe](https://beautifuljekyll.com/assets/img/crepe.jpg){: .mx-auto.d-block :}

Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.

## Local URLs in project sites {#local-urls}

When hosting a *project site* on GitHub Pages (for example, `https://USERNAME.github.io/MyProject`), URLs that begin with `/` and refer to local files may not work correctly due to how the root URL (`/`) is interpreted by GitHub Pages. You can read more about it [in the FAQ](https://beautifuljekyll.com/faq/#links-in-project-page). To demonstrate the issue, the following local image will be broken **if your site is a project site:**

![Crepe](/assets/img/crepe.jpg)

If the above image is broken, then you'll need to follow the instructions [in the FAQ](https://beautifuljekyll.com/faq/#links-in-project-page). Here is proof that it can be fixed:

![Crepe]({{ '/assets/img/crepe.jpg' | relative_url }})

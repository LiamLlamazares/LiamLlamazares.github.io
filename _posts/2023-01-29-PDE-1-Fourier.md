---
layout: post
title: The Fourier transform, tempered distributions and Sobolev spaces
subtitle: The holy trinity
thumbnail-img: /assets/img/Taylor1.jpg
share-img: /assets/img/Taylor1.jpg
tags: [PDEs]
author: L.Llamazares-Elias
---

# Three line summary

- The Fourier transform defines a linear isometry on the space of
  square-integrable complex-valued functions and has as inverse the
  inverse Fourier transform. This allows us to write these
  functions as a superposition of harmonic functions.

- Linear differential operators act as a simple polynomial
  multiplication on the frequency domain. Smooth functions have
  Fourier transforms that decay quickly and vice-versa. This
  correspondence also allows us to introduce fractional differential
  operators and pseudo differential operators, such as
  $\sqrt{-\Delta }$.

- The Sobolev spaces $H^s$ and tempered distributions $\mathcal{S}'$
  are complete spaces of functions to which we can extend differential
  operators.

# Introduction

Hi everyone, welcome to the first post in a new series focusing on
partial differential equations (PDEs). In this post, we'll introduce
some of the key analytical tools used to solve them. These tools will
play a prominent role in future posts in this series and in other
series to come. We'll begin by introducing some notation and necessary
preliminaries on integration. Next, we will introduce the Fourier
transform, which is the fundamental object of harmonic analysis and
plays a fundamental role in partial differential equations (PDEs),
probability theory, and number theory. In particular, we will show in
future posts how many linear PDEs, such as the heat equation, can be
solved using it.\
\
After this, we'll discuss the generalization of what it means to solve a
PDE. To do so, we will need to introduce the space of (tempered)
distributions $\mathcal{S}'$ and Sobolev spaces $H^s$. These two spaces
will be crucial in allowing us to extend the concept of solution to
PDE to these spaces and use their completeness to prove the
existence, uniqueness, and regularity of solutions.\
\
Much of the material here contained can be found in my [undergraduate
thesis](https://gredos.usal.es/bitstream/handle/10366/145629/TFG%20LIAM%20LLAMAZARES.pdf?sequence=1) on the Navier Stokes equations, which in turn are based on
[Terence Tao's excellent notes](https://terrytao.wordpress.com/2018/09/16/254a-notes-1-local-well-posedness-of-the-navier-stokes-equations/).

## Notation

We write $L^p(\mathbb{R}^d)$ and $L^p(\mathbb{R}^d\to\mathbb{C}^m)$ to
denote the space of equivalence classes of $p$ integrable functions from
$\mathbb{R}^d$ to $\mathbb{R}$ and $\mathbb{C}^m$ respectively. Given
a function defined on a factor space $u: X\times Y\rightarrow Z$, we shall
use $u(x)$ to stand for the slightly more cumbersome
$u(x,\cdot ): Y\rightarrow Z$. Given
$\alpha=(\alpha\U 1,...,\alpha\U d)\in\mathbb{N}^d$ we shall write as is
standard

<div>
 $$x^\alpha:=x^{\alpha\U 1}\cdots  x^{\alpha\U d};\quad D^\alpha:=\partial\U 1^{\alpha\U 1}\cdots\partial\U 1^{\alpha\U d}$$
</div>

and whenever the expression $D^\alpha$ appears we will assume implicitly
that $\alpha\in\mathbb{N}^d$. Given $x\in\mathbb{R}^d$ we will write
$\abs{x}$ to denote its norm and the Japanese bracket
$\left\langle x\right\rangle$ will signify

<div>
 $$\left\langle x\right\rangle:=(1+\abs{x}^2)^{1/2}.$$
</div>

Finally, we will employ the notation $f\lesssim g$ to mean that there
exists some constant $C$ such that $f\leq Cg$. If the value of $C$
depends on some other parameter such as the dimension $d$, we shall make
this explicit by writing $f\lesssim\U d g$.

## Some useful results on integration

In PDEs, it is essential to be able to commute limits and differentials
with both summation and integration. The main way of doing this is the
[dominated](https://en.wikipedia.org/wiki/Dominated_convergence_theorem) and [monotone convergence theorem](https://en.wikipedia.org/wiki/Monotone_convergence_theorem) together with the
following two propositions which we state in full generality for
functions valued in a Banach space $E$. Though for now, we will only
need the case $E=\mathbb{R}$. On first reading, this can be assumed for
commodity.

 <a name="cont">
**Proposition 1 (Continuity of the integral)**</a>. Let $(X,\mu )$ be a
measure space, $T$ a first countable metric space, $(E,\norm{})$ a
Banach space and

<div>
 $$f:T\times X\to E$$
</div>

such that $f(t)$ is
([Bochner](https://nowheredifferentiable.com/2022-05-27-The-Bochner-integral/)) integrable for all ${t}\in{T}$ and such that

<div>
 $$\norm{f(t)}\leq g\in L^1(X)\quad \forall{t}\in {T}.$$
</div>

Then given
$t\U 0\in T$ we have that

<div>
 $$\lim\U {t\to t\U 0}\int\U X f(t,x)\mu(dx) =\int\U X\lim\U {t\to t\U 0}f(t,x)\mu(dx) .$$
</div>

In consequence, if $f(x)$ is continuous, so is $\int\U X f(t,x) \mu(dx)$.

**Proof.** The proof is an application of the dominated convergence
theorem to the sequence of functions $f\U n:=f(t\U n)$ where
$t_n$ is some sequence converging to $t$ and the fact
that, in first countable spaces, sequential continuity is
equivalent to continuity. ◻

 <a name="diff">
 **Proposition 2 (Differentiation under the integral sign)**</a>. Let $X$ be
a measure space, $U$ be a convex open interval of $\mathbb{R}$, and $E$
a Banach space. Consider

<div>
 $$f:U\times X\to E$$
</div>

such that:

- $f(t)$ is measurable for every $t\in U$ and integrable for some
  $t\U 0\in U$.

- For each $x\in X$ we have that $f(x)$ is differentiable and there
  exists an integrable function $g: X\to\mathbb{R}$ such that

<div>
 $$\norm{\partial\U {t}{f}(t,x)}\leq g(x)\quad \forall{(t,x)}\in {U\times E}.$$
</div>
Then, it holds that
<div>
 $$\partial\U {t}{\int\U X f(t)\mu(dx)}=\int\U X \partial\U {t}f(t) \mu(dx).$$
</div>

**Proof.** First, we show that the integral on the left-hand side of the
equation above makes sense. Let $t\in U$ be any, then by the mean value
inequality, we have that

<div>
 $$\frac{f(t)-f(t\U 0)}{t-t\U 0}\leq \sup\U {s \in U}\norm{\partial \U t f(s)}\leq g \in L^1(X).$$
</div>

Thus, we may apply the previous proposition to commute the limit with
the integral

<div>
 $$\begin{gathered}
        \lim\U {t \to t\U 0}\frac{\int\U {X} f(t)\mu (dx)-\int\U {X}f(t\U 0) \mu (dx)}{t-t\U 0}  =\lim\U {t \to t\U 0}\int\U {X}    \frac{f(t)-f(t\U 0)}{t-t\U 0} \mu (dx) \\=\int\U {X}\lim\U {t \to t\U 0} \frac{f(t)-f(t\U 0)}{t-t\U 0} \mu (dx) =\int\U {X}\partial \U t f(t) \mu(dx),
    \end{gathered}$$
</div>

where in the first equality, we also used the
[linearity of the Bochner integral](https://nowheredifferentiable.com/2022-05-27-The-Bochner-integral/#:~:text=The%20typical%20properties) and in the last equality we
used that by hypothesis $f(x)$ is everywhere differentiable. This
concludes the proof. ◻

In the literature, the usual hypothesis is that $\partial \U t f$ is
integrable everywhere (see, for example [1](https://books.google.co.uk/books/about/Integraci%C3%B3n_de_funciones_de_varias_vari.html?id=uuHbOgAACAAJ&redir_esc=y) page 108), however as we
have seen it is sufficient to require the integrability at a point. Finally, we end this section with a lemma that will be useful for the convergence of certain integrals and series.

 <a name="lemma 0">
 **Lemma 0.**</a> Let $s\in \mathbb{N}$ then
$$
\int_{\mathbb{R}^d}\langle{x}\rangle^{-s}dx<\infty\iff s>d\iff\sum_{k\in\Z^d}\langle{k}\rangle^{-s}<\infty
$$

**Proof.** The equivalence of these two statements is a consequence of the fact that $\langle{x}\rangle^{-s}$ is monotone decreasing. To prove the first part of the proposition, it is sufficient to apply a change to spherical coordinates. ◻

# The Fourier transform on $\mathbb{R}^d$

These preliminaries out of the way, we now get to our first main
section. We assume the reader has encountered the Fourier transform
before and limit ourselves to giving a rundown of the theory and main
ideas, taking the reader through a basic definition to an extension of
it. To make the Fourier transform an isometry, we will use the following
convention.

**Definition 1**. Given $f\in L^1(\mathbb{R}^d\to\mathbb{C}^m)$ the
Fourier transform of $f$ and the inverse Fourier transform of $f$
are defined respectively by

<div>
 $$\hat{f}(\xi):=\int\U {\mathbb{R}^d}f(x)e^{-2\pi i\xi\cdot  x} dx, \quad \check{f}(\xi):=\int\U {\mathbb{R}^d}f(x)e^{2\pi i\xi\cdot  x} dx$$
</div>

Other exponents such as $e^{-ix}, e^{-\pi i x}$ can also be used with
identical results modulo constants. Let us introduce the notation

<div>
 $$\mathcal{F}\U 1 f:=\hat{f}, \mathcal{F}\U 1 ^{-1} f:=\check{f}$$
</div>

for the Fourier transform
(on $L^1$) and its inverse. The following proposition holds.

 <a name="prop 3">
 **Proposition 3 ( Properties of $\mathcal{F}\U 1$)**</a>. Given
$f\in L^1(\mathbb{R}^d\to\mathbb{C}^m)$
<ol>
<li>The Fourier transform $\mathcal{F}\U 1$ is a continuous linear
    operators

<div>
 $$\mathcal{F}\U 1:L^1(\mathbb{R}^d\to\mathbb{C}^m) \to L^\infty(\mathbb{R}^d\to\mathbb{C}^m)$$
</div>
</li>

.

<li>If $x^\alpha f(x)\in L^1(\mathbb{R}^d\to\mathbb{C}^m)$
then:

<div>
 $$D^\alpha \hat{f}(\xi)=(-2\pi i)^{\abs{\alpha}}\widehat{x^{\alpha} f}(\xi)\qquad\forall \xi\in\mathbb{R}^d.$$
</div>
</li>
<li> If $f$ is absolutely continuous in $x\U j$ for almost every
    $x\U 1,...x\U {j-1},x\U {j+1},...,x\U d$ then then

<div>
 $$\widehat{\partial x\U j f}(\xi)=2\pi i\xi\U j\widehat{ f}(\xi)\qquad\forall \xi\in\mathbb{R}^d.$$
</div>
</li>

**Proof.** The proof of the first point is an application of the triangle
inequality as

<div>
 $$\abs{\hat{f}(\xi )}=\abs{\int\U {\mathbb{R}^d}f(x)e^{2\pi i x\cdot \xi } dx}\leq\int\U {\mathbb{R}^d}\abs{f(x)}dx\quad\forall \xi \in \mathbb{R}^d,$$
</div>
</ol>

and similarly for the inverse. The second point follows by
[differentiation under the integral](#diff). The third point can be proved
by using integration by parts and the observation that every absolutely
continuous function must go to zero at infinity. ◻

We note that the analogous holds for the inverse Fourier transform where
it is only necessary to remove the minus sign in $2$ and a change of the
sign in $3$. The proof can be completed in an identical fashion or by
noting that $\check{f}(\xi )=\hat{f}(-\xi )$. The importance of these
last two properties is that they give us information on the Fourier
transform of a function $f$ based on its regularity and decay. They can
be stated informally as decay gives regularity and regularity gives
decay (as the Fourier transform of any
$f\in L^1(\mathbb{R}^d\to\mathbb{R}^d)$ decays to 0 at infinity by the
[Riemann-Lebesgue lemma](https://en.wikipedia.org/wiki/Riemann%E2%80%93Lebesgue_lemma). In general, the Fourier transform of an
integrable function is not itself integrable. That is,
$L^1(\mathbb{R}^d\to\mathbb{C}^m)$ is not closed under the Fourier
transform. We now introduce a space that is closed under the Fourier
transform, the Schwartz space, which can be thought of as the space of
infinitely regular functions with infinite decay:

**Definition 2**. The Schwartz space
$\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)$ is:

<div>
 $$\begin{align}
    \label{formula}
    \mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m):=\lbrace f\in\mathbb{C}^\infty(\mathbb{R}^d\to\mathbb{C}^m):x^\alpha D^\beta f\in L^\infty(\mathbb{R}^d\to\mathbb{C}^m)\quad\forall\hspace{2pt}\alpha,\beta\in \mathbb{N}^d\rbrace.\end{align}$$
</div>

By applying [Proposition $1$](#cont) we deduce that, given
$f\in\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)$

<div>
 $$\begin{aligned}
\label{rdft}
    \xi^\alpha D^\beta \hat{f}(\xi)   & =(-2\pi i)^{\abs{\beta}}\xi^{\alpha}\widehat{x^{\beta}f}=\frac{(-2\pi i)^{\abs{\beta}}}{(2\pi i)^{\abs{\alpha}}}\widehat{D^{\alpha}x^{\beta}f}\in L^\infty(\mathbb{R}^d\to\mathbb{C}^m) \\
    \xi^\alpha D^\beta \check{f}(\xi) & =\frac{(2\pi i)^{\abs{\beta}}}{(-2\pi i)^{\abs{\alpha}}}\widehat{D^{\alpha}x^{\beta}f}\in L^\infty(\mathbb{R}^d\to\mathbb{C}^m).\end{aligned}$$
</div>

Hence, the Fourier transform and the inverse Fourier transform restrict
to endomorphisms of the Schwartz space, which we will denote respectively
by

<div>
 $$\mathcal{F}\U \mathcal{S},\mathcal{F}^{-1}\U \mathcal{S}:\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)\to\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m).$$
</div>

The next item on the agenda is Plancherel's theorem, which is proven via
the following lemma, in which we shall use the
notation

<div>
 $$\left\langle f,g\right\rangle\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}:=\int\U {\mathbb{R}^d}f(x)\cdot  \overline{g(x)} dx$$
</div>

for the inner product on $L^2(\mathbb{R}^d\to\mathbb{C}^m)$.

 <a name="planch">
 **Lemma 1** (Plancherel for Schwartz functions)</a>. Given
$f,g\in \mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)$

(i) $\left\langle\mathcal{F}\U \mathcal{S}f,g\right\rangle\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}=\left\langle f,\mathcal{F}\U \mathcal{S}^{-1}g\right\rangle\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)};\quad\left\langle\mathcal{F}\U \mathcal{S}^{-1}f,g\right\rangle\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}=\left\langle f,\mathcal{F}\U \mathcal{S}g\right\rangle\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}$

(ii) $\mathcal{F}\U \mathcal{S}^{-1} \mathcal{F}\U \mathcal{S}f=\mathcal{F}\U \mathcal{S}\mathcal{F}\U \mathcal{S}^{-1}  f=f$

A direct application of Fubini can prove the first point. The
second point is trickier and is the crux of why we call $\mathcal{F}^{-1}$
the inverse Fourier transform. The proof can be found in [2](https://link.springer.com/book/10.1007/978-1-4419-7055-8) pages
222-226. From $(i)$ and $(ii)$ we deduce immediately that, given a
Schwartz function $f$,

<div>
 $$\label{Plancherel}
    \norm{f}\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}=\norm{\mathcal{F}\U \mathcal{S}f}\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}=\norm{\mathcal{F}\U \mathcal{S}^{-1}f}\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}$$
</div>

That is, the restrictions of $\mathcal{F}\U 1$ and $\mathcal{F}^{-1}\U 1$

<div>
 $$\mathcal{F}\U \mathcal{S},\mathcal{F}\U \mathcal{S}^{-1}:\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)\to\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m),$$
</div>

are linear unitary operators (we say an operator $T$ is unitary if $\| T\| =1$), which are the inverse of one to the other.
We obtain the following result.

 <a name="plancherel theorem">
 **Proposition 4 (Plancherel's theorem)**</a>. $\mathcal{F}\U \mathcal{S}$
and $\mathcal{F}\U \mathcal{S}^{-1}$ may be extended to unitary operators:

<div>
 $$\mathcal{F},\mathcal{F}^{-1}:L^2(\mathbb{R}^d\to\mathbb{C}^m)\to L^2(\mathbb{R}^d\to\mathbb{C}^m)$$
</div>

With $\mathcal{F}\mathcal{F}^{-1}=\mathcal{F}^{-1}\mathcal{F}=Id$.

**Proof.** This is an immediate result of the density of
$\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)$ in the larger
$L^2(\mathbb{R}^d\to\mathbb{C}^m)$ and the completeness of
$L^2(\mathbb{R}^d\to\mathbb{C}^m)$ together with $(ii)$ and [Plancherel for Schwartz functions](#planch). As, by a simple limiting argument, it is easy to see that
continuous extensions of continuous linear operators preserve the norm
and the inverses of the operators in question. ◻

It is reasonable to wonder if this extended Fourier transform
$\mathcal{F}$ coincides with our initial definition when reasonable.
That is, whether given a function
$f \in L^1(\mathbb{R}^d\to\mathbb{C}^m)\cap L^2(\mathbb{R}^d\to\mathbb{C}^m)$
we have that

<div>
 $$\mathcal{F}f(\xi)=\mathcal{F}\U 1f(\xi)=\int\U {\mathbb{R}^d}f(x)e^{-2\pi ix\cdot \xi} dx\qquad\forall \xi\in\mathbb{R}^d.$$
</div>

This indeed holds, as can be seen by taking a sequence of functions
$\lbrace f\U n\rbrace\U {n=1}^\infty\in\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)$
converging to $f$ in $L^1(\mathbb{R}^d\to\mathbb{C}^m)$ and in
$L^2(\mathbb{R}^d\to\mathbb{C}^m)$. As then $\mathcal{F}\U 1 f\U n$
converges uniformly to $\mathcal{F}\U 1f$ by point $1$ of [Proposition 3](#prop 3)
and in $L^2(\mathbb{R}^d\to\mathbb{C}^m)$ to $\mathcal{F}f$ by
[Plancherel](#plancherel theorem), from where we deduce that as desired
$\mathcal{F}\U 1f=\mathcal{F}f$.

# The Fourier transform of periodic functions

We now extend our previous results to $\mathbb{Z}^d$ periodic
functions, though, for any period, analogous results may be achieved. By
identifying $\mathbb{Z}^d$ periodic functions with functions on the
torus $\mathbb{T}^d:=\mathbb{R}^d/\mathbb{Z}^d\equiv [0,1]^d$ we will
work with functions $f:\mathbb{T}^d\to\mathbb{C}^m.$ As we will see
strikingly similar results are achieved in this setting

**Definition 3**. Given $f\in L^1(\mathbb{T}^d\to\mathbb{C}^m)$ we
define the $k$-th Fourier coefficient of $f$ as:

<div>
 $$\hat{f}(k):=\int\U {\mathbb{T}^d}f(x)e^{-2\pi ik\cdot x}dx.$$
</div>

We thus obtain a function $\hat{f}$ on $\mathbb{Z}^d$ which we shall
call the Fourier series of $f$ and a continuous linear function which we
shall denote as in the Euclidean case:

<div>
 $$\mathcal{F}\U 1:L^1(\mathbb{T}^d\to\mathbb{C}^m)\to l^\infty(\mathbb{Z}^d\to\mathbb{C}^m)$$
</div>

where $l^{\infty}(\mathbb{Z}^d\to\mathbb{C}^m)$ is the set of bounded
sequences from $\mathbb{Z}^d$ to $\mathbb{C}^m$. As before, we have the
following result:

 <a name="decay">
**Proposition 5**</a>. Given $f\in L^1(\mathbb{T}^d\to\mathbb{C}^m)$ if
$f$ is absolutely continuous in $x\U j$ for almost every
$x\U 1,...x\U {j-1},x\U {j+1},...,x\U d$ then

<div>
 $$\widehat{\partial\U {x\U j}{f}}(k)=2\pi i k\U j\widehat{f}(k)\qquad\forall k\in\mathbb{Z}^d.$$
</div>

In particular if $f\in C^\infty(\mathbb{T}^d\to\mathbb{C}^m)$ we have
that:

<div>
 $$\label{rgivesdpft}
    \widehat{D^\alpha f}(k)=(2\pi ik)^\alpha\hat{f}(k),$$
</div>

and as a
result we have that $\hat{f}$ is of rapid decrease (i.e. $\hat{f}$
decreases faster than the inverse of any polynomial). We thus have, as
before, an induced map:

<div>
 $$\mathcal{F}\U {C^\infty}:C^\infty(\mathbb{T}^d\to\mathbb{C}^m)\to s(\mathbb{Z}^d\to\mathbb{C}^m)$$
</div>

<div>
 $$f\mapsto \hat{f}$$
</div>

where $s(\mathbb{Z}^d\to\mathbb{C}^m)$ are the
sequences from $\mathbb{Z}^d$ to $\mathbb{C}^m$ that are of rapid
decrease (this space now plays the role of the Schwartz space
$\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)$). Similarly to the
non-periodic case, we now define

<div>
 $$\mathcal{F}^{-1}\U {C^\infty}:s(\mathbb{Z}^d\to\mathbb{C}^m)\to C^\infty(\mathbb{T}^d\to\mathbb{C}^m);\quad a\mapsto\check{a}$$
</div>

with:

<div>
 $$\check{a}(x):=\sum\U {k\in\mathbb{Z}^d}a(k)e^{2\pi ik\cdot x}.$$
</div>

This is indeed smooth as, by the rapid decay of $a$, we may
[differentiate under the integral sign](#diff) (we recall that sums are
just integrals against discrete measures) to commute all derivatives
with the above sum to obtain that

<div>
 $$\label{dgivesrpft}
    D^\alpha \check{a}(x)=\sum\U {k\in\mathbb{Z}^d}(2\pi ik)^\alpha a(k)e^{2\pi ik\cdot x}\quad\forall{a}\in {s(\mathbb{Z}^d\to\mathbb{C}^m)}.$$
</div>

It is now possible to prove, as with the Euclidean case, that

<div>
 $$\mathcal{F}\U {C^\infty}\mathcal{F}^{-1}\U {C^\infty}=\mathcal{F}^{-1}\U {C^\infty}\mathcal{F}\U {C^\infty}=Id,$$
</div>

and that analogously given $f$ smooth, and $a$ of rapid decrease

<div>
 $$\left\langle\mathcal{F}\U {C^\infty} f,a\right\rangle\U {l^2(\mathbb{Z}^d\to\mathbb{C}^m)}=\left\langle f,\mathcal{F}\U {C^\infty}^{-1} a\right\rangle\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)};\quad\left\langle\mathcal{F}\U {C^\infty}^{-1} a,f\right\rangle\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}=\left\langle a,\mathcal{F}f\right\rangle\U {l^2(\mathbb{Z}^d\to\mathbb{C}^m)}.$$
</div>

See, for example, [2](https://link.springer.com/book/10.1007/978-1-4419-7055-8) pages 197-206. We conclude that
$\mathcal{F}\U {C^\infty}$ are unitary linear functions and that hence:

**Proposition 6 (Plancherel's (periodic) theorem)**.
$\mathcal{F}\U {C^\infty}$ and $\mathcal{F}\U {C^\infty}^{-1}$ may be extended
to unitary operators:

<div>
 $$\mathcal{F}:L^2(\mathbb{T}^d\to\mathbb{C}^m)\to l^2(\mathbb{T}^d\to\mathbb{C}^m);\quad \mathcal{F}^:l^2(\mathbb{Z}^d\to\mathbb{C}^m)\to L^2(\mathbb{R}^d\to\mathbb{C}^m)$$
</div>

with $\mathcal{F}\mathcal{F}^{-1}=\mathcal{F}^{-1}\mathcal{F}=Id.$

We note that, as for the Euclidean case, given
$f\in L^2(\mathbb{T}^d\to\mathbb{C}^m)\cap L^1(\mathbb{T}^d\to\mathbb{C}^m)$
by an identical argument, it holds that

<div>
 $$\mathcal{F}f(k)=\mathcal{F}\U 1f(k)=\int\U {\mathbb{R}^d}f(x)e^{-2\pi ik\cdot x}$$
</div>

and where now Plancherel's theorem gives that, for such $f$:

<div>
 $$\label{Plancerelpft}
    f(x)=\sum\U {k\in\mathbb{Z}^d}\hat{f}(k)e^{2\pi ik\cdot x}.$$
</div>

## Other settings for the Fourier transform

The study of the Fourier transform is a vast subject and cannot be covered in a single blog post. We have chosen to focus on the case of functions with domain on Euclidean space $\mathbb{R}^d$ or the torus $\mathbb{T}^d$
and studied the $L^2$ theory. However, one may also define the Fourier transform when the domain is a group $G$. In this case, the notions of characters (for abelian groups) and representations (for non-abelian groups) appear. If
$G$ is [locally compact](https://en.wikipedia.org/wiki/Locally_compact_space), [abelian](https://en.wikipedia.org/wiki/Abelian_group) and [Haussdorff](https://en.wikipedia.org/wiki/Hausdorff_space) (LCA) one defines the _Pontryagin dual_ (or group of characters) of $G$ as

<div>
$$\hat{G}:=\{\text{ group homomorphisms } \xi:(G,+)\to(\C,\cdot): \abs{\xi(g)}=1,\quad\forall g\in G\}.$$
</div>

Since every locally compact Hausdorff group has a [Haar measure](https://en.wikipedia.org/wiki/Haar_measure) $\mu$ (that is a measure on the Borel sets which is translation invariant and finite on compact sets) which is unique up to a multiplicative constant, we can speak of the spaces $L^p(G)$. The Fourier transform is then defined for all $f\in L^1(G)$ as follows:

<div>
$$\hat{f}(\xi):=\int_G f(x)\xi(x) \mu(dx).$$
</div>

From here one can proceed as previously to extend the Fourier transform on $G$ to an isometry (if the Haar measure is properly normalized) of $L^2(G)$. In the particular cases we studied, we had that the Haar measure is just the Lebesgue measure and

<div>
$$\widehat{\mathbb{R}^d}=\left\{e^{2\pi i\xi \cdot}:\xi\in\R^d\right\}\quad;\widehat{\mathbb{T}^d}=\left\{e^{2\pi ik \cdot}:k\in\Z^d\right\}.$$
</div>
This helps shed light on why in the euclidean case we obtain an integral and in the periodic case we obtain a sum. It is also possible to study the $L^p$ theory of the
Fourier transform for general $p$. The case $p=2$ is greatly facilitated by the fact that $L^2(G), L^2(\hat{G})$ are Hilbert spaces. But for $p\neq 2$, this does not hold. The theory in this setting relies heavily on interpolation theory as one must use the [Riesz Thorin theorem](https://en.wikipedia.org/wiki/Riesz%E2%80%93Thorin_theorem) to obtain the Haussdorff Young inequality

<div>
$$\|\mathcal{F}{f}\|_{L^q(\mathbb{R}^d\to \mathbb{C}^m)}\leq \|{f}\|_{L^p(\mathbb{R}^d\to \mathbb{C}^m)},\quad \forall 1\leq p\leq 2, $$
</div>
where $1/p+1/q=1$. This extends the Fourier transform to $L^p(\mathbb{R}^d\to \mathbb{C}^m)$ for all $1\leq p\leq 2$ and to $L^p(\mathbb{T}^d\to \mathbb{C}^m)$ for all $p\geq 1$ (as $\mathbb{T}^d$ has finite measure). This done, one can study the convergence of Fourier integrals and series
<div>
$$S_Rf(x):=\int_{[-R,R]^d}\hat{f}(\xi)e^{-2\pi i\xi\cdot x}d\xi;\quad S_Nf(x):=\sum_{k\in[-N,N]^d\cap\mathbb{Z}^d}\hat{f}(k)e^{-2\pi ik\cdot x}. $$
</div>

We can speak both of $L^p$ and almost everywhere convergence.

**Theorem ([M. Riesz](https://link.springer.com/article/10.1007/BF01171098).** It holds that for all $f\in L^p(\mathbb{R}^d)$

<div>
$$\lim_{R\to\infty}\|S_Rf-f\|_{L^p(\mathbb{R}^d\to \mathbb{C}^m)}=0$$
</div>
if and only if $1<p\leq 2$.

**Theorem ([Carleson Hunt](https://en.wikipedia.org/wiki/Carleson%27s_theorem#:~:text=The%20analogous%20result)).** It holds that for all $f\in L^p(\mathbb{R})$

<div>
$$\lim_{R\to\infty}S_Rf=f, \quad \text{almost everywhere}$$
</div>
if and only if $1<p\leq 2$.
Note that, in this second case, we must restrict ourselves to dimension $1$. The case of dimension $d>1$ is an [open problem](https://terrytao.wordpress.com/2009/04/06/the-fourier-transform/#:~:text=Remark%2046-,It%20is,-a%20famous%20open). For the torus one has similar results where now the exponent of integration is extended past $p=2$.

**Theorem ([M. Riesz](https://link.springer.com/article/10.1007/BF01171098)).** It holds that for all $f\in L^p(\mathbb{T}^d)$

<div>
$$\lim_{N\to\infty}\|S_Nf-f\|_{L^p(\mathbb{R}^d\to \mathbb{C}^m)}=0$$
</div>
if and only if $1<p<\infty$.

**Theorem ([Carleson-Hunt](https://en.wikipedia.org/wiki/Carleson%27s_theorem)).** It holds that for all $f\in L^p(\mathbb{T}^d)$

<div>
$$\lim_{R\to\infty}S_Rf=f, \quad \text{almost everywhere}$$
</div>
if and only if $1<p\leq\infty$.

Counterexamples exist at the boundary case $p=1$. As Kolmogorov showed, the Fourier series may be made to diverge almost everywhere (see [4](https://iopscience.iop.org/article/10.1070/RM1983v038n04ABEH004205/pdf) Theorem 3.1). With this, we conclude this section.

# Distributions and Sobolev Spaces

Here we will quickly recall the concepts of tempered distributions and
Sobolev spaces, which are concepts of utmost importance in the field of
PDEs and Fourier analysis. The idea is as follows: given a topological
vector space $V$, we denote the dual of $V$ by

<div>
 $$V':=\lbrace w:E\to\mathbb{C}\hspace{2pt}: w \hspace{2pt}\text{continuous}\rbrace.$$
</div>

Furthermore, given $w\in V'$ and $u\in V$ we use the notation

<div>
 $$(u,w):=w(u)$$
</div>

The reason for this is that $w(u)$ can often be
interpreted as the inner product of $w$ against $u$ in a suitable
Hilbert space. In our case, this Hilbert space will be
$L^2(\mathbb{R}^d\to\mathbb{C})$ and the above interpretation will
allow us to extend differentiation and the Fourier transform by a
technique called "duality". We will apply this where
$V=\mathcal{S}(\mathbb{R}^d\to\mathbb{C})$, first we need to introduce
a topology on $E$. In general, given a real vector space $V$ together
with a countable family of semi-norms $\lbrace p\U j\rbrace\U {j=0}^\infty$
with the property that: given $x\neq 0$, there exists $j$ such that
$p\U j(x)\neq 0$. Then

<div>
$$\begin{align}
    d(x,y):=\sum \U {j=0}^\infty 2^{-j}\frac{p \U j(x-y)}{1+p \U j(x-y)}\quad \forall{x,y}\in {E}
\end{align}$$
</div>

is a translation invariant metric on $E$.

**Exercise 1.** Show that $d(x \U n, x)\to 0$ if and only if $p\U j(x \U n-x)\to 0$ for all $j \in \mathbb{N}$. Also show that, if $d'$ is any other distance verifying the above, then $d,d'$ induces the same topology on $E$.

**Hint:** For uniqueness, use the fact that the topology of a first countable space is completely determined by sequential convergence.

In the case of the Schwartz
space $\mathcal{S}(\mathbb{R}^d\to\mathbb{C})$ we give it the topology
induced by

<div>
 $$\label{seminornormsSchwartz}
    p\U k(u):=\sum\U {\abs{\alpha}\leq k} \sup\U {x\in\mathbb{R}^d}\left\langle x\right\rangle^k \abs{D^\alpha u(x)}.$$
</div>

Though other families of semi-norms, the reader may be familiar with such
as

<div>
 $$p\U {k,\alpha}:=\sup\U {x\in\mathbb{R}^d}\abs{x}^k \abs{D^\alpha u(x)};\quad\text{or}\quad p'\U {k,\alpha}:=\sup\U {x\in\mathbb{R}^d}(1+\abs{x})^k \abs{D^\alpha u(x)}$$
</div>

induce equivalent topologies. We note that with this metric
$\mathcal{S}(\mathbb{R}^d\to\mathbb{C})$ is complete. For a quick
proof based on the fundamental theorem of calculus, see, for example
[3](https://books.google.co.uk/books/about/Integraci%C3%B3n\U de\U funciones\U de\U varias\U vari.html?id=uuHbOgAACAAJ&redir\U esc=y) page 237.

**Definition 4**. The space of tempered distributions is the dual
space to $\mathcal{S}(\mathbb{R}^d\to\mathbb{C})$ with the topology
generated by $p\U k)$. We write it
$\mathcal{S}'(\mathbb{R}^d\to\mathbb{C})$.

One may verify that we have the inclusion

<div>
 $$\begin{aligned}
\label{lpisdistr}
    L^p(\mathbb{R}^d\to\mathbb{C})\hookrightarrow\mathcal{S}'(\mathbb{R}^d\to\mathbb{C});\quad f\mapsto T\U f\end{aligned}$$
</div>

where given $u\in \mathcal{S}(\mathbb{R}^d\to\mathbb{C})$ we define

<div>
 $$T\U f(u):=\left\langle u,f\right\rangle:=\int\U {\mathbb{R}^d} u\overline{f}.$$
</div>

Let us write $T^t$ for the transpose of a linear function $T$ and recall
that the Fourier transform is an endomorphism of the Schwartz space.
Then, given two Schwartz functions $u,v$, we have already seen that, by a simple application of Fubini,

<div>
 $$T\U {\mathcal{F}v}(u)=\left\langle u,\mathcal{F}v\right\rangle=\left\langle\mathcal{F}^{-1} u,v\right\rangle=(\mathcal{F}^{-1}u,T\U v)$$
</div>

and integration by parts gives

<div>
 $$T\U {D^\alpha v}(u)=\left\langle u,D^\alpha v\right\rangle=(-1)^{\abs{\alpha}}\left\langle D^\alpha u,v\right\rangle=((-1)^{\abs{\alpha}}D^\alpha u,T\U v)\quad\forall{\alpha}\in {\mathbb{N}^d}.$$
</div>

This gives us a way of extending the Fourier transform and
differentiation to the space of tempered distributions.

**Definition 5**. Given $w\in\mathcal{S}'(\mathbb{R}^d\to\mathbb{C})$
and $\alpha\in\mathbb{N}^d$ we define the (distributional) Fourier
transform of $w$ by

<div>
 $$\mathcal{F}w:= w\circ \mathcal{F}^{-1}$$
</div>

and the
(weak) $\alpha$'th derivative of $w$ by

<div>
 $$D^\alpha w:= w\circ((-1)^{\abs{\alpha}}D^\alpha).$$
</div>

The method we used above to extend $\mathcal{F}, D^\alpha$ is called the
duality method and appears very frequently. Another way of writing the
above definition is:

<div>
 $$(u, \mathcal{F}w):=(\mathcal{F}^{-1} u, w);\quad(u,D^\alpha w):=(-1)^{\abs{\alpha}}(D^\alpha u,w)$$
</div>

Due to our previous discussion, we have that with this definition

<div>
 $$\label{ftlpdistr}
    \mathcal{F}T\U u=T\U {\mathcal{F}u};\quad D^\alpha T\U {u}=T\U {D^\alpha u}\quad\forall u\in \mathcal{S}(\mathbb{R}^d).$$
</div>

Just as one would desire.

Two other operations that are permitted on
$\mathcal{S}(\mathbb{R}^d\to\mathbb{C})$ are multiplication by
functions of polynomial growth $p$ and the application of the inverse
Fourier transform, which we shall, as for $L^2$ functions, denote by
$\mathcal{F}^{-1}$. Both definitions are once again being given by
duality.

<div>
 $$(u,pw):=(\overline{p}u,w);\quad (u,\mathcal{F}^{-1}w):=(\mathcal{F}u,w) .$$
</div>

Before ending our discussion of (scalar) tempered distributions, we
comment on some generalizations. We first note that the previous
discussion works equivalently for vector-valued distributions, i.e.
elements of the dual to $\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)$,
which we shall denote by

<div>
 $$\mathcal{S}'(\mathbb{R}^d\to\mathbb{C}^m)$$
</div>

where the only change is that the inclusion of integrable functions is
now given by

<div>
 $$\begin{aligned}
\label{lpisvectordistr}
    L^p(\mathbb{R}^d\to\mathbb{C}^m)\hookrightarrow\mathcal{S}'(\mathbb{R}^d\to\mathbb{C}^m);\quad f\mapsto T\U f\end{aligned}$$
</div>

with $T\U f$ defined by

<div>
 $$T\U f(u):=\int\U {\mathbb{R}^d} u\cdot \bar{f}\quad\forall{u}\in {\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)}.$$
</div>

In both cases, we have that, by duality, due to the formulas derived in
(\ref{formula}), given a tempered distribution $w$ and
$\alpha\in \mathbb{N}^d$

<div>
 $$\begin{aligned}
\label{derivativedistronperiodic}
    D^\alpha\mathcal{F}w =(-2\pi i)^{\abs{\alpha}}\mathcal{F}x^\alpha w;\quad
    \mathcal{F}D^{\alpha} w= (2\pi i)^{\abs{\alpha}}x^\alpha\mathcal{F}w.\end{aligned}$$
</div>

As we have observed before, multiplication by functions of
polynomial growth is a well-defined operation on
$\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^m)$ so the above expressions
are also well-defined. A quick verification also shows that since
Plancherel's theorem holds for all Schwartz functions,

<div>
 $$\label{planchereldistr}
    \mathcal{F}^{-1}\mathcal{F}w=\mathcal{F}\mathcal{F}^{-1}w=w.$$
</div>

Finally, in addition to "changing the image" of our distributions, we
may also "change the domain" by considering, for example, periodic
tempered distributions, where now, as we saw in the section on the
Fourier transform, $C^\infty(\mathbb{T}^d\to\mathbb{C}^m)$ takes the
place of the Schwartz space and where we place on
$C^\infty(\mathbb{T}^d\to\mathbb{C}^m)$ the topology defined by the
countable family of semi-norms:

<div>
 $$q\U k(u):=\sum\U {\abs{\alpha}\leq k}\sup\U {x\in\mathbb{T}^d}\abs{D^\alpha u}$$
</div>

and denote its dual by $\mathcal{S}'(\mathbb{T}^d\to\mathbb{C}^m).$
Note that, as the domain is bounded, multiplication by polynomials to
ensure rapid decrease is redundant. By defining, as is natural, the
Fourier series of a periodic distribution $w$ by the sequence (which can
be shown to be of polynomial growth)

<div>
 $$\label{fouriercoeffperiodicdist}
    \hat{w}(k):=(e^{-2\pi ikx},w)\quad k\in\mathbb{Z}^d$$
</div>

and its
$\alpha$-th distributional derivative by

<div>
 $$(u,D^\alpha w):=(-1){^\abs{\alpha}}(D^\alpha u,w)$$
</div>

we derive formulas
analogous to the ones seen in the section on the Fourier transform for
"periodic\" distributions as well. Namely:

<div>
 $$\begin{align}\label{periodic}
    w=\sum\U {k\in\mathbb{Z}^d}\hat{w}(k)e^{2\pi i k x};\quad\widehat{D^\alpha w}(k)=(2\pi ik)^\alpha\hat{w}(k).\end{align}$$
</div>

To prove it, all we have to do is apply Plancherel on $u$ and move terms
around via duality,

<div>
 $$\begin{gathered}
    (u,w)=(\sum\U {k\in \mathbb{Z}^d}\hat{u}(k)e^{2\pi ik\cdot x},w )=\sum\U {k\in \mathbb{Z}^d}  \hat{u}(k)\hat{w}(k)\\=\sum\U {k\in \mathbb{Z}^d}  \left(\int\U {\mathbb{T}^d} u(x)e^{-2\pi i\omega\cdot  x}dx\right)\hat{w}(k)=\int\U {\mathbb{T}^d} u(x)\left(\sum\U {k\in \mathbb{Z}^d} \hat{w}(k) e^{-2\pi i\omega\cdot  x}\right)dx.\end{gathered}$$
</div>

This proves the first part, and the second can be proved directly by
considering the relevant definitions.\
\
To sum up, what we have seen, due to the natural inclusion of integrable
functions in the space of tempered distributions and the analogous
inclusion in the periodic case, the notion of Fourier transform and
differentiation extends to the larger space of tempered distributions.
This allows us to manipulate rough functions (periodic or non-periodic)
as if they had Fourier transforms and were smooth. As we shall see, this
will prove of great use when obtaining "distributional solutions" to
some PDEs. We now give the general method by which this achieved

**Definition 6.** Consider a mapping $\mathcal{L}$

<div>
 $$\mathcal{L}:\mathcal{S}(\mathbb{R}^d\to\mathbb{C}^n)\to \mathcal{S}(\mathbb{R}^d\to\mathbb{C}^n),$$
</div>
with adjoint $\mathcal{L}^*$. That is,  
<div>
 $$\label{adjoint}
    (\mathcal{L}u,v)=(u,\mathcal{L}^*v)\quad\forall u,v\in \mathcal{S}(\mathbb{R}^d\to\mathbb{C}^n).$$
</div>

Then, given $f \in \mathcal{S}'(\mathbb{R}^d\to \mathbb{C}^n)$ we say that a
distributional solution to $\mathcal{L}w=f$ is any tempered distribution
$w\in \mathcal{S}'(\mathbb{R}^d\to\mathbb{C}^n)$ verifying

<div>
 $$\label{distrsol}
    (\mathcal{L}^*v,u)=(v,f)\quad\forall v\in \mathcal{S}(\mathbb{R}^d\to\mathbb{C}^n).$$
</div>

In the above definition, $\mathcal{L}$ typically defines a linear or non-linear
differential equation. Note that the above definition may be extended
without any difficulty to the case of (periodic) distributional
solutions in the case where
$P: C^\infty(\mathbb{T}^d\to\mathbb{C}^m)\to C^\infty(\mathbb{T}^d\to\mathbb{C}^n)$.

**Example 1.** Set $\mathcal{L}=1-\Delta$, as we have seen previously
$\Delta$ extends to $S:=\mathcal{S}'(\mathbb{R}^d\to\mathbb{C}^m)$
with

<div>
 $$\mathcal{F}(\Delta \omega)=1+4\pi \abs{\xi }^2\mathcal{F}w .$$
</div>

As
a result, we deduce that for any
$f \in \mathcal{S}'(\mathbb{R}^d\to \mathbb{C}^n)$ the equation $\mathcal{L}w=f$
has as its unique solution

<div>
 $$w=\mathcal{F}^{-1}\left(\frac{-\hat{f}}{1+4\pi \abs{\xi }^2 }\right).$$
</div>

# Sobolev spaces

Sobolev spaces form a particular case of tempered distributions that we
interpret as being smooth and integrable up to sufficient orders.

 <a name="def 7">
 **Definition 7.**</a> Given $k\in\mathbb{N}^+$ we define the Sobolev
space $H^k(\mathbb{R}^d\to\mathbb{C}^m)$ as:

<div>
 $$\begin{gathered}
        H^k(\mathbb{R}^d\to\mathbb{C}^m):=\\ \lbrace f\in L^2(\mathbb{R}^d\to\mathbb{C}^m): D^\alpha f\in L^2(\mathbb{R}^d\to\mathbb{C}^m)\hookrightarrow\mathcal{S}'(\mathbb{R}^d\to\mathbb{C}^m)\quad\forall\hspace{2pt}\abs{\alpha}\leq k\rbrace,
    \end{gathered}$$
</div>

where we consider
$L^2(\mathbb{R}^d\to\mathbb{C}^m)$ as a subspace of
$\mathcal{S}'(\mathbb{R}^d\to\mathbb{C}^m)$.

We may interpret the Sobolev space $H^k(\mathbb{R}^d\to\mathbb{C}^m)$
as the space of $k$ times differentiable functions in
$L^2(\mathbb{R}^d\to\mathbb{C}^m)$ and we give it the norm:

<div>
 $$\norm{f}\U {H^k(\mathbb{R}^d\to\mathbb{C}^m)}:=\sum\U {\abs{\alpha}\leq k}\norm{D^\alpha f}\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}\qquad f\in H^k(\mathbb{R}^d\to\mathbb{C}^m).$$
</div>

Note that it is not enough to require $\abs{\alpha}=k$ in the formula above. For example,
the tempered distribution
$1 \in \mathcal{S}'(\mathbb{R}^d\to\mathbb{C})$ has a derivative equal
to zero however, it is not itself in $L^2(\mathbb{R}^d\to\mathbb{C})$. That is, $1\notin H^1(\mathbb{R}^d)$ Now,
as [the Fourier transform is an automorphism](#planch) of
$\mathcal{S}'(\mathbb{R}^d\to\mathbb{C}^m)$, by using the previously derived formula (\ref{formula})
we deduce that

<div>
 $$D^\alpha f\in L^2(\mathbb{R}^d\to\mathbb{C}^m)\iff \mathcal{F}(D^\alpha f)=\abs{(2\pi i\xi )^{\alpha}} \hat{f}(\xi)\in L^2(\mathbb{R}^d\to\mathbb{C}^m).$$
</div>

As a result, we ontain that

<div>
 $$\label{sobolevcondition}
    f\in H^k(\mathbb{R}^d\to\mathbb{C}^m)\iff \sum\U {\abs{\alpha}\leq k} \abs{(2\pi i\xi )^{\alpha}}\hat{f}(\xi)\sim\U k \left\langle\xi\right\rangle^k\hat{f}\in L^2(\mathbb{R}^d\to\mathbb{C}^m).$$
</div>

In fact, since the Fourier transform is a unitary transformation on
$L^2(\mathbb{R}^d\to\mathbb{C}^m)$, the same reasoning gives

<div>
 $$\label{sobolevnorm}
    \norm{f}\U {H^k(\mathbb{R}^d\to\mathbb{C}^m)}\sim\U k \norm{\left\langle\xi\right\rangle^k\hat{f}(\xi)}\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)}.$$
</div>

From the two equations above, we deduce that if we define for a given
real number $s$ (including negative numbers!), the $s$-th order Sobolev
space as

<div>
 $$H^s(\mathbb{R}^d\to\mathbb{C}^m):=\lbrace f\in \mathcal{S}'(\mathbb{R}^d\to\mathbb{C}^m): \left\langle\xi\right\rangle^s\hat{f}(\xi)\in L^2(\mathbb{R}^d\to\mathbb{C}^m)\rbrace,$$
</div>

and give it the norm

<div>
 $$\norm{f}\U {H^s(\mathbb{R}^d\to\mathbb{C}^m)}:= \norm{\left\langle\xi\right\rangle^s\hat{f}(\xi)}\U {L^2(\mathbb{R}^d\to\mathbb{C}^m)},$$
</div>

then our new definition is equivalent to the [previous one](#def 7) when
$s$ is a positive integer. We have thus found how to generalize the
concept of Sobolev space to all real orders and obtained a useful way of
characterizing them and giving a neat expression for their norm.
Nonetheless, it will always be useful to retain the first definition
based on derivatives, as it carries with it the motivation behind the
definition of Sobolev spaces. As was the case with tempered
distributions, we can extend the concept of Sobolev space to periodic
domains by defining given an integer $k$ the Sobolev space
$H^k(\mathbb{T}^d\to\mathbb{C}^m)$ as the space of square-integrable
$\mathbb{Z}^d$ periodic functions with distributional derivatives
themselves square integrable. Explicitly, we define:

<div>
 $$\begin{gathered}
\label{sobolevdef2}
    H^s(\mathbb{T}^d\to\mathbb{C}^m):=\\\lbrace f\in L^2(\mathbb{T}^d\to\mathbb{C}^m): D^\alpha f\in L^2(\mathbb{T}^d\to\mathbb{C}^m)\hookrightarrow\mathcal{S}'(\mathbb{T}^d\to\mathbb{C}^m)\quad\forall\hspace{2pt}\abs{\alpha}\leq s\rbrace\end{gathered}.$$
</div>

Using the same method as before, this time by [Plancherel](#plancherel theorem) and
the [correspondence between regularity and decay](#decay) for the
Fourier transform of periodic functions, we deduce that

<div>
 $$D^\alpha f\in L^2(\mathbb{T}^d\to\mathbb{C}^m)\iff\widehat{D^\alpha f}(k)=\abs{k^\alpha}\hat{f}(k)\in l^2(\mathbb{Z}^d\to\mathbb{C}^m),$$
</div>

which leads us, as in the previous case, to define for $s\in\mathbb{R}$
the more general Sobolev space

<div>
 $$H^s(\mathbb{T}^d\to\mathbb{C}^m):=\lbrace f\in \mathcal{S}'(\mathbb{R}^d\to\mathbb{C}^m): \left\langle k\right\rangle^{s}\hat{f}(k)\in l^2(\mathbb{Z}^d\to\mathbb{C}^m)\rbrace$$
</div>

and to give it the norm

<div>
 $$\label{sobolevgeneraldef}
    \norm{f}\U {H^s(\mathbb{T}^d\to\mathbb{C}^m)}:=\left(\sum\U {k\in\mathbb{Z}^d}\left\langle k\right\rangle^{2s}\abs{\hat{f}(k)}^2\right)^{\frac{1}{2}},$$
</div>

where of course the two definitions coincide for
$s\in\mathbb{N}$. Note that, by the previous discussion, we have that
both in the Euclidean and periodic case

<div>
 $$\begin{aligned}
\label{Sobolev derivatives embedding}
    f\in H^s(\mathbb{R}^d\to\mathbb{C}^m)  & \iff  D^\alpha f\in H^{s-\abs{\alpha}}(\mathbb{R}^d\to\mathbb{C}^m)\qquad\forall\abs{\alpha}\leq s  \\
    f\in H^s(\mathbb{T}^d\to\mathbb{C}^m) & \iff  D^\alpha f\in H^{s-\abs{\alpha}}(\mathbb{T}^d\to\mathbb{C}^m)\qquad\forall\abs{\alpha}\leq s\end{aligned}.$$
</div>

One major advantage of working with the Sobolev spaces $H^s$ is that,
differently to the classical space of smooth functions $C^s$, they form
a Hilbert space with the inner product given by

<div>
 $$\begin{aligned}
    \left\langle f,g\right\rangle\U {H^s(\mathbb{R}^d\to\mathbb{C}^m)}  & :=\int\U {\mathbb{R}^d}\left\langle\xi \right\rangle^{2s}\hat{f}(\xi )\overline{\hat{g}(\xi )} d\xi \\
    \left\langle f,g\right\rangle\U {H^s(\mathbb{T}^d\to\mathbb{C}^m)} & :=\sum\U {k\in \mathbb{Z}^d} \left\langle k \right\rangle^{2s}\hat{f}(k)\overline{\widehat{g}(k )}.\end{aligned}$$
</div>

This gives one access to all the power of functional analysis and is
invaluable in proofs. However, at the end of the day, one would like to prove
that solutions with smooth initial data are themselves smooth in a
classical sense. This can be done by showing that the solution belongs
to a Sobolev space of high enough order together with the following two
results.

 <a name="lemma 2">
 **Lemma 2 (Sobolev embedding).**</a> Given
$f\in H^{s}(\mathbb{T}^d\to\mathbb{C}^m)$ with $s>d/2$. Then the
Fourier series of $f$ is absolutely convergent and
$f\in C(\mathbb{T}^d\to\mathbb{C}^m)$ with the bound

<div>
 $$\norm{f}\U {L^\infty(\mathbb{T}^d\to\mathbb{C}^m)}\lesssim\U {d,s}\norm{f}\U {H^s(\mathbb{T}^d\to\mathbb{C}^m)}$$
</div>

**Proof.** The proof is an application of the Cauchy-Schwartz inequality
and [Lemma 0](#lemma 0). We have that

<div>
 $$\begin{gathered}
        \sum\U {k\in\mathbb{Z}^d}\abs{\hat{f}(k)}=\sum\U {k\in\mathbb{Z}^d} \left\langle k\right\rangle^{-s}\left\langle k\right\rangle^{s}\abs{\hat{f}(k)}\leq\left(\sum\U {k\in\mathbb{Z}^d} \frac{\left\langle k\right\rangle^{-2s}}{2}\right)^{\frac{1}{2}}\left(\sum\U {k\in\mathbb{Z}^d}\frac{\left\langle k\right\rangle^{2s}}{2}\abs{\hat{f}(k)}^2\right)^{\frac{1}{2}}\\
        \lesssim\U {d,s}\norm{f}\U {H^s(\mathbb{T}^d\to\mathbb{C}^m)}<\infty.
    \end{gathered}$$
</div>

In consequence, the sum

<div>
 $$\label{Fourier sum}
        \sum\U {k\in\mathbb{Z}^d}\hat{f}(k)e^{2\pi ik\cdot x}$$
</div>

converges
absolutely (and uniformly) to some $g$. Since by Plancherel's Theorem, the above sum
also converges in $L^2(\mathbb{T}^d\to\mathbb{C}^m)$ to $f$, we deduce
that $f=g$ (for example,
by taking a subsequence of the above sum that converges almost
everywhere to $f$). Therefore

<div>
 $$\norm{f}\U {L^\infty(\mathbb{T}^d\to\mathbb{C}^m)}=\norm{\sum\U {k\in\mathbb{Z}^d}\hat{f}(k)e^{2\pi ik\cdot x}}\U {L^\infty(\mathbb{T}^d\to\mathbb{C}^m)},$$
</div>

which is

<div>
 $$\leq\sum\U {k\in\mathbb{Z}^d}\norm{\hat{f}(k)e^{2\pi ik\cdot x}}\U {L^\infty(\mathbb{T}^d\to\mathbb{C}^m)}=\sum\U {k\in\mathbb{Z}^d}\abs{\hat{f}(k)}\lesssim\U {d,s}\norm{f}\U {H^s(\mathbb{T}^d\to\mathbb{C}^m)}.$$
</div>

The continuity of $f$ follows from the point-wise equality

<div>
 $$\label{pointwise convergence Fourier sum}
        f(x)=\sum\U {k\in\mathbb{Z}^d}\hat{f}(k)e^{2\pi ik\cdot x}=\int\U {\mathbb{Z}^d} \hat{f}(k)e^{2\pi ik\cdot x} dk$$
</div>

together with the monotone convergence theorem applied to
$\mathbb{Z}^d$ with the counting measure $dk$. ◻

As a corollary of this, we have the following two results

**Proposition 7 (Sobolev embedding)**. Let
$f\in H^s(\mathbb{T}^d\to\mathbb{C}^m)$ where $s>\frac{d}{2}+r$. Then
$f\in C^r(\mathbb{T}^d\to\mathbb{C}^m)$.

**Proof.** Using our knowledge of how the derivative transports functions through sobolev space, we may apply the
previous proposition to deduce that $D^\alpha f$ is continuous for all
$\abs{\alpha}\leq r$. Therefore, it suffices to show that for
$\abs{\alpha}\leq r$ the distributional derivatives $D^\alpha f$ are
also the classical derivatives of $f$ which we denote by $f\U \alpha$. By
the hypothesis placed on $f$, we have that the series

<div>
 $$\sum\U {k\in\mathbb{Z}^d} (2\pi ik)^\alpha \hat{f}(k)e^{2\pi ik\cdot x}$$
</div>

is absolutely convergent (by [Lemma 2](#lemma 2)), and hence, we may commute the
derivatives of $f$ with the sum in its Fourier series to deduce the
point-wise equality

<div>
 $$f\U \alpha(x)=\sum\U {k\in\mathbb{Z}^d} (2\pi ik)^\alpha \hat{f}(k)e^{2\pi ik\cdot x}.$$
</div>

Now, note that by using our calculations for the Fourier transform of the derivative of periodic distributions in (\ref{periodic})
we also have that the equality

<div>
 $$D^\alpha f(x)=\sum\U {k\in\mathbb{Z}^d} (2\pi ik)^\alpha \hat{f}(k)e^{2\pi ik\cdot x},$$
</div>

holds in $L^2(\mathbb{T}^d\to\mathbb{C}^m)$. From these last two
equalities, we deduce that $f\U \alpha=D^\alpha f$ almost everywhere, which
concludes our proof. ◻

As before, the previous results also have a Euclidean analogue whose proof
is identical in replacing all of the above sums over $\mathbb{Z}^d$
with integrals over $\mathbb{R}^d$. Finally, we conclude this post with
a neat little trick. Given smooth $f$ and some differential operator
$\mathcal{L}=\sum\U {\alpha} D^\alpha=p(D)$ we have that

<div>
 $$D^\alpha f =\mathcal{F}^{-1}(\mathcal{F}\mathcal{L}f)=\mathcal{F}^{-1}(p(2 \pi i\xi )\hat{f}(\xi )).$$
</div>

The term $p$ is called a Fourier multiplier, and there is no
need to limit ourselves to polynomials. In fact, we may make the general
definition that for a function of two variables $p$

<div>
 $$p(x,D)f:=\mathcal{F}^{-1}(p(x,\xi )\hat{f}(\xi )).$$
</div>

This leads to the
definition of pseudo-differential operators. A particular case is that
of fractional operators. We now show an example.

**Example 2.** Given smooth $f$ we have that

<div>
 $$\Delta f=\mathcal{F}^{-1}(-4 \pi^2 \abs{\xi}^2 \hat{f}(\xi )).$$
</div>

As a
result, we define for all $s\in \mathbb{R}$

<div>
 $${(-\Delta)}^sf:=\mathcal{F}^{-1} ((4\pi^2 \left\langle\xi \right\rangle^2)^s\hat{f}(\xi )).$$
</div>

This post is already getting a bit long (if you've held on till the end
I salute you), so we leave it off here with a neat little exercise (our
first of this blog)

**Exercise 2.** How should we define

<div>
 $$T:=\left(1-\frac{\Delta}{4\pi ^2}  \right)^\frac{s}{2}\text{?}$$
</div>

Once you do so, show that for all $s,r \in \mathbb{R}$, the operator $T$
defines a linear bijective isometry

<div>
 $$T: H^r(\mathbb{R}^d\to\mathbb{C}^m)\to H^{k-s}(\mathbb{R}^d\to\mathbb{C}^m).$$
</div>

In our future posts, we will discuss Sobolev spaces for different orders of integrability and on general domains (not just $\mathbb{R}^d$ and $\mathbb{T}^d$).

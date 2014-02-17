---
layout: post
topics: gsoc-2011 pydy sympy kanes-method
title: Equations of Motion Example
---

Here, I have derived by hand the equations of motion for a rolling disc.  The
scanned document at the bottom shows the steps I went through.

This is to show what PyDy (my Google Summer of Code 2011 project, under SymPy)
will be doing; by using SymPy’s symbolic manipulation abilities, one can use
the functions in PyDy to derive equations of motion symbolically.  A simple
system like the rolling disc can be done by hand easily but for larger,
multibody systems you will need some computational assistance.

PyDy is primarily built around Kane’s Method [1], but will be able to work
with Lagrange’s Method or Newton-Euler.

Edit: PDF removed for now until I fix an error….

[1] Kane, T. R. and Levinson, D. A. (1985)  Dynamics: Theory and
Applications.  MacGraw-Hill Series in Mechanical Engineering. MacGraw-Hill Book
Company, NewYork.

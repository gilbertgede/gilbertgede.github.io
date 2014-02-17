---
layout: post
topics: pydy gsoc-2011 mems sympy
title: PyDy and other things
---

This weekend is Maker Faire, so the lab is going there.  One thing I'll have is
some info on some MEMS sensors from a class project last quarter.  We collected
info on the Analog Devices ADXL 345 and Invensense ITG-3200 (tried to use a
Honeywell HMC5843, but we couldn't read it over I2C).  Anyways, I got
permission from my group members to post our report online, so here it is.

Report: [MAE276 Final Paper](/images/mae276_finalpaper_6dof.pdf)

For PyDy/SymPy & GSoC there is also some news.  It looks like the previous
separation between UnitVector and Vector classes is going away; in addition
they will no longer extend SymPy's Basic or Expr classes.  There will now be
only one Vector class.

It will store a list of lists; the inner list will have the 3 vector measure
numbers for a frame (something like [([1],[2],[4]),'b'] ), where the measure
numbers will use the SymPy Matrix class (and can have symbols in them).  The
outer list will hold each of these lists for each frame.  So the data stored
will be something like [[([1],[2],[4]),'b'],[([3*x],[1],[0]),'c']]... or
something like that.  The current plan is to write our own operators for
addition, subtraction, scalar multiplication & division, and dot and cross
products.  By not using the SymPy classes, we can better control how the Vector
class will behave.  One important behavior is to have every operator (except
for dot product) take in and return a vector, and not have any confusion
between SymPy objects and Vectors when using operators.

There is also some debate as to whether the ReferenceFrame class should store
its own basis vectors, or they should be returned upon initialization (see the
sympy list post: Question regarding vectors.  I understand the argument to keep
them with their frame and the awkwardness that will exist when creating the
basis vectors upon ReferenceFrame initialization.  But, I feel that the Vector
class already stores information about each frame (in its inner lists), and
question whether basis vectors are a property of ReferenceFrames, or a frame is
a property of a set of basis vectors.

I guess the orthonormal properties of a set of 3 basis vectors exist
independently of a particular reference frame.  I guess what defines a frame?
I think of it as a rotation (and related time derivatives) from on set of basis
vectors to another.  So it is defined by both its basis vectors and a rotation.
I still feel like its is preferable to keep the basis vectors outside of the
ReferenceFrame class, but not sure my position has a strong enough argument
(but I also don't think it is too weak of an argument).  Hopefully starting to
discuss more of the ReferenceFrame class methods will clear this up.

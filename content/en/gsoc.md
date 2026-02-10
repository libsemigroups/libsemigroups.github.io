---
layout: "gsoc"
bgImage: "/images/smalloverlap_510x510.png"
---

# GSoC 2026 project ideas

This page contains a list of ideas for GSoC in 2026 within the
[libsemigroups][] organisation:

1. [Julia bindings for libsemigroups](#1-julia-bindings-semigroupsjl-for-libsemigroups)
2. [Formal verification of Knuth-Bendix and
   Todd-Coxeter](#2-formal-verification-of-knuth-bendix-and-todd-coxeter)
3. [AI for auto-tuning undecidable
   problems](#3-ai-for-auto-tuning-undecidable-problems)
4. [High-performance tropical algebra
   library](#4-high-performance-tropical-algebra-library)
5. [Computing congruences of finite inverse
   semigroups](#5-computing-congruences-of-finite-inverse-semigroups)
6. [Improving errors and their messages in
   GAP](#6-improving-errors-and-their-messages-in-gap)
7. [Free bands](#7-free-bands)

### 1. Julia bindings Semigroups.jl for libsemigroups

This project would involve porting as much as possible of the functionality of
[libsemigroups][] into [Semigroups.jl][]. Something similar already exists for
python in [libsemigroups_pybind11][]. The aim is for [Semigroups.jl][] to
expose the low-level functionality of [libsemigroups][] to be used as a
foundation for a separate higher level package. In particular, a longer term
aim of this project is to replace the kernel extension of the
[GAP package Semigroups][] with [Semigroups.jl][].

This project may involve:

- some familiarity with modern C++ and Julia;
- writing some tools to (at least partially) automate the generation of the
  Julia bindings, documentation, and tests;
- making design decisions about how to map C++ idioms to Julia.

### 2. Formal verification of Knuth-Bendix and Todd-Coxeter

A computer algebra system may produce an answer, but how much confidence can we
have that it is correct? We might compute the same solution using two different
algorithms, if they match, then we have higher confidence! This project is to
provide alternate implementations of some key parts of the [Knuth-Bendix][] and
[Todd-Coxeter][] algorithms in [libsemigroups][] to permit the generation of a
formal proof certificate in [rocq][] or [lean][] that _proves_ with 100%
certainty that the output is correct.

This project may involve:

- some familiarity with modern C++ and [rocq][] or [lean][];
- implementing a logged rewriter in modern C++;
- understanding the mathematics behind [Knuth-Bendix][] and
  [Todd-Coxeter][] as applied to finitely presented semigroups and monoids.

### 3. AI for auto-tuning undecidable problems

In this project we aim to use techniques from AI and machine learning to guide
computations related to undecidable problems. If a group or semigroup is
defined by a presentation, then a classical undecidable problem is whether or
not that semigroup is finite. Two key algorithms for attempting to determine
whether or not a finitely presented semigroup is finite are the
[Knuth-Bendix][] and [Todd-Coxeter][] algorithms. [Todd-Coxeter][] in
particular terminates if and only if the semigroup is finite.

This project may involve:

- extensive testing of the existing implementation of [Knuth-Bendix][] and
  [Todd-Coxeter][] in [libsemigroups][];
- figuring out what AI tools and/or machine learning techniques might be usable
  for this purpose.
- implementing these techniques in modern C++.

### 4. High-performance tropical algebra library

There are a number of high-performance linear algebra packages for linear
algebra involving matrix and vector manipulation over fields (usually the real
numbers or finite fields. Some well-known examples among many others are:
[LinBox](https://linalg.org) and [Eigen](https://libeigen.gitlab.io). This
project will involve implementing (at least some of) the
[BLAS](https://en.wikipedia.org/wiki/Basic_Linear_Algebra_Subprograms)
specification for matrices and vectors of [tropical
semirings](https://en.wikipedia.org/wiki/Tropical_semiring) in modern C++.
Tropical semirings, often using min-plus or max-plus algebra, are powerful
tools for solving optimization, scheduling, and combinatorial problems by
replacing addition/multiplication with minimum/maximum/summation. As such a
high-performance library implementing linear algebra over tropical semirings is
likely to be widely applicable.

This project may involve:

- developing some familiarity with linear algebra over tropical semirings;
- implementing low-level high-performance SIMD accelerated linear algebra over
  tropical semirings;
- developing a new C++ library (build system, documentation, testing framework).

### 5. Computing congruences of finite inverse semigroups

In the paper

- "Computing congruences of finite inverse semigroups" by L. Elliott, A.
  Levine, and J. D. Mitchell [https://arxiv.org/abs/2406.09281][]

the authors present a novel algorithm for
computing a congruence on an inverse semigroup from a collection of generating
pairs. This algorithm uses a myriad of techniques from the theories of groups,
automata, and inverse semigroups. An initial implementation of this algorithm
outperforms existing implementations by several orders of magnitude. In this
project, you would implement this algorithm either in [GAP package
Semigroups][] or within the C++ library [libsemigroups][].

This project may involve:

- developing some familiarity with the theory of inverse semigroups;
- implementing the algorithms described in
  [https://arxiv.org/abs/2406.09281][];
- thoroughly testing and documenting the implementation.

<!-- Cuttings algorithm-->

<!-- Parallelising computer algebra -->

### 6. Improving errors and their messages in GAP

[GAP][] is a system for computational discrete algebra, with particular
emphasis on Computational Group Theory. [GAP][] provides a programming
language, a library of thousands of functions implementing algebraic algorithms
written in the [GAP][] language as well as large data libraries of algebraic
objects.

The aim of this project is to improve errors and their messages in [GAP][] in
something of the same spirit as those introduced in [Python
3.13](https://docs.python.org/3/whatsnew/3.13.html#improved-error-messages).

This project may involve:

- doing a wide-scale review of error messages in the [GAP][] library;
- identification of error messages that can be improved;
- standardisation of error messages across the [GAP][] library;
- liaising with code owners to effect any changes;
- improvements to the error message infrastructure in [GAP][] arising from the
  above.

<!-- ### Nielsen-Schreier free bases

Implement an algorithm for finding the free basis of a finitely generated
subgroup of a free group (i.e. implement a proof of the Nielsen-Schreier
theorem for finitely generated subgroups) (this is pretty nice actually and
uses a similar word graph folding method to what Stephen's algorithm does);
-->

### 7. Free bands

In the paper:

- "Polynomial time multiplication and normal forms in free band" by R.
  Cirpons and J. D. Mitchell [https://doi.org/10.1016/j.tcs.2023.113783](https://doi.org/10.1016/j.tcs.2023.113783)

the authors present efficient computational solutions to the problems of
checking equality, performing multiplication, and computing minimal
representatives of elements of free bands. A reference implementation of the
algorithms from this paper is given in
[https://doi.org/10.5281/zenodo.7071676](https://doi.org/10.5281/zenodo.7071676).
In this project, the reference implementation would be re-implemented in modern
C++ as part of [libsemigroups][]; and integrating subsemigroups of free bands
and their quotients into the framework established in [https://arxiv.org/abs/1510.01868](https://arxiv.org/abs/1510.01868).

This project may involve:

- object oriented programming in modern C++;
- some familiarity with automata and transducers;
- integrating the C++ code into [libsemigroups_pybind11][],
  [Semigroups.jl][], and [GAP package Semigroups][];

<!-- Morphocompletion for Knuth-Bendix

Implement the morphocompletion algorithm using the stop and reinitialize
method you mentioned before.

### High-performance finite state automata

Implement various algorithms for automata or incorporate a good enough
automata library. In particular things like efficient products of automata.

### Todd-Coxeter for varieties

Implement something like the Todd-Coxeter algorithm for varieties from my
thesis, either in full generality or for some specific classes (e.g. bands).
-->

[libsemigroups]: https://libsemigroups.github.io/libsemigroups/
[Semigroups.jl]: https://github.com/libsemigroups/Semigroups.jl
[GAP package Semigroups]: https://semigroups.github.io/Semigroups/
[libsemigroups_pybind11]: https://libsemigroups.github.io/libsemigroups_pybind11/
[rocq]: https://rocq-prover.org
[lean]: https://lean-lang.org
[Todd-Coxeter]: https://link.springer.com/article/10.1007/s00233-024-10431-z
[Knuth-Bendix]: https://en.wikipedia.org/wiki/Knuth–Bendix_completion_algorithm
[https://arxiv.org/abs/2406.09281]: https://arxiv.org/abs/2406.09281
[GAP]: https://www.gap-system.org

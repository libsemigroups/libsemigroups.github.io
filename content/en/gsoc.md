---
layout: "gsoc"
bgImage: "/images/smalloverlap_510x510.png"
lastmod: 2026-02-12
---

# GSoC 2026 in libsemigroups

{{< lastmod >}}

## Introduction

The [libsemigroups][] library for computational semigroup
theory contains efficient implementations of widely used and novel algorithms
in computational semigroup theory.
This library forms the core of the [GAP package Semigroups][] which is
used by researchers in semigroup theory for preliminary computational
explorations that motivate mathematical discoveries or for finding
counterexamples to conjectures.
[libsemigroups][] has also found applications in tooling for cryptography researchers and as
a computational oracle for mathematical formalization projects.

The [libsemigroups][] project focuses on efficiency and ease of use.
For the second goal, we maintain bindings for the libsemigroups library
in Python in the [libsemigroups_pybind11][] project and the 
[GAP package Semigroups][] which depends on [libsemigroups][]. There is
also an ongoing effort to provide Julia bindings as part of the
[Semigroups.jl][] project.

The development of [libsemigroups][] occurs primarily at the
[University of St Andrews](https://www.st-andrews.ac.uk/) with multiple
external collaborators, and we would like to welcome many more as part of 
the [Google summer of code](https://summerofcode.withgoogle.com/) program!
We believe it is a great opportunity for participants to contribute to an
open-source project in mathematics and gain insights into computational
semigroup theory.

## Project ideas

Below is a list of ideas for projects within the [libsemigroups][]
organization, along with potential mentors and a rough estimate of the length
and difficulty of the project.

| Contents    |
| ----------- |
| {{< toc >}} |

---

### 1. Julia bindings Semigroups.jl for libsemigroups

**Description**:
The goal of this project is to create functioning bindings of the
[libsemigroups][] library into Julia aspart of the [Semigroups.jl][] project.
The [libsemigroups_pybind11][] project implements something similar for Python.
The aim is for [Semigroups.jl][] to expose the low-level functionality of
[libsemigroups][] to be used as a foundation for a separate higher level
package. In particular, a longer term aim of this project is to replace the
kernel extension of the [GAP package Semigroups][] with [Semigroups.jl][].

**This project may involve**:

- writing tooling to (at least partially) automate the generation of the
  Julia bindings, documentation, and tests;
- making design decisions about how to map C++ idioms to Julia.

**Mentors**: [Joe Edwards][] and [James Mitchell][]

**Length**: 350h

**Difficulty**: Easy-Medium

**Prerequisites**: 

- some familiarity with modern C++ and Julia;

---

### 2. Formal verification of Knuth-Bendix and Todd-Coxeter

**Description**:
A computer algebra system may produce an answer, but how much confidence can we
have that it is correct? We might compute the same solution using two different
algorithms, if they match, then we have higher confidence. Another approach is to
use a [proof assistant](https://en.wikipedia.org/wiki/Proof_assistant) such as
[rocq][] or [lean][] to produce a formal proof of the result, however doing this
by hand is rather cumbersome and does not scale well. But of course, if the
underlying algorithm is correct, it should be possible to produce such proof
certificates automatically.

The aim of this project is to extend the existing implementation of the
[Knuth-Bendix][] and the [Todd-Coxeter][] algorithms in [libsemigroups][] to have
them return a trace of the decisions made during their runtime.
This trace can then be converted into a formal proof of correctness, as is done
for example in the [MonoidPresentation][] project in [rocq][].

**This project may involve**:
- implementing a logged rewriter in modern C++;
- understanding the mathematics behind [Knuth-Bendix][] and
  [Todd-Coxeter][] as applied to finitely presented semigroups and monoids.
- learning some aspects of formalized mathematics and proof assistants.

**Mentors**: [Reinis Cirpons][], [Joe Edwards][] and [Florent Hivert][]

**Length**: 175h or 350h

**Difficulty**: Medium-Hard

**Prerequisites**:

- some familiarity with abstract algebra;
- good grasp of modern C++.

---

### 3. AI for auto-tuning undecidable problems

**Description**:
The aim of this project is to use techniques from AI and machine learning to
guide computations related to undecidable problems. A classical undecidable
problem is the _semigroup finiteness problem_, which asks whether or not a
finite presentation defines a finite semigroup. There is no program that can
always answer this question in finite time, but there are several semidecision
algorithms, which will always give an answer if a semigroup is finite, but may
run forever on an infinite input.

Two key semidecision algorithms for the finiteness problem are the
[Knuth-Bendix][] and [Todd-Coxeter][] algorithms, both of which are implemented
in [libsemigroups][]. These algorithms have different trade-offs and often one
yields an answer to a particular question much faster than the other, but due to
the undecidable nature of the problem is it very hard to determine which algorithm
to apply first, or how long to wait before switching between them. Such situations
are very common in computational semigroup theory and we believe there is
potential to optimize the usage of these algorithms using a machine learning
based approach.

**This project may involve**:

- extensive testing of the existing implementation of [Knuth-Bendix][] and
  [Todd-Coxeter][] in [libsemigroups][];
- figuring out what AI tools and/or machine learning techniques might be usable
  for this purpose.
- implementing these techniques in modern C++.

**Mentors**: [James Mitchell][] and [Finn Smith][]

**Length**: 175h

**Difficulty**: Easy-Medium

**Prerequisites**:

- some familiarity with Python or modern C++;
- some familiarity with AI or machine learning.

---

### 4. High-performance tropical algebra library

**Description**:
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

**This project may involve**:

- learning about linear algebra over tropical semirings;
- implementing low-level high-performance SIMD accelerated linear algebra over
  tropical semirings;
- developing a new C++ library (build system, documentation, testing framework).

**Mentors**: [Florent Hivert][] and [Finn Smith][]

**Length**: 350h

**Difficulty**: Medium-Hard

**Prerequisites**: 

- some familiarity with linear algebra;
- mastery of modern C++;
- some familiarity with SIMD.

---

### 5. Computing congruences of finite inverse semigroups

**Description**:
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

**This project may involve**:

- developing some familiarity with the theory of inverse semigroups;
- implementing the algorithms described in
  [https://arxiv.org/abs/2406.09281][];
- thoroughly testing and documenting the implementation.

**Mentors**: [Reinis Cirpons][] and [James Mitchell][].

**Length**: 90h or 175h

**Difficulty**: Medium

**Prerequisites**: 

- some familiarity with modern C++ or GAP;
- good grasp of university level abstract algebra.

<!-- Cuttings algorithm-->

<!-- Parallelising computer algebra -->

---

### 6. Improving errors and their messages in GAP

[GAP][] is a system for computational discrete algebra, with particular
emphasis on Computational Group Theory. [GAP][] provides a programming
language, a library of thousands of functions implementing algebraic algorithms
written in the [GAP][] language as well as large data libraries of algebraic
objects.

The aim of this project is to improve errors and their messages in [GAP][] in
something of the same spirit as those introduced in [Python
3.13](https://docs.python.org/3/whatsnew/3.13.html#improved-error-messages).

**This project may involve**:

- doing a wide-scale review of error messages in the [GAP][] library;
- identification of error messages that can be improved;
- standardisation of error messages across the [GAP][] library;
- liaising with code owners to effect any changes;
- improvements to the error message infrastructure in [GAP][] arising from the
  above.

**Mentors**: [Joe Edwards][] and [Michael Young][]

**Length**: 90h or 175h

**Difficulty**: Easy

**Prerequisites**: 

- some familiarity with programming in general.

---

### 7. Nielsen-Schreier free bases

A first course in linear algebra proves that every subspace of a linear space
has a basis. There is an analogue of this statement for free groups, known as
the [Nielsen-Schreier theorem](https://en.wikipedia.org/wiki/Nielsen%E2%80%93Schreier_theorem), which
states that every subgroup of a free group has a basis. For finitely generated
subgroups, there exist rather constructive proofs, which lead to algorithms
for computing the basis explicitly, in the same way that Gaussian elimination
can be used to can be used to find the basis for a vector space.
The goal of this project would be to implement an algorithm for finding the
free basis of a finitely generated subgroup of a free group.

**This project may involve**:

- learning the theory behind the Nielsen-Schreier theorem;
- understanding the algorithmic aspects of certain proofs;
- implementing an algorithm for the Nielsen-Schreier theorem in C++.

**Mentors**: [Reinis Cirpons][]

**Length**: 175h

**Difficulty**: Easy-Medium

**Prerequisites**: 

- some familiarity with abstract algebra;
- some familiarity with modern C++.

---

### 8. Free bands

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
and subsemigroups into the framework established in [https://arxiv.org/abs/1510.01868](https://arxiv.org/abs/1510.01868).

**This project may involve**:

- learning the theory behind free bands;
- object oriented programming in modern C++;
- integrating the C++ code into [libsemigroups_pybind11][],
  [Semigroups.jl][], and [GAP package Semigroups][].

**Mentors**: [Reinis Cirpons][] and [James Mitchell][]

**Length**: 350h

**Difficulty**: Medium-Hard

**Prerequisites**: 

- good grasp of abstract algebra;
- some familiarity with automata and transducers;
- good grasp of modern C++.

---

### 9. Morphocompletion for Knuth-Bendix

[Finitely presented semigroups](https://en.wikipedia.org/wiki/Presentation_of_a_monoid)
are the basic objects of study in combinatorial semigroup theory.
Each finitely presented semigroup is given by specifying an _alphabet_ together
with a set of equations that hold for some words over this alphabet, called the
_relations_. The elements of this semigroup are words over the alphabet, which
are compared by using the relations. In general equality in such a semigroup
is _undecidable_!

The [Knuth-Bendix][] algorithm attempts to solve this issue by orienting and
extending the set of relations such that there is a straightforward method for
checking equality. Since the underlying problem is undecidable, the algorithm
does not necessarily terminate with respect to a given presentation.
To make matters worse, it may sometimes be necessary to increase the alphabet
by replacing certain words with new letters to make the Knuth-Bendix procedure
terminate when it otherwise wouldn't. One approach to doing this is the
_morphocompletion_ procedure developed in

- "Morphocompletion for one-relation monoids" by J. Pedersen
  [https://link.springer.com/chapter/10.1007/3-540-51081-8_141](https://link.springer.com/chapter/10.1007/3-540-51081-8_141)

Roughly speaking, the morphocompletion procedure consists of repeatedly running
the Knuth-Bendix algorithm for a certain number of steps, picking some number
of subwords to replace by letters according to some heuristic such as the
frequency they occur with.

The goal of this project would be to produce an implementation of the
morphocompletion procedure in C++ in the [libsemigroups][] library or
in Python as part of the [libsemigroups_pybind11][] library. As the
procedure depends on various parameters, a further goal for the project
would consist of fine-tuning these parameters to improve performance.

**This project may involve**:

- learning the theory behind the Knuth-Bendix algorithm;
- object oriented programming in modern C++;
- implementing functions relating to word statistics;
- fine-tuning algorithm performance by adjusting algorithm parameters.

**Mentor**: [Joe Edwards][]

**Length**: 90h

**Difficulty**: Easy

**Prerequisites**:

- some familiarity with modern C++ or Python.

<!--
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
[MonoidPresentation]: https://github.com/hivert/MonoidPresentation
[Reinis Cirpons]: https://reinisc.id.lv
[Joe Edwards]: http://joseph-edwards.github.io/
[Florent Hivert]: https://www.lri.fr/~hivert/
[James Mitchell]: https://jdbm.me/
[Finn Smith]: https://flsmith.github.io/
[Michael Young]: https://myoung.uk/

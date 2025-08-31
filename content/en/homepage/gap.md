---
title: "GAP"
header_menu_title: "GAP"
navigation_menu_title: "GAP"
weight: 3
header_menu: true
---

[libsemigroups][] is the workhorse of the [GAP][] package [Semigroups][]
performing fundamental computations for finite and fintely presented semigroups
and monoids. Many of these beat the corresponding methods in the [GAP][]
library, despite [libsemigroups][] not having any optimisations specific to
groups.

```julia
F := FreeGroup(11);;
R := [];;
for i in [1 .. 11] do
  Add(R, [F.(i) ^ 2, One(F)]);
od;
for i in [1 .. 10] do
  Add(R, [F.(i) * F.(i + 1) * F.(i), F.(i + 1) * F.(i) * F.(i + 1)]);
od;
for i in [1 .. 9] do
  for j in [i + 2 .. 11] do
    Add(R, [F.(i) * F.(j), F.(j) * F.(i)]);
  od;
od;
G := F / R;
Size(G); # runs forever
```

But with the [Semigroups][] package loaded:

```julia
F := FreeMonoid(11);;
R := [];;
for i in [1 .. 11] do
  Add(R, [F.(i) ^ 2, One(F)]);
od;
for i in [1 .. 10] do
  Add(R, [F.(i) * F.(i + 1) * F.(i), F.(i + 1) * F.(i) * F.(i + 1)]);
od;
for i in [1 .. 9] do
  for j in [i + 2 .. 11] do
    Add(R, [F.(i) * F.(j), F.(j) * F.(i)]);
  od;
od;
G := F / R;
Size(G);  # 479001600
time; # 60
```

[libsemigroups]: https://libsemigroups.github.io/libsemigroups/
[GAP]: https://www.gap-system.org
[Semigroups]: https://semigroups.github.io

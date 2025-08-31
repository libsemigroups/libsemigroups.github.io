---
title: "Python"
header_menu_title: "Python"
navigation_menu_title: "Python"
weight: 4
header_menu: true
---

[libsemigroups][] is available to use directly in [Python][] via the package
[libsemigroups_pybind11][]. Repeating the example in the [GAP][] section above:

```python
from libsemigroups_pybind11 import KnuthBendix, congruence_kind
from libsemigroups_pybind11.presentation import examples
p = examples.symmetric_group_Moo97_a(12)
kb = KnuthBendix(congruence_kind.twosided, p)
kb.number_of_classes() # returns math.factorial(12)
```

Almost every feature of [libsemigroups][] is available in
[libsemigroups_pybind11][].

[libsemigroups]: https://libsemigroups.github.io/libsemigroups/
[libsemigroups_pybind11]: https://libsemigroups.github.io/libsemigroups_pybind11
[GAP]: https://www.gap-system.org
[Python]: https://python.org

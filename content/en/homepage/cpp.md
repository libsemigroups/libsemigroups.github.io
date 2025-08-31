---
title: "C/C++"
header_menu_title: "C/C++"
navigation_menu_title: "C/C++"
weight: 2
header_menu: true
---

[libsemigroups][] is a modern open source C++17 library designed to be:

- **state of the art**: the mathematical underpinnings of the algorithms
  in [libsemigroups][] use the current state of the art;
- **extensible**: several of the implementations in [libsemigroups][] are generic
  and easily adaptable to user-defined types;
- **adaptable**: the behaviour the algorithms implemented in [libsemigroups][]
  can be fine-tuned via many settings, and used interactively via the
  functions;
- **easy to use**: converting between different types of [libsemigroups][]
  objects is easy; there are many helper functions to streamline common tasks;
  high quality exception messages are implemented throughout the code base
  (although you don't have to use these if you don't want to); long running
  algorithms can provide detailed feedback on their progress; many data
  structures can be visualised; and there are hundreds of examples.
- **fast**: [libsemigroups][] is designed with performance in mind; several
  classes implement parallel algorithms; we provide some "winner takes all"
  mechanisms for running algorithms concurrently; and there are `_no_checks`
  versions of most functions if performance is critical.

[libsemigroups]: https://libsemigroups.github.io/libsemigroups/

# Learn Fatal and Meta-programming by example
This directory contains a set of lessons aimed at teaching the basics of meta-programming in C++.

The lessons gradually introduce idioms to better use Fatal when writing software.

Lessons source code is self-contained, presenting a full textual explanation of the lesson itself.

The output of the lessons is also self-contained, presenting the full textual explanation and source code.

Lessons can be followed by reading the source code, the lesson's output, or better yet: both.

At this point only a few lessons are available. Stay tuned for updates.


## Existing lessons
Fundamentals of metaprogramming:

- [1.0: Representing variables](1.0-variables.cpp)
- [1.1: Representing values](1.0-values.cpp)
- [1.2: Metafunctions](1.0-metafunctions.cpp)


## Lessons on the way
- Variadics
- Higher-order metafunctions
- SFINAE
- Compile-time assertions
- Compile-time lists
- Compile-time strings
- Compile-time prefix trees and efficient string matching
- Examples of how to use metaprogramming for real world applications


## Try it online
These lessons can be [tried online](http://abel.web.elte.hu/shell/metashell) using [Metashell](https://github.com/sabel83/metashell).

Metashell allows you to easily inspect the type of an alias. Whenever you encounter `TYPE(T)` in a lesson, you can simply type `T` instead to print the type represented by it:

```
> using type = std::integral_constant<std::size_t, 42>;
> type
std::integral_constant<std::size_t, 42>
```

Here's an example of how to follow a lesson in Metashell (use a trailing backslash `\` for multi-line statements):

```
> #include <fatal/lesson/lesson.h>
> template <typename T, T... Values> \
...> struct sequence_1 {};
> using mp = sequence_1<std::uint32_t, 3, 7, 31, 127, 8191, 131071, 524287>;
> mp
sequence_1<std::uint32_t, 3, 7, 31, 127, 8191, 131071, 524287>
```

Due to its REPL nature, Metashell provides a much more dynamic environment than the text editor + compiler combo, highly recommended for learning.


## Requirements for lessons
A compliant C++11 compiler. Currently tested under Clang {3.4, 3.5, 3.6, 3.7, 3.8} and GCC {4.8, 4.9, 5.2}.

There are no other external dependencies.


## Building lessons
```sh
$ clang++ -std=c++11 -I path/to/fatal \
  -o path/to/output/binary lesson/lesson_filename.cpp
```
or
```sh
$ g++ -std=c++11 -I path/to/fatal \
  -o path/to/output/binary lesson/lesson_filename.cpp
```
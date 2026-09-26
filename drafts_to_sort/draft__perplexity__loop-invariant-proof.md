<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">

<!-- 🖼️ Site Logo -->
!Site Logo{height=32}

<!-- 📝 Title -->
# HOW-TO: 📘 C++ Array-Bound Reasoning and Loop Correctness

**Version:** 1.0

> Optimized for: VSCode on Windows 11 + Git Bash (SSH)

<!-- 🧭 Navigation -->
### [🏚️ Home](../README.md) | [📁 HOW-TO](index.md)

<!-- 👤 Metadata -->
| **Author**: | Eric L. Hepperle |
| --- | --- |
| **Date Created**: | 2026-09-26 |
| **Date Updated**: | 2026-09-26 |
| **AI Assistant**: | Perplexity |

***

<!-- SECTION: Tags -->
<section id="sec-tags">

## 🏷️ Tags

- C++ Arrays
- Loop Invariants
- Bounds Safety
- Off-By-One Errors
- Defensive Programming

</section>

***

## 📌 Overview

Array-bound reasoning is the practice of logically verifying that every array index used by a C++ program remains within the array’s valid index range. It is not a widely standardized or commonly searchable technical phrase by itself. It is best understood as an instructor-friendly label for several established concepts:

- Array bounds checking
- Bounds safety
- Out-of-bounds access
- Off-by-one errors
- Loop invariants
- Proof of program correctness

For an array with `n` elements, the only valid indexes are:

\[
0 \leq index < n
\]

This means the first element is at index `0`, and the final valid element is at index `n - 1`.

In C++, built-in array indexing does not automatically stop a program from accessing an invalid location. Reading or writing outside an array’s boundaries is undefined behavior. The result may appear to work, produce incorrect data, corrupt nearby memory, crash, or create a security weakness. [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) and CERT-oriented guidance therefore emphasize range checking and bounds-safe representations where practical. [CERT C++ ARR30-C Summary](https://www.mathworks.com/help/bugfinder/ref/certcarr30c.html)

> **Core idea:** Treat an array index like an algebraic variable. Determine its smallest and largest possible values, then prove that each possible value is a legal index.

***

<details>
<summary><strong>🧭 Table of Contents</strong></summary>

- [HOW-TO: 📘 C++ Array-Bound Reasoning and Loop Correctness](#how-to--c-array-bound-reasoning-and-loop-correctness)
    - [🏚️ Home | 📁 HOW-TO](#️-home---how-to)
  - [🏷️ Tags](#️-tags)
  - [📌 Overview](#-overview)
  - [🧠 Terminology](#-terminology)
    - [Array Bounds](#array-bounds)
    - [Array-Bound Reasoning](#array-bound-reasoning)
    - [Systems Programming](#systems-programming)
    - [Loop Invariant](#loop-invariant)
  - [🧮 Proving an Array Loop Safe](#-proving-an-array-loop-safe)
    - [Valid Index Rule](#valid-index-rule)
    - [Safe Loop Example](#safe-loop-example)
      - [Reasoning / Proof Work](#reasoning--proof-work)
    - [Unsafe Loop Example](#unsafe-loop-example)
    - [Derived Index Example](#derived-index-example)
  - [⚙️ Why This Matters](#️-why-this-matters)
    - [Systems-Programming Connection](#systems-programming-connection)
  - [🤖 Verifying AI-Generated Indexing](#-verifying-ai-generated-indexing)
    - [Verification Checklist](#verification-checklist)
    - [Boundary Cases to Test](#boundary-cases-to-test)
    - [Helpful C++ Practices](#helpful-c-practices)
  - [🎥 Video Learning Paths](#-video-learning-paths)
    - [Beginner C++ Array Safety](#beginner-c-array-safety)
    - [Mathematical Loop Correctness](#mathematical-loop-correctness)
    - [Better Search Phrases](#better-search-phrases)
  - [📚 References / See Also](#-references--see-also)
    - [C++ Bounds Safety](#c-bounds-safety)
    - [Loop Correctness and Invariants](#loop-correctness-and-invariants)
    - [Native Collapsible HTML](#native-collapsible-html)
  - [✅ Revision History](#-revision-history)

</details>

***

## 🧠 Terminology

### Array Bounds

An array’s **bounds** are the legal limits of its indexes.

```cpp
int scores [willcrichton](https://willcrichton.net/notes/systems-programming/) = {90, 80, 70, 60, 50};
```

This array holds five elements. Its legal indexes are:

```text
scores[0]
scores [en.wikipedia](https://en.wikipedia.org/wiki/Systems_programming)
scores [coursera](https://www.coursera.org/in/articles/system-programming)
scores [en.cppreference](https://en.cppreference.com/cpp/language/array)
scores [learn.microsoft](https://learn.microsoft.com/en-us/cpp/cpp/arrays-cpp?view=msvc-170)
```

The expression `scores [willcrichton](https://willcrichton.net/notes/systems-programming/)` is invalid because it attempts to access a sixth element that does not exist.

| Array Size | First Valid Index | Last Valid Index | Valid Index Rule |
| --- | --- | --- | --- |
| `5` | `0` | `4` | `0 <= index < 5` |
| `n` | `0` | `n - 1` | `0 <= index < n` |

### Array-Bound Reasoning

**Array-bound reasoning** is an informal teaching phrase for proving that each index expression used in a program remains within its array’s legal limits.

The exact phrase is not a common standardized term in C++ documentation, textbooks, or search results. More common terms include:

- Array bounds checking
- Bounds safety
- Range checking
- Invalid array subscript
- Out-of-bounds access
- Off-by-one error
- Loop invariant
- Proof of correctness

The skill is real even when the wording varies. A programmer should be able to explain why every possible access—such as `values[i]`, `values[i + 1]`, or `grid[row][column]`—is valid before relying on it.

### Systems Programming

**Systems programming** is programming that works closely with computer resources and infrastructure, including:

- Operating systems
- Memory management
- Hardware interfaces
- File systems
- Network services
- Device drivers
- Embedded systems
- Performance-sensitive software components

Array-bound reasoning matters especially in systems programming because an indexing mistake can affect memory directly. C++ is frequently used for performance-sensitive and systems-level work, where the programmer often has significant responsibility for memory safety.

### Loop Invariant

A **loop invariant** is a statement that remains true at the beginning of every loop iteration. Programmers and computer scientists use loop invariants to prove that a loop behaves correctly.

For an array-processing loop, one useful invariant may be:

> At the beginning of every iteration, `i` is a valid index for the element the loop is about to access.

A formal proof commonly has three parts:

- **Initialization**: Show the claim is true before the first iteration
- **Maintenance**: Show one valid iteration preserves the claim for the next iteration
- **Termination**: Show that when the loop stops, the claim and stopping condition establish the desired result

***

## 🧮 Proving an Array Loop Safe

### Valid Index Rule

For an array containing `n` elements:

```cpp
int values[n];
```

the required condition for any index is:

\[
0 \leq index < n
\]

When reviewing code, do not merely ask whether a loop “looks right.” Determine the full range of possible values for every index expression, then compare that range with the legal array bounds.

### Safe Loop Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int values [willcrichton](https://willcrichton.net/notes/systems-programming/) = {10, 20, 30, 40, 50};

    for (int i = 0; i < 5; ++i) {
        cout << values[i] << '\n';
    }

    return 0;
}
```

#### Reasoning / Proof Work

```text
Array size = 5

Valid indexes:
0 <= i < 5

Initial value:
i = 0

Loop condition:
i < 5

Possible values of i in the loop body:
0, 1, 2, 3, 4

Largest possible index:
4

Final valid index for a 5-element array:
5 - 1 = 4

Conclusion:
Every access to values[i] is within the valid range.
```

In algebra-style notation:

\[
0 \leq i < 5
\]

Therefore:

\[
i \in \{0, 1, 2, 3, 4\}
\]

Since `values[0]` through `values [learn.microsoft](https://learn.microsoft.com/en-us/cpp/cpp/arrays-cpp?view=msvc-170)` are valid, `values[i]` is safe for each loop iteration.

### Unsafe Loop Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int values [willcrichton](https://willcrichton.net/notes/systems-programming/) = {10, 20, 30, 40, 50};

    for (int i = 0; i <= 5; ++i) {
        cout << values[i] << '\n';
    }

    return 0;
}
```

This loop is unsafe because `i <= 5` permits `i` to become `5`.

```text
Array size = 5

Valid indexes:
0 <= i < 5

Actual loop condition:
i <= 5

Possible values of i in the loop body:
0, 1, 2, 3, 4, 5

Problem:
values [willcrichton](https://willcrichton.net/notes/systems-programming/) is outside the array.

Conclusion:
The code performs an out-of-bounds access.
```

The required range and the range actually allowed by the loop are different:

\[
\text{Required: } 0 \leq i < 5
\]

\[
\text{Actual: } 0 \leq i \leq 5
\]

The error is an **off-by-one error**. The code allows one more value than the array permits.

### Derived Index Example

Programmers must prove the safety of the full index expression, not just the loop variable.

```cpp
#include <iostream>
using namespace std;

int main() {
    int values [willcrichton](https://willcrichton.net/notes/systems-programming/) = {10, 20, 30, 40, 50};

    for (int i = 0; i < 4; ++i) {
        cout << values[i + 1] << '\n';
    }

    return 0;
}
```

Here, the accessed index is `i + 1`, not simply `i`.

```text
Array size = 5

Valid indexes:
0 <= index < 5

Loop condition:
0 <= i < 4

Index expression:
index = i + 1

Add 1 to the inequality:
1 <= i + 1 < 5

Conclusion:
i + 1 can only be 1, 2, 3, or 4.
All of those are valid indexes.
```

In mathematical notation:

\[
0 \leq i < 4
\]

\[
1 \leq i + 1 < 5
\]

Therefore, `values[i + 1]` stays within valid indexes `1` through `4`.

By contrast, this version is unsafe:

```cpp
for (int i = 0; i < 5; ++i) {
    cout << values[i + 1] << '\n';
}
```

When `i` becomes `4`, the code accesses `values [willcrichton](https://willcrichton.net/notes/systems-programming/)`, which is invalid.

***

## ⚙️ Why This Matters

C++ permits direct array access using the subscript operator:

```cpp
values[index]
```

For built-in arrays and ordinary `operator[]` access, C++ does not automatically guarantee runtime bounds checking. An out-of-bounds read or write is undefined behavior. Its observable result is not reliable or predictable.

Possible outcomes include:

- Seemingly correct output during one test run
- Incorrect values read from unrelated memory
- Corruption of a nearby variable
- A crash now or later in program execution
- A security vulnerability
- Different behavior when compiled with different optimization settings

The practical lesson is that code which “did not crash” is not necessarily correct. A bad index remains bad even if the program appears to work.

The [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) recommend approaches such as representing array ranges explicitly and using bounds-aware access patterns where appropriate. The guidance specifically identifies pointer arithmetic and array indexing as common sources of bounds-safety problems.

### Systems-Programming Connection

Array-bound reasoning is a systems-programming concern because systems software commonly manages data buffers, files, network packets, device data, memory regions, and operating-system resources. In these contexts, one wrong index can impact program correctness, reliability, data integrity, or security.

However, the skill is not limited to systems programming. It also applies to beginner C++ programs, business applications, game development, web back ends, scientific software, and any program that uses arrays, strings, vectors, matrices, or buffers.

***

## 🤖 Verifying AI-Generated Indexing

Treat AI-generated C++ indexing code as a draft that must be checked—not as proof that the code is safe.

### Verification Checklist

- Identify the actual number of elements in the array, vector, string, or matrix dimension
- Write the valid index rule: `0 <= index < size`
- Determine the smallest and largest possible value of each loop variable
- Check every index expression, including `i + 1`, `i - 1`, `count - 1`, and `row * columns + column`
- Confirm that a loop condition uses `< size` rather than `<= size` when indexing begins at zero
- Check empty-container behavior before using expressions such as `size - 1`
- Check one-element behavior, since it exposes assumptions about a “next” or “previous” element
- Verify nested indexes independently for two-dimensional arrays or matrices
- Compile with warnings enabled
- Test boundary and out-of-range cases intentionally
- Use runtime checking and diagnostic tools when available

### Boundary Cases to Test

For an array or container with valid indexes `0` through `n - 1`, test these conditions:

- Empty input or size `0`
- One-element input or size `1`
- First valid index: `0`
- Last valid index: `n - 1`
- First invalid high index: `n`
- A negative index when signed integer input is possible
- An index derived from arithmetic, such as `i + 1`
- The final loop iteration

### Helpful C++ Practices

Use a container that knows its own size when possible:

```cpp
#include <array>
#include <iostream>
using namespace std;

int main() {
    array<int, 5> values = {10, 20, 30, 40, 50};

    for (size_t i = 0; i < values.size(); ++i) {
        cout << values[i] << '\n';
    }

    return 0;
}
```

During learning and debugging, checked access can help expose invalid indexes:

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> values = {10, 20, 30, 40, 50};

    cout << values.at(4) << '\n';

    return 0;
}
```

`std::vector::at()` performs bounds checking and reports an out-of-range access rather than silently proceeding with ordinary unchecked subscript behavior.

For GCC or Clang development builds, sanitizers can help identify memory and undefined-behavior defects:

```bash
g++ -std=c++17 -Wall -Wextra -fsanitize=address,undefined program.cpp -o program
```

Compiler and static-analysis tools can also flag certain suspicious array-index patterns. For example, [Clang-Tidy’s `cppcoreguidelines-pro-bounds-constant-array-index` check](https://clang.llvm.org/extra/clang-tidy/checks/cppcoreguidelines/pro-bounds-constant-array-index.html) is part of the C++ Core Guidelines bounds-safety profile.

> **Important:** Tools are helpful, but they do not replace reasoning. The programmer still needs to understand the legal index range and prove that each access expression stays inside it.

***

## 🎥 Video Learning Paths

### Beginner C++ Array Safety

- [Bounds Checking and Off-by-One Errors in C++ Arrays](https://www.youtube.com/watch?v=e_kFg_Ep3EQ)
  - Focus: C++ array limits, bounds checking, and off-by-one mistakes
  - Best first video for understanding why `i < size` differs from `i <= size`

- [Common Array Errors — C++ Arrays for Beginners, Part 4](https://www.youtube.com/watch?v=yucYw4Tnh3M)
  - Focus: Invalid array subscripts and common beginner errors
  - Best follow-up video for reinforcing zero-based indexes and legal array limits

### Mathematical Loop Correctness

- [Loop Invariant Proofs — Proofs, Part 1](https://www.youtube.com/watch?v=_maJ4Qy7Q0E)
  - Focus: Formal proof of loop correctness through loop invariants
  - Best video for the “show your work like algebra” part of array-bound reasoning

- [How Loop Invariants Guarantee Correctness in Array Sum](https://www.youtube.com/watch?v=pegJM-sqIu4)
  - Focus: Applying loop-invariant reasoning to array algorithms
  - Best connection between formal proof methods and practical array-processing tasks

- [Loop Invariants — Key Coding Interview Concept](https://www.youtube.com/watch?v=95bFFw7m-c4)
  - Focus: A practical explanation of facts that remain true as a loop runs
  - Best after learning the basic terminology

- [Minimum Algorithm — Loop Invariant — Proof of Correctness](https://www.youtube.com/watch?v=ndFArXAsPsc)
  - Focus: Proving correctness for an algorithm that searches an array for a minimum value
  - Best intermediate exercise after understanding basic traversals

### Better Search Phrases

Use the following terms rather than the uncommon phrase `array-bound reasoning`:

```text
C++ arrays off by one error
C++ array index out of bounds
C++ invalid array subscript for loop
C++ array traversal loop
loop invariant beginners
loop invariant proof of correctness
proof a for loop is correct
array traversal loop invariant
boundary value analysis C++ arrays
```

***

## 📚 References / See Also

### C++ Bounds Safety

- [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)
- [CERT C++ ARR30-C Summary: Do Not Form or Use Out-of-Bounds Pointers or Array Subscripts](https://www.mathworks.com/help/bugfinder/ref/certcarr30c.html)
- [Clang-Tidy: `cppcoreguidelines-pro-bounds-constant-array-index`](https://clang.llvm.org/extra/clang-tidy/checks/cppcoreguidelines/pro-bounds-constant-array-index.html)
- [C++ Reference: Array Declaration](https://en.cppreference.com/w/cpp/language/array)
- [Microsoft Learn: Arrays in C++](https://learn.microsoft.com/en-us/cpp/cpp/arrays-cpp?view=msvc-170)

### Loop Correctness and Invariants

- [Loop Invariant Proofs — Proofs, Part 1](https://www.youtube.com/watch?v=_maJ4Qy7Q0E)
- [How Loop Invariants Guarantee Correctness in Array Sum](https://www.youtube.com/watch?v=pegJM-sqIu4)
- [Minimum Algorithm — Loop Invariant — Proof of Correctness](https://www.youtube.com/watch?v=ndFArXAsPsc)
- [Basics of Specification and Verification: Lecture 1, Loop Invariants](https://www.youtube.com/watch?v=J0FGb6PyO_k)

### Native Collapsible HTML

- [MDN Web Docs: `<details>` HTML Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/details)
- [MDN Web Docs: `<summary>` HTML Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/summary)

The native HTML `<details>` and `<summary>` elements create a collapsible disclosure widget without JavaScript. Clicking the `<summary>` element opens or closes the parent `<details>` element. [MDN: `<details>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/details)

***

## ✅ Revision History

| Version | Date | Author | Changes Made |
| --- | --- | --- | --- |
| 1.00 | 2026-09-26 | Eric L. Hepperle | Initial draft created |
| 1.01 | -- | -- | -- |

---
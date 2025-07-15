# ft_printf

## 📘 Project Overview

**ft_printf** is a foundational C project from the 42 curriculum that requires recreating the versatile `printf()` function from the standard C library. This project introduces variadic functions and teaches you to handle variable numbers of arguments while building a well-structured and extensible codebase.

> **Disclaimer:**  
> This document is an unofficial summary written for educational and documentation purposes.  
> It is not affiliated with or endorsed by 42 or its partners.  
> All 42 students are responsible for adhering to the academic integrity policy.  
> You may **not** publish or share any part of the official subject PDF, evaluation scripts, or Moulinette content.

---

## Contents

- [Goals](#goals)
- [General Requirements](#general-requirements)
- [Mandatory Part](#mandatory-part)
- [Bonus Part](#bonus-part)
- [Submission Guidelines](#submission-guidelines)
- [Testing](#testing)

---

## Goals

- Implement a custom version of the `printf()` function.
- Learn to work with variadic functions in C.
- Understand format specifiers and string parsing.
- Master low-level output operations and number base conversions.
- Create a reusable library (`libftprintf.a`) for future 42 projects.

---

## General Requirements

- Written in **C**, following the **42 Norm**.
- No memory leaks or undefined behavior.
- Functions must not crash unexpectedly (segfaults, bus errors, double free).
- All files must compile with `-Wall -Wextra -Werror` using `cc`.
- Global variables are **forbidden**.
- Use `ar` to create the library (not `libtool`).
- `libftprintf.a` must be created at the **root** of the repository.
- External functions allowed: `malloc`, `free`, `write`, `va_start`, `va_arg`, `va_copy`, `va_end`.
- **Libft** is authorized and encouraged.

### Makefile

Must include rules:
- `$(NAME)`, `all`, `clean`, `fclean`, `re`
- `bonus` rule if implementing bonus functions

---

## Mandatory Part

### Function Prototype

```c
int ft_printf(const char *format, ...);
```

### Program Details

- **Program name:** `libftprintf.a`
- **Turn in files:** `Makefile`, `*.h`, `*/*.h`, `*.c`, `*/*.c`
- **Description:** Write a library that contains `ft_printf()`, a function that mimics the original `printf()`

### Key Requirements

- **No buffer management** implementation required (unlike original `printf()`).
- Your function will be compared against the original `printf()`.
- Must handle the following conversions: `c` `s` `p` `d` `i` `u` `x` `X` `%`

### Format Specifiers

| Specifier | Description |
|-----------|-------------|
| `%c` | Prints a single character |
| `%s` | Prints a string (as defined by common C convention) |
| `%p` | Prints a `void *` pointer in hexadecimal format |
| `%d` | Prints a decimal (base 10) number |
| `%i` | Prints an integer in base 10 |
| `%u` | Prints an unsigned decimal (base 10) number |
| `%x` | Prints a number in hexadecimal (base 16) lowercase |
| `%X` | Prints a number in hexadecimal (base 16) uppercase |
| `%%` | Prints a percent sign |

### Implementation Notes

- Function must return the number of characters printed.
- Handle edge cases (NULL pointers, negative numbers, etc.).
- Proper handling of variadic arguments using `va_list` macros.

---

## Bonus Part

> **Important:** The bonus part will only be assessed if the mandatory part is **PERFECT**.  
> Perfect means the mandatory part has been integrally done and works without malfunctioning.

### Bonus Features

You don't have to implement all bonuses, but here are the available options:

#### Flag Management
- **Field width**: Minimum number of characters to print
- **Flags**: `-`, `0`, `.` and field minimum width under all conversions
- **Additional flags**: `#`, `+`, ` ` (space)

#### Flag Descriptions

| Flag | Description |
|------|-------------|
| `-` | Left-justify the result within the field width |
| `0` | Pad with zeros instead of spaces |
| `.` | Precision specifier |
| `#` | Alternative form (e.g., `0x` prefix for hex) |
| `+` | Always show sign for signed conversions |
| ` ` | Add a space before positive numbers |

### Bonus Implementation Tips

- Think about implementation from the start to avoid naive approaches.
- Consider creating a structure to store flags and formatting options.
- Bonus functions must be in `_bonus.{c/h}` files.

---

## Submission Guidelines

- Code must be submitted to the Git repository assigned by 42.
- Only the contents of the repository will be evaluated.
- Evaluation includes peer reviews and possible automated testing via **Deepthought**.
- If a norm or runtime error is found during evaluation, grading stops immediately.

---

## Testing

Even though not required, thorough testing is **highly recommended**.

### Recommended Testing Approach

1. **Basic functionality**: Test each format specifier individually
2. **Edge cases**: NULL pointers, zero values, maximum/minimum integers
3. **Comparison testing**: Compare output with original `printf()`
4. **Memory testing**: Check for leaks using tools like `valgrind`

### Example Test Cases

```c
// Basic tests
ft_printf("Character: %c\n", 'A');
ft_printf("String: %s\n", "Hello, World!");
ft_printf("Pointer: %p\n", &variable);
ft_printf("Decimal: %d\n", 42);
ft_printf("Hex lowercase: %x\n", 255);
ft_printf("Hex uppercase: %X\n", 255);
ft_printf("Percent: %%\n");

// Edge cases
ft_printf("NULL string: %s\n", NULL);
ft_printf("Zero: %d\n", 0);
ft_printf("Negative: %d\n", -42);
```

---

## Key Learning Objectives

- **Variadic Functions**: Understanding `va_list`, `va_start`, `va_arg`, `va_end`
- **String Parsing**: Analyzing format strings and extracting specifiers
- **Number Base Conversion**: Converting integers to different bases
- **Memory Management**: Proper allocation and deallocation
- **Code Architecture**: Building extensible and maintainable code

---

## Final Note

This project is excellent preparation for understanding how formatted output works in C.  
A solid implementation will serve you well in future 42 projects that require formatted output.  
Focus on creating clean, well-structured code that handles edge cases gracefully.

---

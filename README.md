# ft_printf

![42 Badge](https://img.shields.io/badge/42-ft__printf-brightgreen)
![C Badge](https://img.shields.io/badge/Language-C-blue)
![Status Badge](https://img.shields.io/badge/Status-Completed-success)

## Project Details

For full project requirements, see the [Subject File](./subject.md).

## What I Learned

Through this challenging project at 42 School, I developed advanced programming skills and deepened my understanding of:

- **Variadic functions** - Mastered va_list, va_start, va_arg, va_end for handling variable arguments
- **Format string parsing** - Built a robust parser to extract format specifiers and flags from complex strings
- **Flag-based formatting** - Implemented width, precision, and alignment flags for professional output formatting
- **Number base conversion** - Created efficient algorithms for decimal to hexadecimal conversion
- **Memory-efficient string handling** - Optimized string operations without buffer management overhead
- **Modular architecture design** - Structured code with clear separation between mandatory and bonus features
- **Complex conditional logic** - Handled intricate flag interactions and precedence rules
- **Performance optimization** - Balanced functionality with minimal memory allocation
- **Edge case management** - Robust handling of NULL pointers, zero values, and extreme inputs
- **Code extensibility** - Designed architecture that easily accommodates new format specifiers

This project significantly enhanced my understanding of low-level C programming, system calls, and the intricacies of formatted output that underpins much of C programming.

## About the Project

ft_printf is a complete reimplementation of the standard C library's printf() function, featuring both basic format specifiers and advanced formatting flags. It demonstrates mastery of variadic functions while providing a foundation for formatted output in future 42 projects.

The implementation is split into two versions:
- **Mandatory**: Core functionality with essential format specifiers
- **Bonus**: Advanced formatting with flags, width, and precision control

## Implementation Details

### Architecture Overview

The project uses a clean, modular design with separate implementations for mandatory and bonus features:

```
ft_printf/
├── mandatory/          # Core implementation
│   ├── include/        # Basic headers
│   └── src/           # Essential functions
└── bonus/             # Advanced implementation  
    ├── include/       # Extended headers with flags
    └── src/           # Full-featured functions
```

### Core Format Specifiers (Mandatory)

| Specifier | Function | Description |
|-----------|----------|-------------|
| `%c` | ft_putchar_count | Single character output |
| `%s` | ft_putstr_count | String output with NULL safety |
| `%p` | ft_putptr_count | Pointer address in hexadecimal |
| `%d`/`%i` | ft_putnbr_count | Signed decimal integers |
| `%u` | ft_putnbr_unsigned_count | Unsigned decimal integers |
| `%x` | ft_put_hex_count | Lowercase hexadecimal |
| `%X` | ft_put_hex_count | Uppercase hexadecimal |
| `%%` | ft_putchar_count | Literal percent sign |

### Advanced Formatting (Bonus)

The bonus implementation features a sophisticated flag system using a dedicated structure:

```c
typedef struct s_flags
{
    int minus;      // '-' Left justify
    int zero;       // '0' Zero padding  
    int cardinal;   // '#' Alternative form
    int space;      // ' ' Space before positive numbers
    int plus;       // '+' Force sign display
    int width;      // Minimum field width
    int precision;  // Precision for numbers/strings
    int hex_caps;   // Uppercase/lowercase hex control
} t_flags;
```

#### Flag Functionality

| Flag | Purpose | Example |
|------|---------|---------|
| `-` | Left-align within field width | `"%-10d"` |
| `0` | Pad with zeros instead of spaces | `"%08d"` |
| `#` | Alternative form (0x prefix for hex) | `"%#x"` |
| `+` | Always show sign for signed numbers | `"%+d"` |
| ` ` | Space prefix for positive numbers | `"% d"` |
| `.n` | Precision control | `"%.2f"` concept |
| `width` | Minimum field width | `"%10d"` |

### Key Technical Features

- **Smart flag parsing** - Handles complex flag combinations with proper precedence
- **Efficient number conversion** - Custom algorithms for base conversion without standard library dependencies
- **Memory management** - Strategic use of dynamic allocation only where necessary
- **Error resilience** - Graceful handling of invalid inputs and edge cases
- **Performance optimization** - Single-pass parsing with minimal function call overhead

## Usage

```bash
# Compile mandatory version
make

# Compile with bonus features
make bonus

# Clean object files
make clean

# Remove all generated files
make fclean

# Rebuild project
make re
```

## Integration Example

```c
#include "ft_printf.h"

int main(void)
{
    int count;
    
    // Basic usage
    count = ft_printf("Hello, %s!\n", "World");
    ft_printf("Characters printed: %d\n", count);
    
    // Numeric formatting
    ft_printf("Decimal: %d, Hex: %x, Unsigned: %u\n", -42, 255, 3000000000U);
    
    // Pointer handling
    int var = 42;
    ft_printf("Address: %p\n", &var);
    
    // Bonus formatting (if compiled with bonus)
    ft_printf("Padded: |%10d|\n", 42);           // Right-aligned
    ft_printf("Zero-padded: |%08d|\n", 42);      // Zero padding
    ft_printf("Left-aligned: |%-10d|\n", 42);    // Left-aligned
    ft_printf("With sign: |%+d|\n", 42);         // Force sign
    ft_printf("Hex with prefix: |%#x|\n", 255);  // Alternative form
    
    return (0);
}
```

## Technical Challenges Overcome

- **Complex flag interaction logic** - Implementing proper precedence when multiple flags conflict (e.g., `-` overrides `0`)
- **Precision vs width distinction** - Correctly handling the subtle differences between field width and precision
- **Memory optimization** - Minimizing allocations while maintaining functionality, especially for number-to-string conversion
- **Format string state management** - Tracking parser state through complex format specifications
- **Cross-platform compatibility** - Ensuring consistent behavior across different systems and architectures
- **Variadic argument safety** - Proper handling of va_list without causing undefined behavior
- **Edge case completeness** - Handling corner cases like NULL strings, zero values, and maximum integer limits

## Performance Considerations

- **Single-pass parsing** - Format string is parsed in one pass for efficiency
- **Minimal dynamic allocation** - Strategic use of stack vs heap memory
- **Optimized number conversion** - Custom algorithms avoid unnecessary library calls
- **Efficient flag processing** - Bit-manipulation techniques for flag storage and checking

---

*This project was completed as part of the 42 School curriculum, demonstrating mastery of advanced C programming concepts including variadic functions, string parsing, and complex formatting logic.*

---

## License

This project is licensed under the [MIT License](./LICENSE).

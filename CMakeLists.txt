cmake_minimum_required(VERSION 3.31)
project(Printf C)

set(CMAKE_C_STANDARD 11)

add_executable(mandatory ft_printf/mandatory/include/ft_printf.h ft_printf/mandatory/src/ft_printf.c ft_printf/mandatory/src/ft_put_characters.c ft_printf/mandatory/src/ft_put_numbers.c
		ft_printf/Makefile)
target_include_directories(mandatory PRIVATE ft_printf/mandatory/include)

add_executable(bonus ft_printf/bonus/include/ft_printf_bonus.h ft_printf/bonus/src/ft_itoa_bonus.c ft_printf/bonus/src/ft_long_to_hex_bonus.c ft_printf/bonus/src/ft_print_chars_bonus.c ft_printf/bonus/src/ft_print_n_string_bonus.c ft_printf/bonus/src/ft_print_numbers_bonus.c ft_printf/bonus/src/ft_printf_bonus.c ft_printf/bonus/src/ft_string_manipulation_bonus.c ft_printf/bonus/src/ft_utils_bonus.c
		ft_printf/Makefile)
target_include_directories(bonus PRIVATE ft_printf/bonus/include)


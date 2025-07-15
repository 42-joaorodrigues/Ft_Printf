# ************************************************************************** */
#                                                                            */
#                                                        :::      ::::::::   */
#   Makefile                                           :+:      :+:    :+:   */
#                                                    +:+ +:+         +:+     */
#   By: joao-alm <joao-alm@student.1337.ma>        +#+  +:+       +#+        */
#                                                +#+#+#+#+#+   +#+           */
#   Created: 2024/10/21 10:55:50 by joao-alm          #+#    #+#             */
#   Updated: 2024/10/21 10:56:41 by joao-alm         ###   ########.fr       */
#                                                                            */
# ************************************************************************** */

######################
# Basic Configuration
######################

# Output files
NAME		= libftprintf.a

# Compilation settings
CC      	= cc
CFLAGS  	= -Wall -Werror -Wextra
LIBC    	= ar rc
RM      	= rm -rf

###################
# Mandatory Part
###################

# Source and object files
MAND_SRC		= mandatory/src/ft_printf.c \
			  	  mandatory/src/ft_put_characters.c \
			  	  mandatory/src/ft_put_numbers.c
MAND_INC		= -I mandatory/include
MAND_OBJ_DIR	= mandatory/obj
MAND_OBJ		= $(patsubst mandatory/src/%.c, $(MAND_OBJ_DIR)/%.o, $(MAND_SRC))

###################
# Bonus Part
###################

# Source and object files
BONUS_SRC		= bonus/src/ft_itoa_bonus.c \
			  	  bonus/src/ft_long_to_hex_bonus.c \
			  	  bonus/src/ft_print_chars_bonus.c \
			  	  bonus/src/ft_print_n_string_bonus.c \
			  	  bonus/src/ft_print_numbers_bonus.c \
			  	  bonus/src/ft_printf_bonus.c \
			  	  bonus/src/ft_string_manipulation_bonus.c \
			  	  bonus/src/ft_utils_bonus.c
BONUS_INC		= -I bonus/include
BONUS_OBJ_DIR	= bonus/obj
BONUS_OBJ		= $(patsubst bonus/src/%.c, $(BONUS_OBJ_DIR)/%.o, $(BONUS_SRC))

###################
# Main Targets
###################

# Default target: build mandatory part
all: $(NAME)

# Build the library with mandatory files
$(NAME): $(MAND_OBJ)
	$(LIBC) $@ $^

# Build the library with bonus files
bonus: $(BONUS_OBJ)
	$(LIBC) $(NAME) $^

####################
# Compilation Rules
####################

# Pattern rule for mandatory objects
$(MAND_OBJ_DIR)/%.o: mandatory/src/%.c
	@mkdir -p $(dir $@)
	$(CC) $(CFLAGS) $(MAND_INC) -c $< -o $@

# Pattern rule for bonus objects
$(BONUS_OBJ_DIR)/%.o: bonus/src/%.c
	@mkdir -p $(dir $@)
	$(CC) $(CFLAGS) $(BONUS_INC) -c $< -o $@

###################
# Cleaning Rules
###################

# Remove object files
clean:
	$(RM) $(MAND_OBJ_DIR) $(BONUS_OBJ_DIR)

# Remove object files and the library
fclean: clean
	$(RM) $(NAME)

# Rebuild the project from scratch
re: fclean all

# Declare phony targets
.PHONY: all bonus clean fclean re

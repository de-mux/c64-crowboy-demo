
# 6502 SDK Makefile
#
# This makefile will compile a 6502 assembly project. The main source file must be
#  named "boot.a"
# Change DASM_DIR to wherever you have DASM installed.
# Change ASM to the name of the assembler(default is dasm)

PROJECT_NAME=ping
PROJECT_DIR=.
ASM=dasm
DASM_DIR=~/bin
INC_DIR=-I$(PROJECT_DIR)/../sprites -I$(PROJECT_DIR)/../char -I$(PROJECT_DIR)/../music -I$(PROJECT_DIR)/../levels
DASM_OPTIONS=-v0 -E2 -l$(PROJECT_NAME).lst $(INC_DIR)

# -----------------------------------------------------------------------------
# Define the final dependecy;
# -----------------------------------------------------------------------------
all : $(PROJECT_DIR)/$(PROJECT_NAME).prg
	@echo Done

# -----------------------------------------------------------------------------
# Compile the main source program
# -----------------------------------------------------------------------------
$(PROJECT_DIR)/$(PROJECT_NAME).prg : $(PROJECT_DIR)/boot.a
	@$(DASM_DIR)/$(ASM) boot.a -o$(PROJECT_DIR)/$(PROJECT_NAME).prg $(DASM_OPTIONS)
		
		
# -----------------------------------------------------------------------------
# Clean definition;
# -----------------------------------------------------------------------------
.PHONY : clean
clean :
	@/bin/rm -f $(PROJECT_DIR)/$(PROJECT_NAME).prg $(PROJECT_DIR)/$(PROJECT_NAME).lst
	@echo Clean done...


# -----------------------------------------------------------------------------
# EOF;
# -----------------------------------------------------------------------------


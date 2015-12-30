
# 6502 SDK Makefile
#
# This makefile will compile a 6502 assembly project. The main source file must be
#  named "boot.a"
# Change ASM to the name of the assembler(default is dasm)
# Change ASM_DIR to wherever you have DASM installed.
# Change CRUNCHER, CRUNCH_DIR and CRUNCH_OPT based on your cruncher of choice

PROJECT_NAME=crowboy
PROJECT_DIR=.
ASM=dasm
ASM_DIR=~/bin
CRUNCHER=pucrunch
CRUNCH_DIR=~/bin
CRUNCH_OPTS=-c64
PRG_FILE=$(PROJECT_DIR)/$(PROJECT_NAME).prg
OBJ_FILE=$(PROJECT_DIR)/$(PROJECT_NAME).o
LST_FILE=$(PROJECT_DIR)/$(PROJECT_NAME).lst
INC_DIR=-I$(PROJECT_DIR)/../sprites -I$(PROJECT_DIR)/../char -I$(PROJECT_DIR)/../music -I$(PROJECT_DIR)/../levels
DASM_OPTIONS=-v0 -E2 -l$(PROJECT_NAME).lst $(INC_DIR)

# -----------------------------------------------------------------------------
# Define the final dependecy;
# -----------------------------------------------------------------------------
all : $(PROJECT_DIR)/$(PROJECT_NAME).prg
	@echo Done

# -----------------------------------------------------------------------------
# Crunch the main object file
# -----------------------------------------------------------------------------
$(PRG_FILE) : $(OBJ_FILE)
	@$(CRUNCH_DIR)/$(CRUNCHER) $(CRUNCH_OPTS) $(OBJ_FILE) $(PRG_FILE)

# -----------------------------------------------------------------------------
# Compile the main source program
# -----------------------------------------------------------------------------
$(OBJ_FILE) : $(PROJECT_DIR)/boot.a
	@$(ASM_DIR)/$(ASM) boot.a -o$(OBJ_FILE) $(DASM_OPTIONS)
		
		
# -----------------------------------------------------------------------------
# Clean definition;
# -----------------------------------------------------------------------------
.PHONY : clean
clean :
	@/bin/rm -f $(OBJ_FILE) $(PRG_FILE) $(LST_FILE)
	@echo Clean done...


# -----------------------------------------------------------------------------
# EOF;
# -----------------------------------------------------------------------------



TARGET_NAME = holo

CC = gcc

BASE_DIR = ../malloc
OBJ_DIR = $(BASE_DIR)/out
BIN_DIR = $(BASE_DIR)/bin

INC_DIR = \
		$(BASE_DIR)/inc

SRC_DIR = \
		$(BASE_DIR)/src

SRC_C_FILE = $(shell find $(SRC_DIR) -name "*.c")
OBJECT = $(patsubst %.c, %.o, $(wildcard $(SRC_C_FILE)))

INC = $(INC_DIR:%=-I%)

.PHONY : all clean run

all : $(TARGET_NAME)

$(OBJECT) : %.o : %.c
	@echo $(SRC_C_FILE)
	@echo $(OBJECT)
	@mkdir -p $(OBJ_DIR)
	$(CC) -c $(INC) $< -o $(OBJ_DIR)/$(notdir $@)

$(TARGET_NAME) : $(OBJECT)
	@mkdir -p $(BIN_DIR)
	$(CC) $(OBJ_DIR)/*.o -o $(BIN_DIR)/$@

clean :
	@echo clean ......
	rm -rf $(OBJ_DIR)
	rm -rf $(BIN_DIR)

run :
	(cd $(BIN_DIR); ./$(TARGET_NAME))
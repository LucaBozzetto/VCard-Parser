CC = gcc

INCLUDES = -Iinclude
CFLAGS = -Wall $(INCLUDES)
REQUIRED_PARSER = src/VCardParser.c include/VCardParser.h include/HelperFunctions.h src/HelperFunctions.c src/LinkedListAPI.c include/LinkedListAPI.h

UNAME := $(shell uname)

ifeq ($(UNAME), Linux)
all: linuxLib
# do something Linux-y
endif
ifeq ($(UNAME), Darwin)
# do something Solaris-y
all: macLib
endif

macLib: $(REQUIRED_PARSER)
	$(CC) $(CFLAGS) -dynamiclib -undefined suppress -flat_namespace src/VCardParser.c src/HelperFunctions.c src/LinkedListAPI.c -o ../VCardLib.dylib

linuxLib: $(REQUIRED_PARSER)
	$(CC) $(CFLAGS) -shared -fpic src/VCardParser.c src/HelperFunctions.c src/LinkedListAPI.c -o ../VCardLib.so
	

# removes all library files
clean: 
	$(RM) ../*.dylib ../*.so core

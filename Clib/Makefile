# POSIX build of the object simple_mmap.ecf expects on macOS and Linux.
# Usage: make -C Clib
CC ?= cc
CFLAGS ?= -O2 -fPIC

simple_mmap.o: simple_mmap.c simple_mmap.h
	$(CC) $(CFLAGS) -c simple_mmap.c -o simple_mmap.o

clean:
	rm -f simple_mmap.o

.PHONY: clean

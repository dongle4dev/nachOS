# use normal make for this Makefile
#
# Makefile for building user programs to run on top of Nachos
#
# Several things to be aware of:
#
#    Nachos assumes that the location of the program startup routine (the
# 	location the kernel jumps to when the program initially starts up)
#       is at location 0.  This means: start.o must be the first .o passed 
# 	to ld, in order for the routine "Start" to be loaded at location 0
#

# if you are cross-compiling, you need to point to the right executables
# and change the flags to ld and the build procedure for as

GCCDIR = ../../../gnu-decstation-ultrix/decstation-ultrix/2.95.3/

LDFLAGS = -T script -N
ASFLAGS = -mips2
CPPFLAGS = $(INCDIR)

# if you aren't cross-compiling:
# GCCDIR =
# LDFLAGS = -N -T 0
# ASFLAGS =
# CPPFLAGS = -P $(INCDIR)

PATH = $(GCCDIR):/lib:/usr/bin:/bin

CC = $(GCCDIR)gcc -B../../../gnu-decstation-ultrix/
AS = $(GCCDIR)as
LD = $(GCCDIR)ld

CPP = gcc -E
INCDIR =-I../userprog -I../threads
CFLAGS = -G 0 -c $(INCDIR)

all: halt shell matmult sort createfile rwnumber help ascii bbsort readstring

start.o: start.s ../userprog/syscall.h
	$(CPP) $(CPPFLAGS) start.c > strt.s
	$(AS) $(ASFLAGS) -o start.o strt.s
	rm strt.s

halt.o: halt.c
	$(CC) $(CFLAGS) -c halt.c
halt: halt.o start.o
	$(LD) $(LDFLAGS) start.o halt.o -o halt.coff
	../bin/coff2noff halt.coff halt

shell.o: shell.c
	$(CC) $(CFLAGS) -c shell.c
shell: shell.o start.o
	$(LD) $(LDFLAGS) start.o shell.o -o shell.coff
	../bin/coff2noff shell.coff shell

sort.o: sort.c
	$(CC) $(CFLAGS) -c sort.c
sort: sort.o start.o
	$(LD) $(LDFLAGS) start.o sort.o -o sort.coff
	../bin/coff2noff sort.coff sort

matmult.o: matmult.c
	$(CC) $(CFLAGS) -c matmult.c
matmult: matmult.o start.o
	$(LD) $(LDFLAGS) start.o matmult.o -o matmult.coff
	../bin/coff2noff matmult.coff matmult

createfile.o: createfile.c
	$(CC) $(CFLAGS) -c createfile.c
createfile: createfile.o start.o
	$(LD) $(LDFLAGS) start.o createfile.o -o createfile.coff
	../bin/coff2noff createfile.coff createfile

rwnumber.o: rwnumber.c
	$(CC) $(CFLAGS) -c rwnumber.c
rwnumber: rwnumber.o start.o
	$(LD) $(LDFLAGS) start.o rwnumber.o -o rwnumber.coff
	../bin/coff2noff rwnumber.coff rwnumber

# printNumber.o: printNumber.c
# 	$(CC) $(CFLAGS) -c printNumber.c
# printNumber: printNumber.o start.o
# 	$(LD) $(LDFLAGS) start.o printNumber.o -o printNumber.coff
# 	../bin/coff2noff printNumber.coff printNumber

help.o: help.c
	$(CC) $(CFLAGS) -c help.c
help: help.o start.o
	$(LD) $(LDFLAGS) start.o help.o -o help.coff
	../bin/coff2noff help.coff help

ascii.o: ascii.c
	$(CC) $(CFLAGS) -c ascii.c
ascii: ascii.o start.o
	$(LD) $(LDFLAGS) start.o ascii.o -o ascii.coff
	../bin/coff2noff ascii.coff ascii

bbsort.o: bbsort.c
	$(CC) $(CFLAGS) -c bbsort.c
bbsort: bbsort.o start.o
	$(LD) $(LDFLAGS) start.o bbsort.o -o bbsort.coff
	../bin/coff2noff bbsort.coff bbsort

readstring.o: readstring.c
	$(CC) $(CFLAGS) -c readstring.c
readstring: readstring.o start.o
	$(LD) $(LDFLAGS) start.o readstring.o -o readstring.coff
	../bin/coff2noff readstring.coff readstring
	
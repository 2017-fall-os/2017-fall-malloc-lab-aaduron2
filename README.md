# os-malloc
This directory contains:

myAllocator.c: a first-fit allocator
myAllocator.h: its header file

myAllocatorTest1.c: a test program for my allocator 

malloc.c: a replacement for malloc that uses my allocator
test1.c: a test program that uses this replacement malloc

There are two different testers as some implementations of printf
call malloc to allocate buffer space. This causes test1 to behave
improperly as it uses myAllocator as a malloc replacement. In this
case myAllocatorTest1 will function correctly. The only difference
between the programs is that test1 uses myAllocator as a malloc
replacement and myAllocatorTest1 uses myAllocator directly.

Makefile: a fairly portable "makefile", targets "all" and "clean"

To compile: 
 $ make 
To clean:
 $ make clean

The cygwin runtime uses malloc() and brk() extensively.  It is
interesting to compare the output of test1 & myAllocatorTest1.  All
those extra allocated regions are being used by cygwin's libraries!


# Lab Assignment
-----------------

- Modified resizeRegion algorithm to coalesce the current block with the next block if the next block is not allocated and has enough space to be coalesced.  Accomplished this with the coalescePrev method provided with the lab.

- Added findBestFit method that is just a modified version of findFirstFit by looking at all the unallocated blocks and finding with the closest block size to the requested size needed to be allocated.

- Added bestFitAllocRegion, but is just a copy of findFitAllocRegion.

- Added more tests to view if my best fit and resize region are working correctly in myAllocatorTest1.c

Notes
-----

Decided to add the best fit method as it was just a simple modification to the first fit method that was already provided. For the modified resize region, the lab TODO comment just asked to resize with the successor of the current region if there is sufficient space.


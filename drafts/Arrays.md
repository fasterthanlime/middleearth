
Author:  Amos Wenger (nddrylliog)  
Created: 2010-05-15  
Updated: 2010-05-15  
Type:    Feature  
Status:  Draft  
Fixes:   None  

Arrays
======

   + Raw arrays and Pointers
   + ArrayList
   + Introducing: ooc arrays
   + Rationale
   + Issues
   + References and Footnotes

Raw arrays and Pointers
-----------------------

The C language, on which the main ooc implementation is largely based, offers some level of array support. Little distinction is being made between pointers and C arrays.

However, functionality in this area is weak.

First, the order of declaration is quite strange:

    int array[];
    int *array;

C arrays aren't bound-checked, resulting in segmentation faults in case of out-of-bounds read/write, or even worse - corruption of other sensible memory areas.

    int array[10];
    int victim = 42;
    array[11] = -1;
    // kaboom! victim is now -1 if array and victim were contiguous in memory

Pointers may overlap, preventing some optimization (hence the distinction between memmov and memcpy, for example). See [the Wikipedia page on Aliasing][1] for more details.

Also, C arrays aren't multi-dimensional. Although you can declare things like

    int matrix[3][3];

You can't use that notation in function arguments definition

    void printMatrix(int matrix[][]); // error
    
.. you have to use `int *matrix`

ooc has always supported raw arrays and pointers with a C-like syntax with a few syntactic tweaks. In C:

    // in C
    int *a, b, c;   // 'a' is a pointer to int, 'b' and 'c' are ints.
    int *a, *b, *c; // 'a', 'b', 'c', are pointers to int

    // in ooc
    a, b, c: Int* // 'a', 'b', 'c', are pointers to int

ArrayList
---------

ooc provides a higher-level way to store an ordered list of elements: structs/ArrayList. However, even with improvements to the generics code, it'll never be quite as fast as built-in arrays.

The main difference between an array and an ArrayList is that ArrayList make a distinction between size and capacity.

    list := ArrayList<Int> new(10) // size = 0, capacity = 10
    list add(1)                    // size = 1, capacity = 10
    list[8] // error! can't access the 9th element, 9 >= 1

Introducing: ooc arrays
-----------------------

Therefore, 

Rationale
---------



Issues
------

When creating bindings for a C library


References and Footnotes
------------------------


[1]: http://en.wikipedia.org/wiki/Aliasing_(computing) "Wikipedia article on Aliasing"

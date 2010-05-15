
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

The C language, on which the main ooc implementation is largely based, offers some level of array support. Little distinction is being made between pointers and C arrays. However, functionality in this area is weak. Arrays aren't bound-checked, resulting in segmentation faults in case of out-of-bounds read/write. Pointers may overlap, preventing some optimization (hence the distinction between memmov and memcpy, for example). See [The Wikipedia page on Aliasing][1] for more details.

Also, C arrays, besides being not bound-checked and with a weird declaration syntax, aren't multi-dimensional. Although you can declare things like

``
int matrix[3][3];
``

You can't use that notation in function arguments definition

``
void printMatrix(int[][] matrix); // error
``

ooc has always supported raw arrays and pointers with a C-like syntax, again, making little distinction between them.

ArrayList
---------

ooc provides a higher-level way to store an ordered list of elements: structs/ArrayList. However, even with improvements to the generics code, it'll never be quite as fast as built-in arrays.

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

##### Symbolic Value : Error Handling
##### ERRNUM_MASK - Mask to obtain status code.
---
##### #include <globerr.h>
**Description :**
The 16-bit value of a STATUS error code consists of the following fields:

1 bit: Flag bit - status message has been displayed
1 bit: Flag bit - status message came from a remote machine (i.e., a server)
6 bits: "Package" code or partial package code
8 bits: Status value or partial package code plus status value

This mask is used to obtain the 8 bit status value from a STATUS error code.  
This mask is useful only with package codes that use the designated 6 bits of 
the status code.  Newer package codes may use more than 6 bits, leaving fewer 
than 8 bits for the status value. 
**See Also :**
[ERRNUM](D:/md_files/ERRNUM.md)
[STATUS](D:/md_files/STATUS.md)
---

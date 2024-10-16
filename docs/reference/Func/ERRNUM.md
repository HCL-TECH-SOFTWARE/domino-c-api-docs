##### Function : Error Handling
##### ERRNUM - Error code specific to the package portion of STATUS error code .
---
```
#include <globerr.h>
STATUS ERRNUM(

	STATUS  x);
```
**Description :**

The 16-bit value of a STATUS error code consists of the following fields:

1 bit: Flag bit - status message has been displayed
1 bit: Flag bit - status message came from a remote machine (i.e., a server)
6 bits: "Package" code or partial package code
8 bits: Status value or partial package code plus status value

This macro masks off the 2 flag bits and the 6-bit package code.  Note that 
newer package codes may use more than 6 bits (leaving fewer than 8 bits for the 
status value).  

Note: This function is implemented as a macro:

#define ERRNUM(x) ((STATUS) ((x) & ERRNUM_MASK))

**Parameters :**
Input :
x  -  STATUS error code returned from a C API function.

Output :
(routine)  -  STATUS error code with high order byte masked off.



**See Also :**
[OSLoadString](/domino-c-api-docs/reference/Func/OSLoadString)
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
[ERRNUM_MASK](/domino-c-api-docs/reference/Symb/ERRNUM_MASK)
[ERR](/domino-c-api-docs/reference/Func/ERR)
[PKG](/domino-c-api-docs/reference/Func/PKG)
---

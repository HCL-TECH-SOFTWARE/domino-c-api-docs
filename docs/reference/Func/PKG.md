##### Function : Error Handling
##### PKG - Return the Domino package code.
---
```
#include <globerr.h>
STATUS PKG(

	STATUS  x);
```
**Description :**

The 16-bit value of a STATUS error code consists of the following fields:

1 bit: Flag bit - status message has been displayed
1 bit: Flag bit - status message came from a remote machine (i.e., a server)
6 bits: "Package" code or partial package code
8 bits: Status value or partial package code plus status value

The package code identifies which Notes component generated the status code.  
The PKG macro masks off the 2 flag bits and the 8 lowest bits, leaving only the 
package code.  This function is useful only with package codes that use the 
designated 6 bits of the status code.  Newer package codes may use more than 6 
bits (leaving fewer than 8 bits for the status value).  This function will not 
return the correct results for these newer package codes.

Note: This function is implemented as a macro:

#define PKG(x) ((STATUS) ((x) & PKG_MASK))

**Parameters :**
Input :
x  -  Notes status code.

Output :
(routine)  -  Package code from a Domino STATUS value.



**See Also :**
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
[STS_xxx](/domino-c-api-docs/reference/Symb/STS_xxx)
[ERR](/domino-c-api-docs/reference/Func/ERR)
[ERRNUM](/domino-c-api-docs/reference/Func/ERRNUM)
[PKG_MASK](/domino-c-api-docs/reference/Symb/PKG_MASK)
---

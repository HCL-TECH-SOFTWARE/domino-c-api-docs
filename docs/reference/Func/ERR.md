##### Function : Error Handling
##### ERR - Mask off flag bits from STATUS value.
---
```
#include <globerr.h>
STATUS ERR(

	STATUS  x);
```
**Description :**

The 16-bit value of a STATUS error code consists of the following fields:

1 bit: Flag bit - status message has been displayed
1 bit: Flag bit - status message came from a remote machine (i.e., a server)
6 bits: "Package" code or partial package code
8 bits: Status value or partial package code plus status value

The bit flag STS_REMOTE indicates that the error was detected on a remote Lotus 
Domino Server, rather than on the local machine.  The bit flag STS_DISPLAYED 
indicates that some component of the system has already reported this error to 
the user, so your program probably does not need to.

The C API macro ERR() masks off these two bit flags, yielding an error code 
with just the subsystem identifier and the subsystem-specific error code.  Use 
the macro ERR() to mask off these bits before passing a STATUS error code to 
OSLoadString, because these bits may prevent OSLoadString from interpreting the 
code correctly.

Note: This function is implemented as a macro:

#define ERR(x) ((STATUS) (x & ERR_MASK))

**Parameters :**
Input :
x  -  STATUS error code returned from a C API function.

Output :
(routine)  -  STATUS error code with flag bits masked off.



**See Also :**
[OSLoadString](/domino-c-api-docs/reference/Func/OSLoadString)
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
[PKG](/domino-c-api-docs/reference/Func/PKG)
[ERRNUM](/domino-c-api-docs/reference/Func/ERRNUM)
[ERR_MASK](/domino-c-api-docs/reference/Symb/ERR_MASK)
---

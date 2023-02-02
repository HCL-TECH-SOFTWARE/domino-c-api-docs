##### Function : Miscellaneous
##### ERROR_REMOTE - Indicate whether the STS_REMOTE bit is set.
---
##### #include <globerr.h>
STATUS **ERROR_REMOTE(**

	STATUS  x);
**Description :**
Indicate whether the STS_REMOTE bit is set.
Note: This function is implemented as a macro:

#define ERROR_REMOTE(x) ((x) & STS_REMOTE)
**Parameters :**
Input :
x  -  Status code.

Output :
(routine)  -  Return status from this call -- indicates whether the error code's STS_REMOTE bit is set.


**See Also :**
[STATUS](D:/md_files/STATUS.md)
[STS_xxx](D:/md_files/STS_xxx.md)
---

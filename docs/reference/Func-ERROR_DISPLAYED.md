##### Function : Miscellaneous
##### ERROR_DISPLAYED - Indicate whether the STS_DISPLAYED bit is set.
---
##### #include <globerr.h>
STATUS **ERROR_DISPLAYED(**

	STATUS  x);
**Description :**
Indicate whether the STS_DISPLAYED bit is set.
Note: This function is implemented as a macro:

define ERROR_DISPLAYED(x) ((x) & STS_DISPLAYED)
**Parameters :**
Input :
x  -  Status code.

Output :
(routine)  -  Return status from this call -- indicates whether the error code's STS_DISPLAYED bit is set.


**See Also :**
[STATUS](D:/md_files/STATUS.md)
[STS_xxx](D:/md_files/STS_xxx.md)
---

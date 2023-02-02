##### Function : Miscellaneous
##### RAWBLK - Return the "raw" error status code value.
---
##### #include <globerr.h>
STATUS **RAWBLK(**

	STATUS  x);
**Description :**
Return the "raw" error status code value, with the status code flags removed, 
as a value of type STATUS.

Note: This function is implemented as a macro:

#define RAWBLK(x) ((STATUS) ((x)&~(STS_DISPLAYED|STS_REMOTE)))
**Parameters :**
Input :
x  -  Error status code.

Output :
(routine)  -  "Raw" error status code value, with the status code flags removed.


**See Also :**
[NOBLK](D:/md_files/NOBLK.md)
[STATUS](D:/md_files/STATUS.md)
[STS_xxx](D:/md_files/STS_xxx.md)
---

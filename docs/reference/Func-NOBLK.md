##### Function : Miscellaneous
##### NOBLK - Extract the status code flag values from the status code.
---
##### #include <globerr.h>
STATUS **NOBLK(**

	STATUS  x);
**Description :**
The status code flag values are extracted from the status code, and returned in 
a value of type STATUS.

Note: This function is implemented as a macro:

#define NOBLK(x) ((STATUS) ((x)&(STS_DISPLAYED|STS_REMOTE)))
**Parameters :**
Input :
x  -  Status code

Output :
(routine)  -  Status code flag values extracted from the status code.


**See Also :**
[RAWBLK](D:/md_files/RAWBLK.md)
[STS_xxx](D:/md_files/STS_xxx.md)
---

##### Function : Character Manipulation
##### OSGetLMBCSCLS - Returns an NLS_INFO struct containing information about the default LMBCS character set.
---
```
#include <osmisc.h>
NLS_PINFO LNPUBLIC OSGetLMBCSCLS(
void);
```
**Description :**

This function returns an NLS_INFO struct containing information about the 
current default LMBCS character set. The NLS_INFO struct may then be used in 
subsequent calls to other NLS functions.

**Parameters :**

Output :
(routine)  -  A pointer to an NLS_INFO struct.



**See Also :**
[NLS_INFO](/domino-c-api-docs/reference/Data/NLS_INFO)
[NLS_PINFO](/domino-c-api-docs/reference/Data/NLS_PINFO)
[OSGetNativeCLS](/domino-c-api-docs/reference/Func/OSGetNativeCLS)
---

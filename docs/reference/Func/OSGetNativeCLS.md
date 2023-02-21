##### Function : Character Manipulation
##### OSGetNativeCLS - Returns an NLS_INFO struct containing information about the native (machine-specific) character set.
---
```
#include <osmisc.h>
NLS_PINFO LNPUBLIC OSGetNativeCLS(
void);
```
**Description :**

This function returns an NLS_INFO struct containing information about the 
native character set. If for some reason your application needed to manipulate 
text in the platform's native character set rather than in LMBCS, The NLS_INFO 
struct could then be used in subsequent calls to other NLS functions.

**Parameters :**

Output :
(routine)  -  A pointer to an NLS_INFO struct.



**See Also :**
[NLS_INFO](/domino-c-api-docs/reference/Data/NLS_INFO)
[NLS_PINFO](/domino-c-api-docs/reference/Data/NLS_PINFO)
[OSGetLMBCSCLS](/domino-c-api-docs/reference/Func/OSGetLMBCSCLS)
---

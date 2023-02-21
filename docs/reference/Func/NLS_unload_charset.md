##### Function : Character Manipulation
##### NLS_unload_charset - Unloads a character set.
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_unload_charset(

	NLS_PINFO  pInfo);
```
**Description :**

This function unloads a character set that had previously been loaded by a call 
to NLS_load_charset.

**Parameters :**
Input :
pInfo  -  A pointer to a populated NLS_INFO structure.

Output :
(routine)  -  NLS_SUCCESS



**See Also :**
[NLS_load_charset](/domino-c-api-docs/reference/Func/NLS_load_charset)
---

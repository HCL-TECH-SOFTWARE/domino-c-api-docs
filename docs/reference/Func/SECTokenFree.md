##### Function : User Registration
##### SECTokenFree - Free a Single Sign-On Token.
---
```
#include <bsafe.h>
void LNPUBLIC SECTokenFree(

	MEMHANDLE *mhToken);
```
**Description :**

Use this function to free the memory associated with an SSO_TOKEN structure. 
There is no need to unlock the structure or its members before freeing, this 
call will unlock all outstanding locks.

**Parameters :**
Input :
mhToken  -  Pointer to a MEMHANDLE returned from a call to SECTokenGenerate.

Output :
(routine)  -  None.



**See Also :**
[SECTokenGenerate](/domino-c-api-docs/reference/Func/SECTokenGenerate)
[SECTokenValidate](/domino-c-api-docs/reference/Func/SECTokenValidate)
[SSO_TOKEN](/domino-c-api-docs/reference/Data/SSO_TOKEN)
---

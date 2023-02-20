##### Function : Dir
##### DirCtxSetFlags - Sets the flags for directory operations. 
---
```
#include <dirctx.h>
STATUS LNPUBLIC DirCtxSetFlags(

	DIRCTX  hCtx,
	DWORD  flags);
```
**Description :**

Sets the flags for directory operations. 

**Parameters :**
Input :
hCtx  -  Directory context to set the flags of.

flags  -  Flags which control the domains searched.
DIR_TRUSTED_FOR_AUTHENTICATION
DIR_TRUSTED_FOR_AUTHORIZATION
DIR_PRIMARY_ONLY
DIR_NO_DIRCAT
DIR_VIRTUALIZE


Output :
(routine)  -  NOERROR
...
An ERR status on failure indicating the problem. 




**See Also :**
---

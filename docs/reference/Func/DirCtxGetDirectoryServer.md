##### Function : Dir
##### DirCtxGetDirectoryServer - Gets the name of the Domino server to perform directory operations on
---
```
#include <dirctx.h>
STATUS LNPUBLIC DirCtxGetDirectoryServer(

	DIRCTX  char *,
	char *serverName);
```
**Description :**

Gets the name of the Domino server to perform directory operations on.

**Parameters :**
Input :
char *  -  Directory context to be queried.

Output :
(routine)  -  Status code: 
NOERROR on success. 
An ERR status on failure indicating the problem. 


serverName  -  Caller allocated buffer at least MAXDOMAINNAME+1 in size to receive the serverName component of the hCtx.


**See Also :**
[DirCtxGetDomain](/reference/Func/DirCtxGetDomain)
---

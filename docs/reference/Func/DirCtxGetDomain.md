##### Function : Dir
##### DirCtxGetDomain - Gets the name of the Domino domain to perform directory operations on.
---
```
#include <dirctx.h>
STATUS LNPUBLIC DirCtxGetDomain(

	DIRCTX  hCtx,
	char *domainName);
```
**Description :**

Gets the name of the Domino domain to perform directory operations on, if not 
previously set then a NULL domain name is returned (i.e. "").

**Parameters :**
Input :
hCtx  -  Directory context to be queried.

Output :
(routine)  -  Status code: 
NOERROR on success. 
An ERR status on failure indicating the problem. 


domainName  -  Caller allocated buffer at least MAXDOMAINNAME+1 in size to receive the domain component of the hCtx.


**See Also :**
[DirCtxGetDirectoryServer](/reference/Func/DirCtxGetDirectoryServer)
---

##### Function : Dir
##### DirCtxCreateDominoPerson - Create an in-memory dominoPerson entry. 
---
```
#include <dirctx.h>
STATUS LNPUBLIC DirCtxCreateDominoPerson(

	DIRCTX  hCtx,
	const char *name,
	const char *lastName,
	DIRENTRY *hEntry);
```
**Description :**

Create an in-memory dominoPerson entry. 
Note that the entry is not actually written to the directory until a subsequent 
DirEntryUpdate() operation. This API supports the promotion of existing 
non-Domino person entries (typically in an LDAP based directory) to be full 
dominoPerson entry. It also supports the creation of a dominoPerson entry from 
scratch. 


**Parameters :**
Input :
hCtx  -  Directory context for this operation.

name  -  The Notes name of the person to be added, specified in Notes distinguished name or abbreviated name syntax. An entry by this name must not exist in domainName.

lastName  -  The last name of the person.

hEntry  -  If non-NULL on input, this indicates that a Person entry in a non-Domino directory (typically LDAP based) is to be "registered" as a DominoPerson. The input handle is typically obtained from a previous DirCtxSearchByName or similar search/lookup/get operation. If NULL on input, then a new DominoPerson entry will be created from scratch and returned via this parameter.

Output :
(routine)  -  Status code: 
NOERROR on success. 
ERR_DN_PARSE
ERR_DIR_NULL_ARGUMENT If itemName is NULL.
ERR_DIR_INVALID_ARGUMENT
ERR_DIR_MUST_PROMOTE
An ERR status on failure indicating the problem.


hEntry  -  If non-NULL on input, this indicates that a Person entry in a non-Domino directory (typically LDAP based) is to be "registered" as a DominoPerson. The input handle is typically obtained from a previous DirCtxSearchByName or similar search/lookup/get operation. If NULL on input, then a new DominoPerson entry will be created from scratch and returned via this parameter.


**See Also :**
[DirEntryUpdate](/domino-c-api-docs/reference/Func/DirEntryUpdate)
---

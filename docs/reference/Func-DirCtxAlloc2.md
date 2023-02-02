##### Function : Dir
##### DirCtxAlloc2 - Allocates a directory context for performing directory operations. 
---
##### #include <dirctx.h>
STATUS LNPUBLIC **DirCtxAlloc2(**

	const char *serverName,
	const char *domainName,
	DIRCTX *rethCtx);
**Description :**
The properties of this directory context are assigned the following values: 
The server name will be assigned from the serverName argument. 
The domain will be assigned from the domainName argument. 
The flags value will be 0.
**Parameters :**
Input :
serverName  -  Name of the Domino server to perform the operation on. A client would typically specify the directory server for this parameter (see DirServerGetDirectoryServer()). A server would typically specify NULL to perform the operation locally.

domainName  -  The Domino domain to determine the administration server for. If domainName is NULL or the server does not have directory assistance configured, then the primary domain of serverName is implied.

Output :
(routine)  -  Status code: 
NOERROR on success. 
ERR_DIR_NULL_ARGUMENT if rethCtx is NULL. 
An ERR status on failure indicating the problem. 


rethCtx  -  Directory context for directory operations. NULLDIRCTX is returned if unsuccessful.

**See Also :**
[](D:/md_files/.md)
---

##### Function : User Registration
##### SECTokenGenerate - Generate a Single Sign-On Token.
---
##### #include <bsafe.h>
STATUS LNPUBLIC **SECTokenGenerate(**

	char *ServerName,
	char *OrgName,
	char *ConfigName,
	char *UserName,
	TIMEDATE *Creation,
	TIMEDATE *Expiration,
	MEMHANDLE *retmhToken,
	DWORD  dwReserved,
	void *vpReserved);
**Description :**
Use this function to generate an authentication token for interoperability with 
Domino protocols that support Single Sign-On (IE: HTTP and DIIOP), as well as 
IBM WebSphere Advanced Server. The return value retmhToken is a MEMHANDLE that 
references an SSO_TOKEN structure when locked with OSMemoryLock. See SSO_TOKEN 
for more information.

Note: this function will be remoted in a future release.
**Parameters :**
Input :
ServerName  -  Domino server to ask to generate the token (reserved as NULL).

OrgName  -  Organization that the server belongs to (OPTIONAL: Specify NULL if not using 'Internet Sites' view for configuration)

ConfigName  -  Name of Web SSO Configuration to use.

UserName  -  Canonicalized Notes username to encode in the token.

Creation  -  Creation time to set for the token (specify NULL to use the current time).

Expiration  -  Expiration time to set for the token (specify NULL to use expiration from specified Web SSO Configuration).

dwReserved  -  Must be 0 or fSECToken_EnableRenewal.  If fSECToken_EnableRenewal is passed, and vpReserved is not NULL, then the routine will write to a TIMEDATE pointed to by vpReserved the time at which the Token does its IdleTimeout (which may be sooner than the value returned by Expiration if idle timeout is enabled for this LTPA token).  Idle timeout can only be enabled for Domino style tokens. The Websphere format does not support them.  See fSECToken_xxx.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.


retmhToken  -  MEMHANDLE to an SSO_TOKEN structure.

vpReserved  -  If not NULL (see dwReserved), then the routine will write to a TIMEDATE pointed to by vpReserved the time at which the Token does its IdleTimeout (which may be sooner than the value returned by Expiration if idle timeout is enabled for this LTPA token).  Idle timeout can only be enabled for Domino style tokens. The Websphere format does not support them.  

**See Also :**
[fSECToken_xxx](D:/md_files/fSECToken_xxx.md)
[SECTokenFree](D:/md_files/SECTokenFree.md)
[SECTokenValidate](D:/md_files/SECTokenValidate.md)
[SSO_TOKEN](D:/md_files/SSO_TOKEN.md)
---

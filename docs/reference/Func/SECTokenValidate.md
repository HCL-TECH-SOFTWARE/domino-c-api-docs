##### Function : User Registration
##### SECTokenValidate - Validate a Single Sign-On Token.
---
```
#include <bsafe.h>
STATUS LNPUBLIC SECTokenValidate(

	char *ServerName,
	char *OrgName,
	char *ConfigName,
	char *TokenData,
	char *retUsername,
	TIMEDATE *retCreation,
	TIMEDATE *retExpiration,
	DWORD  dwReserved,
	void *vpReserved);
```
**Description :**

Use this function to validate an authentication token for interoperability with 
Domino protocols that support Single Sign-On (IE: HTTP and DIIOP), as well as 
IBM WebSphere Advanced Server. Returns the username encoded in the token as 
well as the token creation and expiration time. The creation time is not 
returned if the configuration specified is set up for interoperability with 
IBM's WebSphere. Any error returned from this function represents 
authentication failure, but the username and times returned are valid on 
ERR_LTPA_TOKEN_EXPIRED.

Note: this function will be remoted in a future release.

**Parameters :**
Input :
ServerName  -  Domino server to ask to validate the token. (Reserved as NULL)

OrgName  -  Organization that the server belongs to (OPTIONAL: Specify NULL if not using 'Internet Sites' view for configuration)

ConfigName  -  Name of Web SSO Configuration to use.

TokenData  -  Null-terminated token data.

dwReserved  -  Must be 0 or fSECToken_EnableRenewal.  If fSECToken_EnableRenewal is passed, and vpReserved is not NULL, then the routine will write to a TIMEDATE pointed to by vpReserved the time at which the Token does its IdleTimeout (which may be sooner than the value returned by Expiration if idle timeout is enabled for this LTPA token).  Idle timeout can only be enabled for Domino style tokens. The Websphere format does not support them.  See fSECToken_xxx.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.


retUsername  -  Pointer to a buffer to return name into (must be MAXUSERNAME sized)

retCreation  -  Pointer to a TIMEDATE to return creation into (OPTIONAL, can specify NULL)

retExpiration  -  Pointer to a TIMEDATE to return expiration into (OPTIONAL, can specify NULL)

vpReserved  -  If not NULL (see dwReserved), then the routine will write to a TIMEDATE pointed to by vpReserved the time at which the Token does its IdleTimeout (which may be sooner than the value returned by Expiration if idle timeout is enabled for this LTPA token).  Idle timeout can only be enabled for Domino style tokens. The Websphere format does not support them.  


**See Also :**
[SECTokenFree](/reference/Func/SECTokenFree)
[SECTokenGenerate](/reference/Func/SECTokenGenerate)
[SSO_TOKEN](/reference/Data/SSO_TOKEN)
---

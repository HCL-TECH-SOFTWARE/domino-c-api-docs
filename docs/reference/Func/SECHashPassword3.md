##### Function : User Registration
##### SECHashPassword3 -  Returns the more secure digest, given an unencoded password. 
---
```
#include <misc.h>
STATUS LNPUBLIC SECHashPassword3(

	WORD  wPasswordLen,
	BYTE *Password,
	WORD  wVersion,
	WORD  wHashType,
	void *Param1,
	DWORD  dwParam1,
	void *Param2,
	DWORD  dwParam2,
	WORD  wMaxDigestLen,
	WORD *retDigestLen,
	BYTE *retDigest,
	DWORD  ReservedFlags,
	void *pReserved
);
```
**Description :**

This function takes an unencoded password and returns the more secure version 
of the digest. The Internet Password is in this "more secure" format.

**Parameters :**
Input :
wPasswordLen  -  Length of password to be digested

Password  -  Password to be digested

wVersion  -  Which version of the notes password digest to build. See SEC_xxx.

wHashType  -  Which algorithm to use to generate the digest
Currently only SEC_ai_HMAC_SHA1 will be supported

Param1  -  Parameter specific to wHashType

dwParam1  -  DWORD specific to wHashType

Param2  -  Another parameter specific to wHashType

dwParam2  -  Another DWORD specific to wHashType

wMaxDigestLen  -  Maximum length of retDigest

ReservedFlags  -  0

pReserved
  -  NULL

Output :
(routine)  -  Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.



retDigestLen  -  Return length of the digest

retDigest  -  Buffer filled in with digest


**See Also :**
[SECHashPassword](/domino-c-api-docs/reference/Func/SECHashPassword)
[SEC_ai_HMAC_SHA1](/domino-c-api-docs/reference/Symb/SEC_ai_HMAC_SHA1)
[SEC_xxx](/domino-c-api-docs/reference/Symb/SEC_xxx)
---

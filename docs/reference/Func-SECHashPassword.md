##### Function : User Registration
##### SECHashPassword - Returns the more secure digest, given an unencoded password. 
---
##### #include <misc.h>
STATUS LNPUBLIC **SECHashPassword(**

	WORD  wPasswordLen,
	BYTE *Password,
	WORD  wMaxDigestLen,
	WORD *retDigestLen,
	BYTE *retDigest,
	DWORD  ReservedFlags,
	void *pReserved);
**Description :**
This function takes an unencoded password and returns the more secure version 
of the digest. The Internet Password is in this "more secure" format.
**Parameters :**
Input :
wPasswordLen  -  Length of an unencoded password to be digested.

Password  -  An unencoded password to be digested

wMaxDigestLen  -  Maximum output length of retDigest

ReservedFlags  -  Should be set to 0. Reserved.

pReserved  -  Should be set to NULL. Reserved.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


retDigestLen  -  Length of digest that is returned 

retDigest  -  Digest that is returned 

**See Also :**
[SECVerifyPassword](D:/md_files/SECVerifyPassword.md)
---

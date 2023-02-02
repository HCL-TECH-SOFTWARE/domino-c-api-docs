##### Function : User Registration
##### SECTokenFree - Free a Single Sign-On Token.
---
##### #include <bsafe.h>
void LNPUBLIC **SECTokenFree(**

	MEMHANDLE *mhToken);
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
[SECTokenGenerate](D:/md_files/SECTokenGenerate.md)
[SECTokenValidate](D:/md_files/SECTokenValidate.md)
[SSO_TOKEN](D:/md_files/SSO_TOKEN.md)
---

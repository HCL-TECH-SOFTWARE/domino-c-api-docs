##### Function : IDs
##### PKCS12_ImportFileToIDFile - Insert the certificates and keys from a PKCS 12 file into an ID file.
---
```
#include <pkcs12.h>
STATUS LNPUBLIC PKCS12_ImportFileToIDFile(

	char *pPKCS12Filename,
	char *pPKCS12Filepassword,
	char *pIdFilename,
	char *pIdFilepassword,
	DWORD  ImportFlags,
	DWORD  ReservedFlags,
	void *pReserved);
```
**Description :**

Insert the certificates and keys from a Public Key Cryptography Standards #12  
file into an ID file.  This function is supported for Windows 32-bit, IBM AIX 
and Macintosh platforms only. 

**Parameters :**
Input :
pPKCS12Filename  -  Pointer of the name of the PKCS 12 file to be parsed.

pPKCS12Filepassword  -  Pointer to PKCS 12 file password.

pIdFilename  -  Pointer to the name of an ID file which the keys and the certificates will be inserted into.

pIdFilepassword  -  Pointer to the password of the ID file which the keys and the certificates will be inserted into.

ImportFlags  -  0 or one of the values specified in PKCS12_xxx.

ReservedFlags  -  Reserved for future expansion.  Should be set to 0.

pReserved  -  Reserved for future expansion.  Should be set to NULL.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[PKCS12_ExportIDFileToFile](/reference/Func/PKCS12_ExportIDFileToFile)
[PKCS12_xxx](/reference/Symb/PKCS12_xxx)
---

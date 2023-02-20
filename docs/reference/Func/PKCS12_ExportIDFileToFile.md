##### Function : IDs
##### PKCS12_ExportIDFileToFile - Writes the key and the certificates found in an ID file to a PKCS12 file.
---
```
#include <pkcs12.h>
STATUS LNPUBLIC PKCS12_ExportIDFileToFile(

	char *pIdFilename,
	char *pIdFilepassword,
	char *pPKCS12Filename,
	char *pPKCS12Filepassword,
	DWORD  ExportFlags,
	DWORD  ReservedFlags,
	void *pReserved);
```
**Description :**

Writes the key and the certificates found in an ID file to a Public Key C
ryptography Standards #12 file.  This function is supported for Windows 32-bit, 
IBM AIX and Macintosh platforms only. 

**Parameters :**
Input :
pIdFilename  -  Pointer of the name of an ID file to be processed.

pIdFilepassword  -  Pointer of the password of an ID file to be processed.

pPKCS12Filename  -  Pointer of the name of a PKCS 12 file.

pPKCS12Filepassword  -  Pointer of the password of a PKCS 12 file.

ExportFlags  -  0 or one of the values defined in PKCS12_xxx.

ReservedFlags  -  Reserved for future expansion.  Should be set to 0.

pReserved  -  Reserved for future expansion.  Should be set to NULL.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[PKCS12_ImportFileToIDFile](/reference/Func/PKCS12_ImportFileToIDFile)
[PKCS12_xxx](/reference/Symb/PKCS12_xxx)
---

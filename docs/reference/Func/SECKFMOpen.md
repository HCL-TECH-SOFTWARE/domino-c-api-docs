##### Function : IDs
##### SECKFMOpen - Open an ID file.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECKFMOpen(

	KFHANDLE *phKFC,
	char *pIDFileName,
	char *pPassword,
	DWORD  Flags,
	DWORD  Reserved,
	void *pReserved);
```
**Description :**

This routine will read all the information in the ID file and return a handle 
to it.

**Parameters :**
Input :

pIDFileName  -  Name of ID file to be read.

pPassword  -  Null terminated password string.

Flags  -  Zero or SECKFM_open_All will read all information out of the id file.  See SECKFM_xxx.

Reserved  -  Reserved for future use, should be set to zero.

pReserved  -  Reserved for future use, should be set to NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.   The return codes include:

NOERROR - action successful


phKFC  -  ID file handle to be passed back upon successful opening of the id file.


**See Also :**
[SECKFM_xxx](/domino-c-api-docs/reference/Symb/SECKFM_xxx)
---

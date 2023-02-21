##### Function : IDs
##### SECKFMClose - Close an ID file.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECKFMClose(

	KFHANDLE *phKFC,
	DWORD  Flags,
	DWORD  Reserved,
	void *pReserved);
```
**Description :**

This routine will close the ID file.  If the Flags parameter is set it will 
write the information contained in the handle out to the ID file specified, 
otherwise it will clear the handle passed in and set it to NULL before closing 
it.

**Parameters :**
Input :
phKFC  -  Pointer to id file handle to be closed.

Flags  -  Write the information contained in the handle out to ID file otherwise set to 0.  See SECKFM_close_WriteIdFile in SECKFM_xxx.

Reserved  -  Reserved for future use, should be set to 0.

pReserved  -  Reserved for future use, should be set to NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.   The return codes include:

NOERROR - action successful



**See Also :**
[SECKFMOpen](/domino-c-api-docs/reference/Func/SECKFMOpen)
[SECKFM_xxx](/domino-c-api-docs/reference/Symb/SECKFM_xxx)
---

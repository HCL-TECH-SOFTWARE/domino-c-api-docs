##### Function : encryption
##### NSFCipherDestroy - Destroy a CIPHERHANDLE
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFCipherDestroy(

	CIPHERHANDLE *phCipher);
```
**Description :**

Destroy a CIPHERHANDLE that was returned as an output argument from another NSF 
function.  Returns NOERROR if phCipher is NULL or *phCipher is 
NULLCIPHERHANDLE.

**Parameters :**
Input :
phCipher  -  Handle for a cryptographic operation

Output :
(routine)  -  Return status from this call.
	NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**See Also :**
---

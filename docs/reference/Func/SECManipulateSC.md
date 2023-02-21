##### Function : Smartcards
##### SECManipulateSC - Smartcard manipulation function.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECManipulateSC(

	DWORD  OpCode,
	SCMCTX *pContext,
	DWORD *pdwFlags,
	DWORD *pdwParam1,
	void *pvParam2);
```
**Description :**

Depending on OpCode specified, this function will manipulate a Smartcard 
context.

**Parameters :**
Input :
OpCode  -  Indicates the action being performed by the operation.  See SC_manip_xxx.

pContext  -  The address of a pointer to an opaque context blob.  See SCMCTX, NULLSCMCTX and SC_manip_xxx.

pdwFlags  -  Context sensitive input, based on the OpCode.  See SC_manip_xxx.

pdwParam1  -  Context sensitive input, based on the OpCode.  See SC_manip_xxx.

pvParam2  -  Context sensitive input, based on the OpCode.  See SC_manip_xxx.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 


pContext  -  The address of a pointer to an opaque context blob.


**See Also :**
[NULLSCMCTX](/domino-c-api-docs/reference/Symb/NULLSCMCTX)
[SCMCTX](/domino-c-api-docs/reference/Data/SCMCTX)
[SC_manip_xxx](/domino-c-api-docs/reference/Symb/SC_manip_xxx)
---

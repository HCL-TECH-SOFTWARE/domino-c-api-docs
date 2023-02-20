##### Function : Compound Text 
##### CompoundTextAssimilateBuffer - Append the contents in PABID's (Personal Address Book ID's )  of a compound text buffer to a compound text context.
---
```
#include <easycd.h>
STATUS CompoundTextAssimilateBuffer(

	DHANDLE  hCompound,
	void *pvData,
	DWORD  dwDataLen);
```
**Description :**

Append the contents of a compound text buffer to a compound text context. 

The contents are adjust  in that PABID's (Personal Address Book ID's ) and 
styles defined in the source are renumbered and/or renamed as necessary to fit 
into the destination context.

**Parameters :**
Input :
hCompound  -  Compound context handle.

pvData  -  Void pointer to store the data.

dwDataLen  -  Length, in bytes, of the data provide in pData.

Output :
(routine)  -  if error ,returns ERR_MISC_INVALID_ARGS error ,else NOERROR.



**Sample Usage :**
```
	void *pvData = OSLock(void, hMainOutputBuffer); 
	DWORD dwLen = 0; 
	STATUS error = OSMemGetSize(hMainOutputBuffer, &dwLen); 
	if (NOERROR == error) 
	 error = CompoundTextAssimilateBuffer(hCompound, pvData, dwLen); 
	OSUnlock(hMainOutputBuffer);
```
**See Also :**
---

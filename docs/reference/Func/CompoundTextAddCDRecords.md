##### Function : Compound Text
##### CompoundTextAddCDRecords - Add CD records to an existing CompoundText context.
---
```
#include <easycd.h>
STATUS LNPUBLIC CompoundTextAddCDRecords(

	DHANDLE  hCompound,
	void *pvRecord,
	DWORD  dwRecordLength);
```
**Description :**

This function adds a buffer of formatted CD records to an existing CompoundText 
context.

**Parameters :**
Input :
hCompound  -  Handle of CompoundText context.

pvRecord  -  A pointer to a buffer of formatted CD records.

dwRecordLength  -  The length of the buffer.

Output :
(routine)  -  (routine)  -    Return status from this call: 

NOERROR - Successfully added the buffer to the CompoundText context.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**See Also :**
[CompoundTextClose](/reference/Func/CompoundTextClose)
[CompoundTextCreate](/reference/Func/CompoundTextCreate)
---

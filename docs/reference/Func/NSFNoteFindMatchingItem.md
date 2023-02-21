##### Function : Note
##### NSFNoteFindMatchingItem - Find item in one note that matches the same item in another.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteFindMatchingItem(

	NOTEHANDLE  hNote1,
	BLOCKID  bhItem1,
	NOTEHANDLE  hNote2,
	DWORD  dwFlags,
	BLOCKID *retbhItem2);
```
**Description :**

This routine returns the BLOCKID of an item in one note that matches the same 
item in another note.  Two items match if the item name one matches the item 
name of the other.  This function is useful for replication conflict handlers.

**Parameters :**
Input :
hNote1  -  Handle of the first note.

bhItem1  -  BLOCKID of the source item.

hNote2  -  Handle of the second note.

dwFlags  -  Reserved for future use.  Must be set to 0L.

Output :
(routine)  -  NOERROR - Successfully found a matching item.
ERR_ITEM_NOT_FOUND - A matching item was not found in the second note.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


retbhItem2  -  BLOCKID of the matching item.


**See Also :**
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[NSFNoteFindDivergenceTime](/domino-c-api-docs/reference/Func/NSFNoteFindDivergenceTime)
[NSFItemGetModifiedTime](/domino-c-api-docs/reference/Func/NSFItemGetModifiedTime)
[NSFItemGetModifiedTimeByBLOCKID](/domino-c-api-docs/reference/Func/NSFItemGetModifiedTimeByBLOCKID)
---

##### Function : Item (Field)
##### NSFItemGetModifiedTime - Get the last modified time for an item.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemGetModifiedTime(

	DHANDLE  hNote,
	const char *ItemName,
	WORD  ItemNameLength,
	DWORD  Flags,
	TIMEDATE *retTime);
```
**Description :**

Find the first item of the given name in a note and return its last modified 
time.

**Parameters :**
Input :
hNote  -  The note handle.  If this handle is NULLHANDLE, then the retTime argument is cleared (TimeDateClear is performed on retTime) and NSFItemGetModifiedTime returns NOERROR.

ItemName  -  The item name.

ItemNameLength  -  The length of the item name or MAXWORD for null terminated strings.

Flags  -  Reserved for future use.  Must be set to 0L.

Output :
(routine)  -  NOERROR - Successfully got the time the item was last modified.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


retTime  -  Time that the item was last updated to the note.


**See Also :**
[NSFItemGetModifiedTimeByBLOCKID](/domino-c-api-docs/reference/Func/NSFItemGetModifiedTimeByBLOCKID)
---

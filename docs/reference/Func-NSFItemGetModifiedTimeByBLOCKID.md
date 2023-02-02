##### Function : Item (Field)
##### NSFItemGetModifiedTimeByBLOCKID - Get the last modified time for an item, given the item's BLOCKID.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFItemGetModifiedTimeByBLOCKID(**

	DHANDLE  hNote,
	BLOCKID  bhItem,
	DWORD  Flags,
	TIMEDATE *retTime);
**Description :**
Find an item with a given BLOCKID and return the time it was last modified. The 
BLOCKID can easily be found using the call NSFItemInfo.
**Parameters :**
Input :
hNote  -  The note handle.  If this handle is NULLHANDLE, then the retTime argument is cleared (TimeDateClear is performed on retTime) and NSFItemGetModifiedTimeByBLOCKID returns NOERROR.

bhItem  -  The BLOCKID for the item we are interested in.

Flags  -  Reserved for future use.  Must be set to 0L.

Output :
(routine)  -  NOERROR - Successfully got the last modified time
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


retTime  -  Time that the item was last updated to the note.

**See Also :**
[NSFItemGetModifiedTime](D:/md_files/NSFItemGetModifiedTime.md)
---

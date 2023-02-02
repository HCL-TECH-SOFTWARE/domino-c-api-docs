##### Function : MIME
##### NSFMimePartGetPart - returns the MIME_PART ODS structure for a given TYPE_MIME_PART item.
---
##### #include <nsfmime.h>
STATUS LNPUBLIC **NSFMimePartGetPart(**

	BLOCKID  bhItem,
	DHANDLE *phPart);
**Description :**
The function NSFMimePartGetPart returns the MIME_PART ODS structure for a 
TYPE_MIME_PART item, given its BLOCKID.  The caller is responsible for freeing 
the block of memory in which the MIME_PART is returned.
**Parameters :**
Input :
bhItem  -  the BLOCKID for the TYPE_MIME_PART item.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully added the MIME part.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



phPart  -  pointer to location for the handle to the allocated memory containing the MIME_PART.

**Sample Usage :**
```
STATUS error;
BLOCKID bhValue;
DWORD dwValueLen;
BLOCKID bhItem;
DHANDLE hPart;
MIME_PART *pPart;

if (error = NSFItemInfo(hNote,
    MAIL_BODY_ITEM,
    sizeof(MAIL_BODY_ITEM)-1,
    &bhItem,
    NULL,
    &bhValue,
    &dwValueLen)) {
 goto exit;
}

if (error = NSFMimePartGetPart(bhItem, &hPart)) {
 goto exit;
}

pPart = OSLock(MIME_PART, hPart);

/* perform ODS operations... */

OSUnlockAndFree(hPart);

```
**See Also :**
[BLOCKID](D:/md_files/BLOCKID.md)
[NSFItemInfo](D:/md_files/NSFItemInfo.md)
[NSFMimePartGetInfo](D:/md_files/NSFMimePartGetInfo.md)
[NSFMimePartGetInfoByBLOCKID](D:/md_files/NSFMimePartGetInfoByBLOCKID.md)
[NSFMimePartGetInfoNext](D:/md_files/NSFMimePartGetInfoNext.md)
---

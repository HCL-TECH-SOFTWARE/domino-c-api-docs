##### Function : MIME
##### NSFMimePartGetInfo - get information about a named MIME part item.
---
##### #include <nsfmime.h>
STATUS LNPUBLIC **NSFMimePartGetInfo(**

	NOTEHANDLE  hNote,
	char *pchItemName,
	WORD  wItemNameLen,
	WORD *pwPartType,
	DWORD *pdwFlags,
	WORD *pwReserved,
	WORD *pwPartLen,
	BLOCKID *pbhItem);
**Description :**
The function NSFMimePartGetInfo returns information about a named 
TYPE_MIME_PART item in an open note.  The returned BLOCKID, bhItem, is the 
BLOCKID for the first item of name 'pchItemName' found by NSFMimePartGetInfo.
**Parameters :**
Input :
hNote  -  a handle to an open note.

pchItemName  -  Pointer to buffer containing item name to use; typically should be MAIL_BODY_ITEM.

wItemNameLen  -   item name length.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully fetched the MIME part info.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



pwPartType  -  pointer to location for the returned MIME part type.

pdwFlags  -  pointer to location for the returned MIME part flags.

pwReserved  -  reserved -- presently unused.

pwPartLen  -  pointer to location for returned part data length in bytes.

pbhItem  -  pointer to location for returned BLOCKID for MIME part item.

**Sample Usage :**
```
    STATUS error;
WORD wPartType;
DWORD dwFlags;
WORD wReserved;
WORD wPartLen;
BLOCKID bhItem;

if (error = NSFMimePartGetInfo(hNote,
	     MAIL_BODY_ITEM,
	     sizeof(MAIL_BODY_ITEM)-1,
	     &wPartType,
	     &dwFlags,
	     &wReserved,
	     &wPartLen,
	     &bhItem)) {
	goto exit;
}

```
**See Also :**
[BLOCKID](D:/md_files/BLOCKID.md)
[NOTEHANDLE](D:/md_files/NOTEHANDLE.md)
[NSFMimePartGetInfoByBLOCKID](D:/md_files/NSFMimePartGetInfoByBLOCKID.md)
[NSFMimePartGetInfoNext](D:/md_files/NSFMimePartGetInfoNext.md)
---

##### Function : MIME
##### NSFMimePartGetInfoNext - get information about a subsequent named MIME part item.
---
```
#include <nsfmime.h>
STATUS LNPUBLIC NSFMimePartGetInfoNext(

	NOTEHANDLE  hNote,
	BLOCKID  bhItem,
	char *pchItemName,
	WORD  wItemNameLen,
	WORD *pwPartTyp,
	DWORD *pdwFlags,
	WORD *pwReserved,
	WORD *pwPartLen,
	BLOCKID *pbhItemNext);
```
**Description :**

The function NSFMimePartGetInfoNext returns information about a subsequent 
named TYPE_MIME_PART item in an open note, using the BLOCKID returned by 
NSFMimePartGetInfo for the first named TYPE_MIME_PART item.  The returned 
BLOCKID, bhItemNext, is the BLOCKID for the just fetched item of name 
'pchItemName', to be passed as bhItem on subsequent calls to 
NSFMimePartGetInfoNext.


**Parameters :**
Input :
hNote  -  a handle to an open note.

bhItem  -  BLOCKID for the current TYPE_MIME_PART of the given name.

pchItemName  -  Pointer to buffer containing item name to use; typically should be MAIL_BODY_ITEM.

wItemNameLen  -  item name length.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully fetched the MIME part info.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



pwPartTyp  -  pointer to location for the returned MIME part type.

pdwFlags  -  pointer to location for the returned MIME part flags.

pwReserved  -  reserved -- presently unused.

pwPartLen  -  pointer to location for returned part data length in bytes.

pbhItemNext  -  pointer to location for returned BLOCKID for next MIME part item.


**Sample Usage :**
```
STATUS error;
WORD wPartType;
DWORD dwFlags;
WORD wReserved;
WORD wPartLen;
BLOCKID bhItem;
BLOCKID bhItemNext;
int n = 0;

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

while (!ISNULLBLOCKID(bhItem)) {
	++n;

	if (error = NSFMimePartGetInfoNext(hNote,
	          bhItem,
	          MAIL_BODY_ITEM,
	          sizeof(MAIL_BODY_ITEM)-1,
	          &wPartType,
	          &dwFlags,
	          &wReserved,
	          &wPartLen,
	          &bhItemNext)) {
	 goto exit;
	}

	bhItem = bhItemNext;
}

```
**See Also :**
[BLOCKID](/domino-c-api-docs/reference/Data/BLOCKID)
[NOTEHANDLE](/domino-c-api-docs/reference/Data/NOTEHANDLE)
[NSFMimePartGetInfo](/domino-c-api-docs/reference/Func/NSFMimePartGetInfo)
[NSFMimePartGetInfoByBLOCKID](/domino-c-api-docs/reference/Func/NSFMimePartGetInfoByBLOCKID)
---

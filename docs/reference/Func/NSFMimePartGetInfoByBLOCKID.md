##### Function : Mail
##### NSFMimePartGetInfoByBLOCKID - given its BLOCKID, get information about a MIME part item.
---
```
#include <nsfmime.h>
STATUS LNPUBLIC NSFMimePartGetInfoByBLOCKID(

	BLOCKID  bhItem,
	WORD *pwPartType,
	DWORD *pdwFlags,
	WORD *pwReserved,
	WORD *pwPartOffset,
	WORD *pwPartLen,
	WORD *pwBoundaryOffset,
	WORD *pwBoundaryLen,
	WORD *pwHeadersOffset,
	WORD *pwHeadersLen,
	WORD *pwBodyOffset,
	WORD *pwBodyLen);
```
**Description :**

The function NSFMimePartGetInfoByBLOCKID returns information about a 
TYPE_MIME_PART item in an open note, given its BLOCKID.  If wBoundaryLen or 
wHeadersLen are returned as 0, there is no boundary or headers, respectively, 
for the TYPE_MIME_PART item.


**Parameters :**
Input :
bhItem  -  the BLOCKID for the TYPE_MIME_PART item.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully fetched the MIME part info.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



pwPartType  -  pointer to location for the returned MIME part type.

pdwFlags  -  pointer to location for the returned MIME part flags.

pwReserved  -  reserved -- presently unused.

pwPartOffset  -  offset of the MIME part data within the TYPE_MIME_PART item; i.e., after the MIME_PART ODS structure.

pwPartLen  -  pointer to location for returned part data length in bytes.

pwBoundaryOffset  -  offset of the part boundary, if any, within the TYPE_MIME_PART item; i.e., after the MIME_PART ODS structure.

pwBoundaryLen  -  length of the boundary.

pwHeadersOffset  -  offset of the part headers, if any, within the TYPE_MIME_PART item; i.e., after the MIME_PART ODS structure.

pwHeadersLen  -  length of the headers.

pwBodyOffset  -  offset of the part body within the TYPE_MIME_PART item; i.e., after the MIME_PART ODS structure.

pwBodyLen  -  length of the body.


**Sample Usage :**
```
    STATUS error;
BLOCKID bhValue;
DWORD dwValueLen;
BLOCKID bhItem;
WORD wPartType;
DWORD dwFlags;
WORD wReserved;
WORD wPartOffset;
WORD wPartLen;
WORD wBoundaryOffset;
WORD wBoundaryLen;
WORD wHeadersOffset;
WORD wHeadersLen;
WORD wBodyOffset;
WORD wBodyLen;

if (error = NSFItemInfo(hNote,
	   MAIL_BODY_ITEM,
	   sizeof(MAIL_BODY_ITEM)-1,
	   &bhItem,
	   NULL,
	   &bhValue,
	   &dwValueLen)) {
	goto exit;
}

if (error = NSFMimePartGetInfoByBLOCKID(bhItem,
	         &wPartType,
	         &dwFlags,
	         &wReserved,
	         &wPartOffset,
	         &wPartLen,
	         &wBoundaryOffset,
	         &wBoundaryLen,
	         &wHeadersOffset,
	         &wHeadersLen,
	         &wBodyOffset,
	         &wBodyLen)) {
	goto exit;
}

```
**See Also :**
[BLOCKID](/reference/Data/BLOCKID)
[NSFMimePartGetInfo](/reference/Func/NSFMimePartGetInfo)
[NSFMimePartGetInfoNext](/reference/Func/NSFMimePartGetInfoNext)
---

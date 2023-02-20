##### Function : MIME
##### MIMEConvertRFC822TextItemByBLOCKID - Convert a TYPE_RFC822_TEXT item into it's pre-V5 equivalent.
---
```
#include <mime.h>
STATUS LNPUBLIC MIMEConvertRFC822TextItemByBLOCKID(

	NOTEHANDLE  hNote,
	BLOCKID  bhItem,
	BLOCKID  bhValue);
```
**Description :**

This function converts the input TYPE_RFC822_TEXT item in an open note to its 
pre-V5 equivalent; i.e. to TYPE_TEXT, TYPE_TEXT_LIST, or TYPE_TIME.    It does 
not update the Domino database; to update the database, call NSFNoteUpdate.

You must specify as input the handle to the open note, a BLOCKID for the item, 
and a BLOCKID for the item value.

MIMEConvertRFC822TextItem converts the named input item to the appropriate 
pre-V5 item type.  For example, MIMEConvertRFC822TextItem converts the 
PostedDate TYPE_RFC822_TEXT item to a TYPE_TIME item.  (PostedDate is the Notes 
equivalent of the 'Date:' header in Internet format messages; see also the 
discussion of the MIMEHeaderNameToItemName and MIMEItemNameToHeaderName APIs 
below for information on mapping between Notes item names and Internet message 
header names.)


**Parameters :**
Input :
hNote  -  The handle to the open note containing the item to be converted.

bhItem  -  BLOCKID for the item.

bhValue  -  BLOCKID for the item value.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully converted the item.
	ERR_MISC_INVALID_ARGS - Item is not a TYPE_RFC822_TEXT item.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.




**Sample Usage :**
```
BLOCKID bhItem;
BLOCKID bhValue;
WORD wDataType;
DWORD dwValueLen;
STATUS error;

if (error = NSFItemInfo(hNote,
	   MAIL_POSTEDDATE_ITEM, sizeof(MAIL_POSTEDDATE_ITEM)-1,
	   &bhItem, &wDataType, &bhValue, &dwValueLen)) {
	goto exit;
}

if (error = MIMEConvertRFC822TextItemByBLOCKID(hNote, bhItem, bhValue)) {
	goto exit;
}

```
**See Also :**
[BLOCKID](/reference/Data/BLOCKID)
[NOTEHANDLE](/reference/Data/NOTEHANDLE)
---

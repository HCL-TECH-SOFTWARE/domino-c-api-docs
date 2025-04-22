##### Function : MIME
##### MIMEConvertRFC822TextItem - Convert a TYPE_RFC822_TEXT item into its pre-V5 equivalent.
---
```
#include <mime.h>
STATUS LNPUBLIC MIMEConvertRFC822TextItem(

	NOTEHANDLE  hNote,
	char *pszItemName,
	WORD  the string length of the item name.);
```
**Description :**

This function converts the input TYPE_RFC822_TEXT item in an open note to its 
pre-V5 equivalent; i.e. to TYPE_TEXT, TYPE_TEXT_LIST, or TYPE_TIME.    It does 
not update the Domino database; to update the database, call NSFNoteUpdate.

You must specify as input the handle to the open note, a pointer to the item 
name (an ASCIIZ string), and the length of the item name.

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

pszItemName  -  Pointer to the ASCIIZ item name.

the string length of the item name.  -  the string length of the item name.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully converted the item.
	ERR_MISC_INVALID_ARGS - Item is not a TYPE_RFC822_TEXT item.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.




**Sample Usage :**
```
STATUS error;

if (error = MIMEConvertRFC822TextItem(hNote, MAIL_POSTEDDATE_ITEM, 
sizeof(MAIL_POSTEDDATE_ITEM)-1)) {
	goto exit;
}

```
**See Also :**
[MIMEConvertMIMEPartCC](/domino-c-api-docs/reference/Func/MIMEConvertMIMEPartCC)
[MIMEConvertMIMEPartsCC](/domino-c-api-docs/reference/Func/MIMEConvertMIMEPartsCC)
---

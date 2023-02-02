##### Function : MIME
##### MIMEConvertRFC822TextItems - Convert all TYPE_RFC822_TEXT items into their pre-V5 equivalents.
---
##### #include <mime.h>
STATUS LNPUBLIC **MIMEConvertRFC822TextItems(**

	NOTEHANDLE  hNote,
	BOOL  bCanonical);
**Description :**
This function converts the all TYPE_RFC822_TEXT items in an open note to their 
pre-V5 equivalents; i.e., to TYPE_TEXT, TYPE_TEXT_LIST, or TYPE_TIME.    It 
does not update the Domino database; to update the database, call NSFNoteUpdate.

You must specify as input the handle to the open note and a BOOLEAN value 
indicating if the note was opened in canonical format (TRUE) or host format 
(FALSE).

MIMEConvertRFC822TextItems converts all TYPE_RFC822_TEXT items to the 
appropriate pre-V5 item types.  For example, MIMEConvertRFC822TextItems 
converts the PostedDate TYPE_RFC822_TEXT item to a TYPE_TIME item.  (PostedDate 
is the Notes equivalent of the 'Date:' header in Internet format messages; see 
also the discussion of the MIMEHeaderNameToItemName and 
MIMEItemNameToHeaderName APIs below for information on mapping between Notes 
item names and Internet message header names.)

**Parameters :**
Input :
hNote  -  The handle to the open note containing the item to be converted.

bCanonical  -  bCanonical

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully converted the item.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**Sample Usage :**
```
WORD wNoteFlags;
BOOL bCanonical;
STATUS error;

NSFNoteGetInfo(hNote, _NOTE_FLAGS, &wNoteFlags);

bCanonical = (wNoteFlags & NOTE_FLAG_CANONICAL) != 0;

if (error = MIMEConvertRFC822TextItems(hNote, bCanonical)) {
	goto exit;
}

```
**See Also :**
[](D:/md_files/.md)
---

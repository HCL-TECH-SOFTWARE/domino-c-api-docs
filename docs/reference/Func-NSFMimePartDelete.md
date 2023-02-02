##### Function : MIME
##### NSFMimePartDelete - delete a TYPE_MIME_PART item from a note.
---
##### #include <nsfmime.h>
STATUS LNPUBLIC **NSFMimePartDelete(**

	NOTEHANDLE  hNote,
	char *pchItemName,
	WORD  wItemNameLen);
**Description :**
The function NSFMimePartDelete deletes the TYPE_MIME_PART items named 
pchItemName from an open note.  NSFMimePartDelete does not delete the object 
associated with a given TYPE_MIME_PART item if the object is shared. 

**Parameters :**
Input :
hNote  -  a handle to an open note.

pchItemName  -  a pointer to the TYPE_MIME_PART item name.

wItemNameLen  -  the length of the item name.

Output :
(routine)  -   Return status from this call.
	NOERROR - Successfully added the MIME part.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**Sample Usage :**
```
    STATUS error;

if (error = NSFMimePartDelete(hNote, MAIL_BODY_ITEM, sizeof(MAIL_BODY_ITEM)-1)) 
{
	goto exit;
}

```
**See Also :**
[NSFMimePartAppend](D:/md_files/NSFMimePartAppend.md)
---

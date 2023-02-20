##### Function : MIME
##### NSFMimePartCreateStream - Creates a context for streaming a large MIME part to a note item.  All other NSFMimePart*Stream functions use this context.
---
```
#include <nsfmime.h>
STATUS LNPUBLIC NSFMimePartCreateStream(

	NOTEHANDLE  hNote,
	char *pchItemName,
	WORD  wItemNameLen,
	WORD  wPartType,
	DWORD  dwFlags,
	DHANDLE *phCtx);
```
**Description :**

The function NSFMimePartCreateStream creates a MIME part context for adding 
large MIME parts to a named note item.  Subsequent calls to 
NSFMimePartAppendStream. NSFMimePartAppendFileToStream, or 
NSFMimePartAppendFileToStream require the MIME part context as input.


**Parameters :**
Input :
hNote  -  a handle to an open note.

pchItemName  -  the name of the item in which to store the appended MIME data.

wItemNameLen  -  the length of the item name.

wPartType  -  the type of MIME part item to create; MIME_PART_PROLOG, MIME_PART_BODY, MIME_PART_EPILOG, etc.

dwFlags  -   flags for the MIME part; MIME_PART_HAS_BOUNDARY, MIME_PART_HAS_HEADERS, etc.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully create the MIME part context.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



phCtx  -  a pointer to a location for the output handle to the context.


**Sample Usage :**
```
    STATUS error;
DHANDLE hCtx;

if (err = NSFMimePartCreateStream(hNote,
	        MAIL_BODY_ITEM,
	        sizeof(MAIL_BODY_ITEM)-1,
	        MIME_PART_BODY,
	        MIME_PART_HAS_BOUNDARY | MIME_PART_HAS_HEADERS,
	        &hCtx)) {
	goto exit;
}

```
**See Also :**
[MIMEPARTTYPE](/reference/Data/MIMEPARTTYPE)
[MIME_PART_xxx](/reference/Symb/MIME_PART_xxx)
[NOTEHANDLE](/reference/Data/NOTEHANDLE)
[NSFMimePartAppendStream](/reference/Func/NSFMimePartAppendStream)
[NSFMimePartCloseStream](/reference/Func/NSFMimePartCloseStream)
---

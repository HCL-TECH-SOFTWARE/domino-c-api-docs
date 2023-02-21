##### Function : MIME
##### NSFMimePartAppendStream - Appends data to a MIME part item.
---
```
#include <nsfmime.h>
STATUS LNPUBLIC NSFMimePartAppendStream(

	DHANDLE  hCtx,
	char *pchData,
	WORD  wDataLen);
```
**Description :**

The function NSFMimePartAppendStream appends the data pointed to by pchData to 
the MIME part context created by NSFMimePartCreateStream.  
NSFMimePartCloseStream must be called to "flush" the context to the item 
originally specified on the calls to NSFMimePartCreateStream.  In addition 
NSFMimePartCloseStream frees all memory associated with the MIME part context.

N.B., When line endings are used --e.g., with boundary lines or headers-- the 
line ending must be carriage return, line feed, ASCII values 13 and 10, 
respectively.  NSFMimePartAppendStream will not function correctly if UNIX 
(line feed) or Mac (carriage return) line endings are used.


**Parameters :**
Input :
hCtx  -  the handle to the MIME part context.

pchData  -  pointer to the data to append to the MIME part context.

wDataLen  -  the length of the data.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully appended the data to the MIME part context..
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.




**Sample Usage :**
```
    STATUS error;
DHANDLE hCtx;
char *pszBoundary = "\015\012--Boundary_String\015\012";
char *pszHeaders = "Content-type: text/plain\015\012\015\012";
char *pszBody = "This is the body of a text/plain MIME part.\015\012";

if (err = NSFMimePartCreateStream(hNote,
	        MAIL_BODY_ITEM,
	        sizeof(MAIL_BODY_ITEM)-1,
	        MIME_PART_BODY,
	        MIME_PART_HAS_BOUNDARY | MIME_PART_HAS_HEADERS,
	        &hCtx)) {
	goto exit;
}

if (error = NSFMimePartAppendStream(hCtx, pszBoundary, strlen(pszBoundary)) {
	goto exit;
}

if (error = NSFMimePartAppendStream(hCtx, pszHeaders, strlen(pszHeaders)) {
	goto exit;
}

if (error = NSFMimePartAppendStream(hCtx, pszBody, strlen(pszBody)) {
	goto exit;
}

```
**See Also :**
[NSFMimePartCloseStream](/domino-c-api-docs/reference/Func/NSFMimePartCloseStream)
[NSFMimePartCreateStream](/domino-c-api-docs/reference/Func/NSFMimePartCreateStream)
---

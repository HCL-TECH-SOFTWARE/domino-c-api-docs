##### Function : MIME
##### NSFMimePartCloseStream - Flush a MIME part context's data to a MIME part item and release all memory associated with the MIME part context.
---
```
#include <nsfmime.h>
STATUS LNPUBLIC NSFMimePartCloseStream(

	DHANDLE  hCtx,
	BOOL  bUpdate);
```
**Description :**

The function NSFMimePartCloseStream flushes the MIME part context's data to a 
MIME part item and releases all memory associated with the MIME part context.  
If bUpdate is FALSE (e.g., if closing the stream after some processing error), 
NSFMimePartCloseStream does not create the indicated MIME part item and it only 
frees the memory associated with the MIME part context.  The caller must set 
bUpdate to TRUE to force NSFMimePartCloseStream to create the indicated MIME 
part.


**Parameters :**
Input :
hCtx  -  a handle to the MIME part context.

bUpdate  -  if TRUE, create the indicated MIME part note item and free memory, otherwise only free memory.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully updated the note and closed the MIME part stream.
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

if (error = NSFMimePartAppendStream(hCtx, pszBoundary, strlen(pszBoundary))) {
	goto exit;
}

if (error = NSFMimePartAppendStream(hCtx, pszHeaders, strlen(pszHeaders))) {
	goto exit;
}

if (error = NSFMimePartAppendStream(hCtx, pszBody, strlen(pszBody))) {
	goto exit;
}

if (error = NSFMimePartCloseStream(hCtx, TRUE)) {
	goto exit;
}

```
**See Also :**
[NSFMimePartAppendStream](/reference/Func/NSFMimePartAppendStream)
[NSFMimePartCreateStream](/reference/Func/NSFMimePartCreateStream)
---

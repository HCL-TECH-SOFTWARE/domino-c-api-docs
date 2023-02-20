##### Function : MIME
##### NSFMimePartAppendObjectToStream - Associates a named database object (i.e., a file attachment) with the given MIME part context.
---
```
#include <nsfmime.h>
STATUS LNPUBLIC NSFMimePartAppendObjectToStream(

	DHANDLE  hCtx,
	char *pszAttachmentName);
```
**Description :**

The function NSFMimePartAppendObjectToStream associates a named attachment with 
the given MIME part stream.  Assumptions:

You have previously called NSFMimePartAppendStream to add the boundary, 
headers, and trailing CRLF to the MIME part.
You have previously specified the appropriate Content-Transfer-Encoding 
header.  If the named attachment is not encoded, specify "binary" encoding.
You should not call NSFMimePartAppendStream after 
NSFMimePartAppendObjectToStream. The next MimePartStream call should be 
NSFMimePartCloseStream.

**Parameters :**
Input :
hCtx  -  the handle to the MIME part context.

pszAttachmentName  -  the name of the database object (i.e., file attachment) from which to append data to the MIME part context.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully appended the data to the MIME part context..
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.




**Sample Usage :**
```
STATUS error;
DHANDLE hCtx;
char *pszBoundary = "\015\012--Boundary_String\015\012";
char *pszHeaders = "Content-type: image/jpeg\015\012"
	   "Content-Transfer-Encoding: binary\015\012"
	   "Content-Disposition: inline\015\012";

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

if (error = NSFMimePartAppendObjectToStream(hCtx, "picture.jpg") {
	goto exit;
}

if (error = NSFMimePartCloseStream(hCtx, TRUE)) {
	goto exit;
}

```
**See Also :**
[NSFMimePartAppend](/reference/Func/NSFMimePartAppend)
[NSFMimePartAppendFileToStream](/reference/Func/NSFMimePartAppendFileToStream)
[NSFMimePartCloseStream](/reference/Func/NSFMimePartCloseStream)
[NSFMimePartCreateStream](/reference/Func/NSFMimePartCreateStream)
---

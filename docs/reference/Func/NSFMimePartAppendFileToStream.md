##### Function : MIME
##### NSFMimePartAppendFileToStream - Append data from a file to a MIME part context.
---
```
#include <nsfmime.h>
STATUS LNPUBLIC NSFMimePartAppendFileToStream(

	DHANDLE  hCtx,
	char *pszFilename);
```
**Description :**

The function NSFMimePartAppendFileToStream opens the named input file and 
appends its data to the MIME part context using the supplied MIME part context 
handle.  Note that the data is always base64 encoded as it is written to the 
MIME part context and that the caller is responsible for appending any MIME 
part boundary or headers to the MIME part context before calling 
NSFMimePartAppendFileToStream.


**Parameters :**
Input :
hCtx  -  the handle to the MIME part context.

pszFilename  -  the name of the file from which to append data to the MIME part context.

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
	   "Content-Transfer-Encoding: base64\015\012"
	   "Content-Disposition: inline\015\012";

if (error = NSFMimePartCreateStream(hNote,
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

if (error = NSFMimePartAppendFileToStream(hCtx, "picture.jpg")) {
	goto exit;
}

if (error = NSFMimePartCloseStream(hCtx, TRUE)) {
	goto exit;
}

```
**See Also :**
---

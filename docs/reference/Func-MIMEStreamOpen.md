##### Function : MIME
##### MIMEStreamOpen - Open a MIME Stream for a MIME format note.
---
##### #include <mime.h>
STATUS LNPUBLIC **MIMEStreamOpen(**

	NOTEHANDLE  hNote,
	char *pchItemName,
	WORD  wItemNameLen,
	DWORD  dwOpenFlags,
	MIMEHANDLE *rethMIMEStream);
**Description :**
This function MIMEStreamOpen opens a MIME stream for MIME format note.  You 
must specify as input the handle to the open note, the name of the item to use 
to create the MIME stream, the length of the item name, the MIME stream open 
flags (see the MIME_STREAM_XXX flags), and a pointer to a MIMEHANDLE.  The 
MIMEHANDLE must be used on all subsequent calls to MIMEStream APIs.

On entry MIMEStreamOpen always writes a NULL to the output MIME handle 
location, *rethMIMEStream.  

If the flag MIME_STREAM_OPEN_READ is specified, MIMEStreamOpen creates a MIME 
stream, serializes the named items into it, and returns a MIMEHANDLE to the 
MIME stream.  Specify the flag MIME_STREAM_RFC2822_INCLUDE_HEADERS to flush all 
RFC2822 headers to the output MIME stream; i.e., the message's initial headers 
-- To, From, Subject, Date, etc.  Also specify the flag 
MIME_STREAM_OPEN_INCLUDE_HEADERS to flush all MIME entity headers to the output 
MIME stream.

If the flag MIME_STREAM_OPEN_WRITE is specified, MIMEStreamOpen ignores the 
pchItemName and wItemNameLen arguments.  MIMEStreamOpen creates a MIME stream 
and returns a MIMEHANDLE to the MIME stream.  (After completing output to the 
MIME stream using MIMEStreamPutLine or MIMEStreamWrite, specify the item name 
and its length on the subsequent call to MIMEStreamItemize.)

(N.B.  It is an error to specify both the MIME_STREAM_OPEN_READ and 
MIME_STREAM_OPEN_WRITE flags.  If both are specified, MIMEStreamOpen behaves as 
if only MIME_STREAM_OPEN_READ was specified.)

**Parameters :**
Input :
hNote  -  Handle to the open note

pchItemName  -  Pointer to the item name (does not have to be an ASCIIZ string).

wItemNameLen  -  The length of item name

dwOpenFlags  -  MIME Stream open flags

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully converted the note.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



rethMIMEStream  -  Pointer to a MIME stream handle.

**Sample Usage :**
```
STATUS error;
MIMEHANDLE hMIMEStream;

if (error = MIMEStreamOpen(hNote,
	      MAIL_BODY_ITEM,
	      sizeof(MAIL_BODY_ITEM)-1,
	      MIME_STREAM_OPEN_READ|MIME_STREAM_INCLUDE_HEADERS,
	      &hMIMEStream)) {
	goto exit;
}

```
**See Also :**
[MIMEHANDLE](D:/md_files/MIMEHANDLE.md)
[MIMEStreamClose](D:/md_files/MIMEStreamClose.md)
[MIMEStreamRead](D:/md_files/MIMEStreamRead.md)
[MIMEStreamWrite](D:/md_files/MIMEStreamWrite.md)
[MIME_STREAM_xxx](D:/md_files/MIME_STREAM_xxx.md)
---

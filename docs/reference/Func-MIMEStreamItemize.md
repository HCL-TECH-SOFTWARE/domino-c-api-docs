##### Function : MIME
##### MIMEStreamItemize - Parse a MIME stream to create a Notes/Domino MIME format document.
---
##### #include <mime.h>
STATUS LNPUBLIC **MIMEStreamItemize(**

	NOTEHANDLE  hNote,
	char *pchItemName,
	WORD  wItemNameLen,
	DWORD  dwFlags,
	MIMEHANDLE  hMIMEStream);
**Description :**
This function MIMEStreamItemize parses a MIME stream to create a Notes/Domino 
MIME format document.  You must specify as input a handle to an open note, 
optionally an item name to received the "itemized" MIME body parts, the length 
of the item name, the itemize flags, and the handle to the MIME stream.

If the dwFlags variable is 0, MIMEStreamItemize only itemizes the body parts of 
the input MIME stream.  If the pchItemName pointer is NULL or if pchItemName is 
equal to the null string (""), MIMEStreamItemize itemizes the MIME body parts 
into items named "Body".  If the dwFlags variable is set to MIME_STREAM_ITEMIZE 
headers, MIMEStreamItemize only parses and itemizes the MIME streams initial 
RFC2822 headers into Notes/Domino items; e.g., the Internet message header, 
'To:', is itemized to the Notes item, 'SendTo'.

MIMEStreamItemize itemizes the headers and the body parts of the input MIME 
stream if both the MIME_STREAM_ITEMIZE_HEADERS and MIME_STREAM_ITEMIZE_BODY 
flags are set in dwFlags.  (See the MIME_STREAM_ITEMIZE_XXX flags, especially 
MIME_STREAM_ITEMIZE_FULL.)

**Parameters :**
Input :
hNote  -  A handle to an open note.

pchItemName  -  An optional pointer to an item name.

wItemNameLen  -  The length of the item name.

dwFlags  -   The MIME stream itemize flags.

hMIMEStream  -  A handle to the MIME stream.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully converted the note.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**Sample Usage :**
```
STATUS error;

if (error = MIMEStreamItemize(hNote, MAIL_BODY_ITEM, sizeof(MAIL_BODY_ITEM)-1, 
MIME_STREAM_ITEMIZE_FULL, hMIMEStream)) {
	goto exit;
}

```
**See Also :**
[MIMEStreamPutLine](D:/md_files/MIMEStreamPutLine.md)
[MIME_STREAM_xxx](D:/md_files/MIME_STREAM_xxx.md)
---

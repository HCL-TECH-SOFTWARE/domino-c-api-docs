##### Function : MIME
##### MIMEGetText - get the MIME text for a given item name.
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEGetText(

	NOTEHANDLE  hNote,
	const char *pchItemName,
	WORD  wItemNameLen,
	BOOL  bNotesEOL,
	char *pchBuf,
	DWORD  dwMaxBufLen,
	DWORD *pdwBufLen);
```
**Description :**

The function MIMEGetText returns the text data from a MIME format note, up to 
the limit specified by dwMaxBufLen.  The item name typically should be 
MAIL_BODY_ITEM.  If the boolean bNotesEOL is TRUE, MIMEGetText will terminate 
lines using the Notes line terminator -- the NUL byte, '\0'.

MIMEGetText creates a MIME directory and traverses it searching for text 
parts.  MIMEGetText copies most text/* parts "as is" to the output buffer, 
pchBuf, but it 'filters' text/html parts, removing all HTML tags and writing 
only the renderable text to the output buffer.  MIMEGetText stores the number 
of bytes it wrote to the output buffer in the DWORD pointed to by pdwBufLen.

Note that MIMEGetText only processes the first text part found within a 
multipart/alternative, skipping any subsequent parts in the 
multipart/alternative.

(Note:  This procedure is essentially the same procedure used by the @Abstract 
function when it abstracts MIME documents.)


**Parameters :**
Input :
hNote  -  a handle to an open note

pchItemName  -  pointer to the item name for the MIME entities; typically MAIL_BODY_ITEM.

wItemNameLen  -  the length of the item name in bytes.

bNotesEOL  -  if TRUE, use Notes line terminators (NUL) at the end of lines; otherwise use carriage return, line feed.

dwMaxBufLen  -  the maximum number of bytes to write to the output buffer.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY and allocated the parameter value memory.
	ERR_MISC_INVALID_ARGS - returned for various input parameter errors.
	ERR_MIME_NO_DATA - returned if no MIME data for input item.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



pchBuf  -  pointer to the output buffer.

pdwBufLen  -  pointer to a DWORD for the number of bytes written to the output buffer.


**Sample Usage :**
```
#define MAXBUFLEN 512

HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
DWORD dwFlags;
char achBuf[MAXBUFLEN];
BOOL bNotesEOL = FALSE;
DWORD dwBufLen;

if (error = MIMEGetText(hNote,
	   MAIL_BODY_ITEM,
	   sizeof(MAIL_BODY_ITEM)-1,
	   bNotesEOL,
	   achBuf,
	   MAXBUFLEN,
	   &dwBufLen))
	goto exit;
}

```
**See Also :**
[NOTEHANDLE](/reference/Data/NOTEHANDLE)
[ITEM_xxx](/reference/Symb/ITEM_xxx)
---

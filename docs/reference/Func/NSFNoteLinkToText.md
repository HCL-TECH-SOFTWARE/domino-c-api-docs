##### Function : HTML
##### NSFNoteLinkToText - Convert NOTELINK to tagged text.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteLinkToText(

	char far *Title,
	NOTELINK far *NoteLink,
	char far *ServerHint,
	char far *LinkText,
	DHANDLE far *phLinkText,
	WORD far *pLinkTextLength,
	DWORD  Flags);
```
**Description :**

Converts a NOTELINK structure to tagged text note link format.  The format of 
the tagged text is described in the entry for NSFNoteLinkFromText().  A Domino 
memory object is allocated to store the tagged text;  the caller is responsible 
for freeing this memory object.

**Parameters :**
Input :
Title  -  Title string for the note link.

NoteLink  -  NOTELINK structure.

ServerHint  -  Text to be written to the <HINT> tag.

LinkText  -  Descriptive text to be written to the <REM> tag.

Flags  -  Note link option flags (see the entry for LINKFLAG_xxx).

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include: 

NOERROR - Conversion successful.


phLinkText  -  The handle to the memory object containing the tagged text note link is stored at this address.

pLinkTextLength  -  The size of the tagged text note link, in bytes, is written to this address.


**See Also :**
[LINKFLAG_xxx](/reference/Symb/LINKFLAG_xxx)
[NOTELINK](/reference/Data/NOTELINK)
[NSFNoteLinkFromText](/reference/Func/NSFNoteLinkFromText)
---

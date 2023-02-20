##### Function : HTML
##### NSFNoteLinkFromText - Convert tagged text to NOTELINK.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteLinkFromText(

	DHANDLE  hLinkText,
	WORD  LinkTextLength,
	NOTELINK far *NoteLink,
	char far *ServerHint,
	char far *LinkText,
	WORD  MaxLinkText,
	DWORD far *retFlags);
```
**Description :**

Converts a link to a note stored as tagged text to a NOTELINK structure.  The 
text containing the link must be stored in a Domino memory object.  The tagged 
text format for a note link is:

Link Title String
<NDL>
<REPLICA>85250123:006E4567</REPLICA>
<VIEW>OF85258901:00682345-ON8525ABCD:0065EF01</VIEW>
<NOTE>OF4E851234:A91A5678-ON85259ABC:004BDEF0</NOTE>
<HINT>CN=Ann/O=Iris</HINT>
<REM>Database 'Sample Database', View 'Example View', Document 'Title of 
Note'</REM>
<FLAGS ADDTEMPORARY=1 NOREPLSEARCH=1>
</NDL>



**Parameters :**
Input :
hLinkText  -  Handle to Notes memory object containing the link text.

LinkTextLength  -  Size, in bytes, of the link text.

MaxLinkText  -  Maximum number of bytes to copy to the LinkText address.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include: 

NOERROR - Conversion successful.
ERR_LINK_FORMAT - Format of the link text is invalid.


NoteLink  -  The NOTELINK structure is written to this address.

ServerHint  -  The string in the <HINT> tag is copied to this address.

LinkText  -  The string in the <REM> tag is copied to this address.

retFlags  -  Link flag bits are stored at this address (see the entry for LINKFLAG_xxx).


**See Also :**
[LINKFLAG_xxx](/reference/Symb/LINKFLAG_xxx)
[NOTELINK](/reference/Data/NOTELINK)
[NSFNoteLinkToText](/reference/Func/NSFNoteLinkToText)
---

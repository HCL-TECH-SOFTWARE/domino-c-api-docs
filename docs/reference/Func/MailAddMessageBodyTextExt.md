##### Function : Mail Gateway
##### MailAddMessageBodyTextExt - Converts a text file and adds it as body item(s) to a message, allowing use of NLS_INFO structure.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailAddMessageBodyTextExt(

	DHANDLE  hMessage,
	char far *ItemName,
	char far *InputFileName,
	DWORD  FontID,
	char far *LineDelim,
	WORD  ParaDelim,
	NLS_PINFO  pInfo);
```
**Description :**

This function converts a text file to composite text and adds it as body 
item(s) to a message, allowing the use of the NLS_INFO structure.  This 
function creates multiple items of the same name and therefore is not limited 
to 64KB of input.

**Parameters :**
Input :
hMessage  -  Open message handle.

ItemName  -  Text item name (null-terminated).  Optional - NULL is "Body".

InputFileName  -  Input file name string (null-terminated).

FontID  -  Font ID to be used.  Optional - 0 is 10pt Helv.

LineDelim  -  Line delimiter characters (e.g. "\r\n").  Optional - NULL is "" or null-terminated.  If the line delimiter character is not NULL, and if a line contains one or more null characters, this line will be ignored.

ParaDelim  -  Paragraph delimiter flags (PARADELIM_xxx).  Optional - 0 is PARADELIM_ANYBLANKLINE.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().  (NULL if body text already in the Lotus Multibyte Character Set (LMBCS)).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.




**See Also :**
[MailCreateBodyItem](/reference/Func/MailCreateBodyItem)
[MailAppendBodyItemLine](/reference/Func/MailAppendBodyItemLine)
---

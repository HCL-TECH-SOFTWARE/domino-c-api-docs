##### Function : MIME
##### MIMEOpenDirectory - create a MIMEDIRECTORY for an open Notes MIME format note.
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEOpenDirectory(

	NOTEHANDLE  hNote,
	HMIMEDIRECTORY *phMIMEDir);
```
**Description :**

This function MIMEOpenDirectory creates a MIMEDIRECTORY object for an open 
note.  You must specify as input a handle to an open note and a pointer to a 
MIMEDIRECTORY handle.

If the open note is a Notes MIME format document, MIMEOpenDirectory creates a 
tree structure to represent the various parts of the MIME document; RFC2822 
headers, MIME body part Content headers, MIME body parts, etc.

If the open note is a Notes Rich Text format document, MIMEOpenDirectory first 
converts the document to MIME format and then creates the MIMEDIRECTORY.

Elements and attributes of the MIMEDIRECTORY may be accessed via the various 
MIMEEntity APIs; see below for details.


**Parameters :**
Input :
hNote  -  a handle to an open note.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully opened the MIMEDIRECTORY.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



phMIMEDir  -  a pointer to a MIMEDIRECTORY handle.


**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[HMIMEDIRECTORY](/domino-c-api-docs/reference/Data/HMIMEDIRECTORY)
[MIMEFreeDirectory](/domino-c-api-docs/reference/Func/MIMEFreeDirectory)
---

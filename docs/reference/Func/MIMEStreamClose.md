##### Function : MIME
##### MIMEStreamClose - Close a MIME Stream for a MIME format note.
---
```
#include <mime.h>
void LNPUBLIC MIMEStreamClose(

	MIMEHANDLE  hMIMEStream);
```
**Description :**

This function MIMEStreamClose closes a previously opened MIME stream.  You must 
specify as input the handle to the MIME stream.


**Parameters :**
Input :
hMIMEStream  -  A MIME stream handle.

Output :
(routine)  -  none



**See Also :**
[MIMEHANDLE](/domino-c-api-docs/reference/Data/MIMEHANDLE)
[MIMEStreamOpen](/domino-c-api-docs/reference/Func/MIMEStreamOpen)
[MIMEStreamRead](/domino-c-api-docs/reference/Func/MIMEStreamRead)
[MIMEStreamWrite](/domino-c-api-docs/reference/Func/MIMEStreamWrite)
---

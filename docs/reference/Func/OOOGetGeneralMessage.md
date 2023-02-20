##### Function : OOO
##### OOOGetGeneralMessage - This function gets general message messages
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOGetGeneralMessage(

	OOOCTXPTR *pOOOContext,
	char *pGeneralMessage,
	WORD *pGeneralMessageLen);
```
**Description :**

OOO supports two sets of messages.  They are called General message/subject and 
Special message/subject.
This is function returns the handle to the text of the general message and the 
size of the memory containing the message.  

**Parameters :**
Input :
pOOOContext  -  Pointer obtained from the OOOStartOperation call

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 
NOERROR - Successfully performed this operation


pGeneralMessage  -  The text of the general message, the text may contain nulls. This is not a null terminated string, use pGeneralMessageLen  to determine size. The caller is responsible for allocating and freeing this memory.  This is an optional parameter. Pass in NULL pointer if you want to receive just the size information.

pGeneralMessageLen  -  The length of the text of the general message.  If  pGeneralMessage is not specified this is an ouput parameter. If pGeneralMessage is specified it is input/output parameter.  It specifies the maximum size of the returned text, and is updated if we have less text than the buffer size.


**See Also :**
[OOOSetGeneralMessage](/reference/Func/OOOSetGeneralMessage)
---

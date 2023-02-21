##### Function : OOO
##### OOOGetGeneralSubject - This function gets general subject messages
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOGetGeneralSubject(

	OOOCTXPTR *pOOOContext,
	char *pGeneralSubject);
```
**Description :**

OOO supports two sets of messages.  They are called General message/subject and 
Special message/subject. This function gets the general subject.  This is a 
zero terminated string that will appear as the subject line of the OOO 
notification. 

**Parameters :**
Input :
pOOOContext  -  Pointer obtained from the OOOStartOperation call

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 
NOERROR - Successfully performed this operation


pGeneralSubject  -  This is a zero terminated string that contains the subject line of the General message


**See Also :**
[OOOSetGeneralSubject](/domino-c-api-docs/reference/Func/OOOSetGeneralSubject)
---

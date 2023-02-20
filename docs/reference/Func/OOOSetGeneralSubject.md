##### Function : OOO
##### OOOSetGeneralSubject - This function sets general subject messages.
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOSetGeneralSubject(

	OOOCTXPTR *pOOOContext,
	const char *pGeneralSubject,
	BOOL  bDisplayReturnDate);
```
**Description :**

OOO supports two sets of notification messages.  They are called General 
message/subject and Special message/subject.The rest of the people will receive 
the general message/subject message. This function sets the general subject.If 
this field is not specified in by this API call, the value defined using Notes 
Client will be used, otherwise the default for this field is the following text
AUTO: Katherine Smith is out of the office (returning 02/23/2009 10:12:17 AM)

**Parameters :**
Input :
pOOOContext  -  Pointer obtained from the OOOStartOperation call 

pGeneralSubject  -  This is a pointer to a zero terminated string that will appear as the subject line of the OOO notification.

bDisplayReturnDate  -  This is a Boolean which controls whether (returning <date>) appears on the subject line.  Default value is TRUE.

Output :
(routine)  -  This is a Boolean which controls whether (returning <date>) appears on the subject line.  Default value is TRUE.



**See Also :**
[OOOGetGeneralSubject](/reference/Func/OOOGetGeneralSubject)
---

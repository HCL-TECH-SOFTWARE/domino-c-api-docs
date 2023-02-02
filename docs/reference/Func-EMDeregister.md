##### Function : Extension Manager
##### EMDeregister - Deregisters functions from Extension Manager
---
##### #include <extmgr.h>
STATUS LNPUBLIC **EMDeregister(**

	HEMREGISTRATION  hRegistration);
**Description :**
All functions registered to the Extension Manager must be deregistered using 
the registration handle that was returned from EMRegister.
**Parameters :**
Input :
hRegistration  -  Handle returned from call to EMRegister()

Output :
(routine)  -  Returns status codes from Domino or Notes core.
NOERROR
ERR_ILLEGALEXT


**See Also :**
[EMRegister](D:/md_files/EMRegister.md)
---

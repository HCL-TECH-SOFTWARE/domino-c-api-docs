##### Data Type : User Registration
##### REG_MISC_INFO - Structure that defines miscellaneous registration information.
---
```
#include <reg.h>
```

**Definition :**
```
typedef struct
	{
	DWORD  Size;   /* size of this structure - must initialize with sizeof 
(REG_MISC_INFO) */
	char  *Location;
	char  *Comment;
	char  *LocalAdminName;
	DWORD  Reserved[4];
	void  *pReserved[4];
	} REG_MISC_INFO;


```

**Description :**

This structure defines miscellaneous registration information for the REGNewPerson, REGNewCertifierExtended, and REGNewServerExtended2 functions.  The entire structure must
<ul><br>
be initialized to zero.<br>
<br>
The fields in the structure are (all fields that are not used must be NULL/O):<br>
<br>
Size		Size of this structure - must be initialized with sizeof (REG_MISC_INFO)<br>
Location		Location string added to be added to the newly created note<br>
Comment		Comment string added to be added to the newly created note<br>
LocalAdminName	Name of the local administrator to be added to the newly created note<br>
Reserved		Reserved - must be 0<br>
pReserved		Reserved - must be NULL</ul>



**See Also :**
[REGNewCertifierExtended](/domino-c-api-docs/reference/Func/REGNewCertifierExtended)
[REGNewPerson](/domino-c-api-docs/reference/Func/REGNewPerson)
[REGNewServerExtended2](/domino-c-api-docs/reference/Func/REGNewServerExtended2)
---

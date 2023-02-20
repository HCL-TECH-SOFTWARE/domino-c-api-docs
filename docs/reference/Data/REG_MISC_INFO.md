##### Data Type : User Registration
##### REG_MISC_INFO - Structure that defines miscellaneous registration information.
---
```
#include <reg.h>
```
**Description :**

This structure defines miscellaneous registration information for the 
REGNewPerson, REGNewCertifierExtended, and REGNewServerExtended2 functions.  
The entire structure must
be initialized to zero.

The fields in the structure are (all fields that are not used must be NULL/O):

Size  Size of this structure - must be initialized with sizeof (REG_MISC_INFO)
Location  Location string added to be added to the newly created note
Comment  Comment string added to be added to the newly created note
LocalAdminName Name of the local administrator to be added to the newly created 
note
Reserved  Reserved - must be 0
pReserved  Reserved - must be NULL

**See Also :**
[REGNewCertifierExtended](/reference/Func/REGNewCertifierExtended)
[REGNewPerson](/reference/Func/REGNewPerson)
[REGNewServerExtended2](/reference/Func/REGNewServerExtended2)
---

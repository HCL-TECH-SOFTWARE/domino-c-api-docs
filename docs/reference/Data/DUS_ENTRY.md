##### Data Type : Domino Upgrade Services
##### DUS_ENTRY - Represents one user or group being imported via a DUS process.
---
```
#include <dus.h>
```
**Description :**

An array of these structures is allocated by Domino and passed in to the DUS 
with DUSRetrieveUsers and DUSRetrieveGroups. The DUS fills in the data and the 
DUS_ENTRY is passed back to Domino, where the data is displayed in the "Foreign 
Directory Import" dialog box within the list of "Available users/groups" under 
registration for a user.  You are responsible for allocating memory for each 
DUS_ENTRY with OSMemAlloc() and freeing the memory with OSMemFree().

**See Also :**
[DUSRetrieveGroups](/domino-c-api-docs/reference/Func/DUSRetrieveGroups)
[DUSRetrieveUsers](/domino-c-api-docs/reference/Func/DUSRetrieveUsers)
---

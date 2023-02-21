##### Function : ID Table
##### IDTableTime - Returns the TIMEDATE structure that is stored in an ID Table.
---
```
#include <idtable.h>
TIMEDATE LNPUBLIC IDTableTime(

	void far *pIDTable);
```
**Description :**

This function returns the TIMEDATE structure that is stored in an ID Table.  
This storage is reserved for the caller usage and can be used to date an ID 
Table for later comparison with other versions of the same ID Table.

**Parameters :**
Input :
pIDTable  -  A pointer to an ID Table.

Output :
(routine)  -  Returns the TIMEDATE structure that is stored in the specified ID Table.



**Sample Usage :**
```
idtable_td = IDTableTime(idtable_ptr);
```
**See Also :**
[IDTableFlags](/domino-c-api-docs/reference/Func/IDTableFlags)
[IDTableSetFlags](/domino-c-api-docs/reference/Func/IDTableSetFlags)
[IDTableSetTime](/domino-c-api-docs/reference/Func/IDTableSetTime)
---

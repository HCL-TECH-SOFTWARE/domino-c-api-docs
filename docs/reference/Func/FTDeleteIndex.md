##### Function : Full Text Search
##### FTDeleteIndex - Deletes a full text index for a database.
---
```
#include <ft.h>
STATUS LNPUBLIC FTDeleteIndex(

	DBHANDLE  hDB);
```
**Description :**

This function deletes a full text index for a database.

This function does not disable full text indexing for a database.  In order to 
disable full text indexing for a database, use , NSFDbSetOption(hDb, 0, 
DBOPTION_FT_INDEX);

**Parameters :**
Input :
hDB  -  The handle to the open database.

Output :
(routine)  -   Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.



**See Also :**
[FTIndex](/reference/Func/FTIndex)
---

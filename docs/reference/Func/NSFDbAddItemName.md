##### Function : Database
##### NSFDbAddItemName - Adds an item to a database's Item Definition Table
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbAddItemName(

	DBHANDLE  hDB,
	WORD  type,
	char *string,
	WORD  length,
	DWORD *rtnItemNumber);
```
**Description :**

This function takes a database handle, an item name to be added to a database's 
Item Definition Table, the length of the item name and the type of item that is 
being named. It returns the item number of the item added to the Item 
Definition Table. 

**Parameters :**
Input :
hDB  -  Handle to the open database in which to add the item.

type  -  Item data type. See TYPE_xxx.

string  -  Name of item to be added.

length  -  Length of item name.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully added an item to the Item Definition Table.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


rtnItemNumber  -  The item number of the item added to the Item Definition Table. 


**See Also :**
[NSFDbItemDefTable](/domino-c-api-docs/reference/Func/NSFDbItemDefTable)
---

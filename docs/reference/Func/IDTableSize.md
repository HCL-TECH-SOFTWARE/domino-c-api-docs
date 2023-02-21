##### Function : ID Table
##### IDTableSize - Returns the size of the specified ID Table in bytes.
---
```
#include <idtable.h>
DWORD LNPUBLIC IDTableSize(

	DHANDLE  hTable);
```
**Description :**

This function takes a HANDLE to an ID Table, then calculates and returns the 
size of the entire ID Table in bytes.  Since an ID Table contains header 
information and is compressed, the size returned cannot be computed based on 
the number of IDs in the table.

**Parameters :**
Input :
hTable  -  A HANDLE to the ID Table.

Output :
(routine)  -  Returns the size of the specified ID Table in bytes.



**Sample Usage :**
```

   printf("IDTableSize from function: %lu\n",
           IDTableSize(idtable_handle));


```
**See Also :**
[IDTableFlags](/domino-c-api-docs/reference/Func/IDTableFlags)
[IDTableTime](/domino-c-api-docs/reference/Func/IDTableTime)
[IDTableSetFlags](/domino-c-api-docs/reference/Func/IDTableSetFlags)
[IDTableSetTime](/domino-c-api-docs/reference/Func/IDTableSetTime)
[IDTableSizeP](/domino-c-api-docs/reference/Func/IDTableSizeP)
---

##### Function : ID Table
##### IDTableSizeP - Returns the size of the specified ID Table in bytes.
---
```
#include <idtable.h>
DWORD LNPUBLIC IDTableSizeP(

	void far *pIDTable);
```
**Description :**

This function takes a pointer to an ID Table, then calculates and returns the 
size of the entire ID Table in bytes.  Since an ID Table contains header 
information and is compressed, the size returned cannot be computed based on 
the number of IDs in the table.

**Parameters :**
Input :
pIDTable  -  Pointer to the ID Table.

Output :
(routine)  -  Returns the number of bytes occupied by the specified ID Table.



**See Also :**
[IDTableSize](/reference/Func/IDTableSize)
---

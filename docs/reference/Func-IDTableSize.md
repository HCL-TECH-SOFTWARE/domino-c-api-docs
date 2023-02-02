##### Function : ID Table
##### IDTableSize - Returns the size of the specified ID Table in bytes.
---
##### #include <idtable.h>
DWORD LNPUBLIC **IDTableSize(**

	DHANDLE  hTable);
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
[IDTableFlags](D:/md_files/IDTableFlags.md)
[IDTableTime](D:/md_files/IDTableTime.md)
[IDTableSetFlags](D:/md_files/IDTableSetFlags.md)
[IDTableSetTime](D:/md_files/IDTableSetTime.md)
[IDTableSizeP](D:/md_files/IDTableSizeP.md)
---

##### Function : ID Table
##### IDEntries - Returns the number of note IDs in the specified ID Table.
---
##### #include <idtable.h>
DWORD LNPUBLIC **IDEntries(**

	DHANDLE  hTable);
**Description :**
This function takes a handle to an ID Table and returns the number of IDs in 
the ID Table.
**Parameters :**
Input :
hTable  -  A HANDLE to a Domino memory object containing an ID Table.

Output :
(routine)  -  Returns number of IDs in the specified ID Table.


**Sample Usage :**
```

               /* Some demographics */

               num_entries = IDEntries(arctable_handle);
               printf("Analysis of Notes between begin & end:\n");
               printf("\n# of Entries in idtable = %lu\n",
                       notes_scanned);
               printf("# of Entries in arctable = %lu\n",
                       num_entries);

```
**See Also :**
[IDCreateTable](D:/md_files/IDCreateTable.md)
[IDDelete](D:/md_files/IDDelete.md)
[IDDeleteAll](D:/md_files/IDDeleteAll.md)
[IDEnumerate](D:/md_files/IDEnumerate.md)
[IDInsert](D:/md_files/IDInsert.md)
[IDIsPresent](D:/md_files/IDIsPresent.md)
[IDScan](D:/md_files/IDScan.md)
[IDTableCopy](D:/md_files/IDTableCopy.md)
[IDTableSize](D:/md_files/IDTableSize.md)
---

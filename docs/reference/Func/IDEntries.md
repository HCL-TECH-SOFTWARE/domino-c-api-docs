##### Function : ID Table
##### IDEntries - Returns the number of note IDs in the specified ID Table.
---
```
#include <idtable.h>
DWORD LNPUBLIC IDEntries(

	DHANDLE  hTable);
```
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
[IDCreateTable](/reference/Func/IDCreateTable)
[IDDelete](/reference/Func/IDDelete)
[IDDeleteAll](/reference/Func/IDDeleteAll)
[IDEnumerate](/reference/Func/IDEnumerate)
[IDInsert](/reference/Func/IDInsert)
[IDIsPresent](/reference/Func/IDIsPresent)
[IDScan](/reference/Func/IDScan)
[IDTableCopy](/reference/Func/IDTableCopy)
[IDTableSize](/reference/Func/IDTableSize)
---

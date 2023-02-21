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
[IDCreateTable](/domino-c-api-docs/reference/Func/IDCreateTable)
[IDDelete](/domino-c-api-docs/reference/Func/IDDelete)
[IDDeleteAll](/domino-c-api-docs/reference/Func/IDDeleteAll)
[IDEnumerate](/domino-c-api-docs/reference/Func/IDEnumerate)
[IDInsert](/domino-c-api-docs/reference/Func/IDInsert)
[IDIsPresent](/domino-c-api-docs/reference/Func/IDIsPresent)
[IDScan](/domino-c-api-docs/reference/Func/IDScan)
[IDTableCopy](/domino-c-api-docs/reference/Func/IDTableCopy)
[IDTableSize](/domino-c-api-docs/reference/Func/IDTableSize)
---

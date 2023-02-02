##### Function : ID Table
##### IDIsPresent - Determine if ID is present in an ID Table.
---
##### #include <idtable.h>
BOOL LNPUBLIC **IDIsPresent(**

	DHANDLE  hTable,
	DWORD  id);
**Description :**
This is a function takes a HANDLE to an ID Table and a  DWORD containing a note 
ID, and returns whether the DWORD is present in the ID Table.
**Parameters :**
Input :
hTable  -  A HANDLE of the ID Table.

id  -  The note ID you wish to search for in the ID Table.

Output :
(routine)  -  Returns one of the following values:

TRUE - ID is present in ID Table.
FALSE - Could not find ID in ID Table.


**Sample Usage :**
```

   /* Demo using one table to cleanup another - safe way */

           notes_scanned = 0L;
           while(IDScan(cpytable_handle,
                        (FLAG)(notes_scanned++==0L), &note_id))
           {
               if (IDIsPresent(idtable_handle, note_id))
               {
                   error_status = IDDelete(idtable_handle,
                                                note_id, &ok_flag);
                   if (!ok_flag || error_status)
                   {
                       printf("\nIDDelete from idtable failed.\n");
                       goto Exit;
                   }
               }
           }


```
**See Also :**
[IDCreateTable](D:/md_files/IDCreateTable.md)
[IDInsert](D:/md_files/IDInsert.md)
[IDDelete](D:/md_files/IDDelete.md)
[IDDeleteAll](D:/md_files/IDDeleteAll.md)
[IDEnumerate](D:/md_files/IDEnumerate.md)
[IDEntries](D:/md_files/IDEntries.md)
[IDScan](D:/md_files/IDScan.md)
[IDTableSize](D:/md_files/IDTableSize.md)
[IDTableCopy](D:/md_files/IDTableCopy.md)
[IDTableSize](D:/md_files/IDTableSize.md)
---

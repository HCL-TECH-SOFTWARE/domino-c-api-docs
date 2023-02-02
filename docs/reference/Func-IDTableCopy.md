##### Function : ID Table
##### IDTableCopy - Copies an ID Table.
---
##### #include <idtable.h>
STATUS LNPUBLIC **IDTableCopy(**

	DHANDLE  hTable,
	DHANDLE far *rethTable);
**Description :**
This function takes an a handle associated with an existing ID Table and 
returns a new handle of a new ID Table that is a copy of the original.  It also 
sets the IDTABLE_MODIFIED flag in the new ID Table upon successful completion.
**Parameters :**
Input :
hTable  -  A handle associated with an existing ID Table.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - If the ID Table was successfully copied.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


rethTable  -  The address of a HANDLE in which the handle to the newly copied ID Table will be returned.  The caller is responsible for disposing of this memory object with IDDestroyTable() when through with it.

**Sample Usage :**
```

           if ( error_status = IDTableCopy(idtable_handle,
                                           &cpytable_handle))
               goto Exit;
           else
               cleanup_state += FREE_CPYTABLE;
     
```
**See Also :**
[IDCreateTable](D:/md_files/IDCreateTable.md)
[IDDelete](D:/md_files/IDDelete.md)
[IDDeleteAll](D:/md_files/IDDeleteAll.md)
[IDDestroyTable](D:/md_files/IDDestroyTable.md)
[IDEntries](D:/md_files/IDEntries.md)
[IDEnumerate](D:/md_files/IDEnumerate.md)
[IDInsert](D:/md_files/IDInsert.md)
[IDIsPresent](D:/md_files/IDIsPresent.md)
[IDScan](D:/md_files/IDScan.md)
[IDTableCopy](D:/md_files/IDTableCopy.md)
[IDTableSize](D:/md_files/IDTableSize.md)
---

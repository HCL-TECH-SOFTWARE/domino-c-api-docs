##### Function : ID Table
##### IDDeleteAll - Deletes all IDs from an ID Table.
---
```
#include <idtable.h>
STATUS LNPUBLIC IDDeleteAll(

	DHANDLE  hTable);
```
**Description :**

This function takes a handle to an ID Table and deletes all the IDs in it.

**Parameters :**
Input :
hTable  -  A handle to the ID Table.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - If deletion and memory release of the IDs was successful.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**Sample Usage :**
```

                if (IDEntries(deltable_handle))
 
               {   /* Using NULL in 3rd arg avoids ERR_REMOTE_UNID */

                    if (error_status = NSFDbDeleteNotes (
                                            db_handle_src,
                                            deltable_handle,
                                            NULL))
                        goto Exit;

                    /* adjust del_count exit of while(IDScan) */

                    printf("\n%s: %lu Notes in %s\n",
                           (del_count <= del_max)? "Deleting"
                                                 : "Deleted",
                           (del_count <= del_max)? 50
                                                 : del_count-1,
                           src_name);
                    if (error_status = IDDeleteAll(deltable_handle))
                        goto Exit;
                }

```
**See Also :**
[IDCreateTable](/domino-c-api-docs/reference/Func/IDCreateTable)
[IDDelete](/domino-c-api-docs/reference/Func/IDDelete)
[IDEntries](/domino-c-api-docs/reference/Func/IDEntries)
[IDEnumerate](/domino-c-api-docs/reference/Func/IDEnumerate)
[IDInsert](/domino-c-api-docs/reference/Func/IDInsert)
[IDIsPresent](/domino-c-api-docs/reference/Func/IDIsPresent)
[IDScan](/domino-c-api-docs/reference/Func/IDScan)
[IDTableCopy](/domino-c-api-docs/reference/Func/IDTableCopy)
[IDTableSize](/domino-c-api-docs/reference/Func/IDTableSize)
---

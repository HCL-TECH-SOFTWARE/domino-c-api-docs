##### Function : Database
##### NSFDbDeleteNotes - Deletes all notes in an ID table from a database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbDeleteNotes(**

	DBHANDLE  hDB,
	DHANDLE  hTable,
	UNID far *retUNIDArray);
**Description :**
This function takes a database handle, a handle associated with a Note ID 
Table, and deletes all the notes specified in the ID table.  For local 
databases only, it also optionally returns an array of UNIDs of the deleted 
notes (mostly used by the Replication process).

This function is useful when deleting a large number of notes in a remote 
database, because it minimizes the network traffic by sending only one request 
to the Lotus Domino Server.

Note: This function will return an error if the ID table contains View notes or 
Design notes.
**Parameters :**
Input :
hDB  -  A handle to a Domino database.

hTable  -  A HANDLE to an ID table containing the IDs you wish to have deleted from the Domino database.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully deleted the notes contained in the ID Table from the database.
ERR_REMOTE_UNID - (you cannot obtain the UNIDs using this call to remote databases).
ERR_VIEW_UPDATE - (you cannot delete View notes or Design notes using this call).
ERR_NO_DELETED_NOTES - No documents were deleted.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retUNIDArray  -  The address of an array of UNID structures in which the UNIDs of the deleted notes are returned.  Specify NULL if you do not wish this information to be returned.  The number of notes in the ID table should not exceed the number of available elements in the UNID array.  In the case of an ID in the table which represents a Category (and not a real note), the corresponding UNID is not returned in the array.  The UNIDs are returned in Domino canonical format.

**Sample Usage :**
```

            /* Batch any Deletions */
 
           if (error_status = IDCreateTable( alignment,
                                              &deltable_handle))
                goto Exit;
            else
                cleanup_state += FREE_DELTABLE;
            del_max = IDEntries(thetable_handle);
            del_count = 0L;
            while( del_count < del_max )
            {
                while (IDScan(thetable_handle,
                             (BOOL)(del_count++==0L), &note_id))
                {

                    /* Build a table to batch operation */

                    error_status = IDInsert(deltable_handle,
                                            note_id, &ok_flag);
                    if (!ok_flag || error_status)
                    {
                        printf("IDInsert in deltable failed.\n");
                        goto Exit;
                    }
                    if ((del_count % MAXOPTIMALDELETIONS) == 0)
                        break;
                }
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
            }

            cleanup_state -= FREE_DELTABLE;
            if ( error_status = IDDestroyTable(deltable_handle))
                 goto Exit;

```
**See Also :**
[IDDeleteAll](D:/md_files/IDDeleteAll.md)
[IDEnumerate](D:/md_files/IDEnumerate.md)
[IDScan](D:/md_files/IDScan.md)
[NSFDbGetModifiedNoteTable](D:/md_files/NSFDbGetModifiedNoteTable.md)
[NSFDbStampNotes](D:/md_files/NSFDbStampNotes.md)
---

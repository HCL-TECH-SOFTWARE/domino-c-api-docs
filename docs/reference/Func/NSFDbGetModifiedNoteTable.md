##### Function : Database
##### NSFDbGetModifiedNoteTable - Get ID Table of notes modified during a time span.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetModifiedNoteTable(

	DBHANDLE  hDB,
	WORD  NoteClassMask,
	TIMEDATE  Since,
	TIMEDATE far *retUntil,
	DHANDLE far *rethTable);
```
**Description :**

This function takes a database handle, note class mask, and starting 
time/date.  It returns a handle to an ID Table of Note IDs of notes which have 
been modified in some way from the given starting time until "now".  The ending 
time/date is returned, so that this function can be performed incrementally.

Except when TIMEDATE_MINIMUM is specified, the IDs of notes deleted during the 
time span will also be returned in the ID Table, and the IDs of these deleted 
notes have been ORed with RRV_DELETED before being added to the table.  You 
must check the RRV_DELETED flag when using the resulting table.

Note: If there are NO modified or deleted notes in the database since the 
specified time, the error ERR_NO_MODIFIED_NOTES will be returned.  Since this 
is most likely not a fatal error to the application, you should check for this 
error code explicitly.

Note: You program is responsible for freeing any memory associated with a valid 
handle returned in argument 5.

**Parameters :**
Input :
hDB  -  A DBHANDLE to an open Domino database.

NoteClassMask  -  A WORD containing the appropriate NOTE_CLASS_xxx mask for the documents you wish to select.   Symbols can be OR'ed to obtain the desired Note classes in the resulting ID Table.   

Since  -  A TIMEDATE structure containing the starting date used when selecting notes to be added to the ID Table built by this function.  To include ALL notes (including those deleted during the time span) of a given note class, use TimeConstant() with the TimeConstantType argument set to TIMEDATE_WILDCARD.  To include ALL notes of a given note class, but excluding those notes deleted during the time span, use TimeConstant() with the TimeConstantType argument set to TIMEDATE_MINIMUM.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully obtained the Modified Note Table.

ERR_NO_MODIFIED_NOTES -  No documents have been modified since specified time.

ERR_DIRECTORY - This function is inappropriate for Directories.  Several Db APIs operate on 'directory handles' that are created by passing a directory instead of a filename to NSFDbOpen or NSFDbOpenExtended.  NSFDbLocateByReplicaID is an example of a Db API that operates on directories.  NSFDbGetModifiedNoteTable is an example of one that does not.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retUntil  -  A pointer to a TIMEDATE structure into which the ending time of this search will be returned.  This can subsequently be used as the starting time in a later search.

rethTable  -  The address of a HANDLE into which the handle of the newly allocated ID Table will be returned.  You are responsible for freeing the storage when you are done with it using IDDestroyTable().


**Sample Usage :**
```


   /* Get the requested Notes */

   if (error_status = NSFDbGetModifiedNoteTable(db_handle_src,
                       NOTE_CLASS_DOCUMENT,
                       begin_td, &end_td, &idtable_handle))
   {
       if (ERR(error_status) == ERR_NO_MODIFIED_NOTES)
       {
           printf("\n%s contains no data notes from:\n",
                  src_name);
           if (strlen(begin_str))
               printf("\tBegin date: %s\n", begin_str);
           else
               printf("\tBegin date: Beginning of Cosmos\n");
           printf("\tthrough End date: %s\n", end_str);
           goto Exit;
       }
       else
           goto Exit;
   }

```
**See Also :**
[IDEnumerate](/domino-c-api-docs/reference/Func/IDEnumerate)
[NSFApplyModifiedNoteTable](/domino-c-api-docs/reference/Func/NSFApplyModifiedNoteTable)
[NSFDbDeleteNotes](/domino-c-api-docs/reference/Func/NSFDbDeleteNotes)
[NSFDbStampNotes](/domino-c-api-docs/reference/Func/NSFDbStampNotes)
[IDDestroyTable](/domino-c-api-docs/reference/Func/IDDestroyTable)
---

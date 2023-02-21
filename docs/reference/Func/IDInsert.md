##### Function : ID Table
##### IDInsert - Inserts a note ID into an ID Table.
---
```
#include <idtable.h>
STATUS LNPUBLIC IDInsert(

	DHANDLE  hTable,
	DWORD  id,
	BOOL far *retfInserted);
```
**Description :**

This function takes a handle to an ID Table and a note ID. It inserts the ID 
into the ID Table only if the table does not already contain that ID.  It 
returns a BOOL value in the *retfInserted parameter indicating whether or not 
the note ID was successfully inserted into the ID Table.  A value of FALSE 
indicates that the ID Table already contained that ID.  This function also sets 
the IDTABLE_MODIFIED flag if the ID was successfully inserted, that is if the 
returned BOOL value is TRUE.    

ID Tables are ordered by ID value. IDInsert stores the ID in the table 
according to its value.

**Parameters :**
Input :
hTable  -  A handle to the ID Table.

id  -  The ID you wish to insert into the ID Table.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - ID successfully inserted or ID found already in the table.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retfInserted  -  The address of a BOOL variable in which the outcome of the call to IDInsert is placed.  TRUE - if the specified ID was inserted into the ID Table.  FALSE - if the ID was already in the ID Table.  Can be NULL if no return value is required.


**Sample Usage :**
```
STATUS LNPUBLIC AddIDUnique    
            (void * phNoteIDTable, 
            SEARCH_MATCH *search_info, 
            ITEM_TABLE *summary_info)
{
    DHANDLE      hNoteIDTable;
    STATUS      error;
    BOOL        flagOK;

    if (!(search_info->SERetFlags & SE_FMATCH))     /* V4 */
        return (NOERROR);


    hNoteIDTable = *((DHANDLE *)phNoteIDTable);

    if (error = IDInsert(hNoteIDTable, search_info->ID.NoteID, &flagOK))
    {
        printf ("Error: unable to insert note ID into table.\n");
        return (ERR(error));
    }
    if (flagOK == TRUE)
    {
        printf ("\tInserted note %lX into table.\n", search_info->ID.NoteID);
    }
    else
    {
        printf ("\tNote %lX is already in table.\n", search_info->ID.NoteID);
    }

    return (NOERROR);
}
```
**See Also :**
[IDCreateTable](/domino-c-api-docs/reference/Func/IDCreateTable)
[IDDelete](/domino-c-api-docs/reference/Func/IDDelete)
[IDDeleteAll](/domino-c-api-docs/reference/Func/IDDeleteAll)
[IDEntries](/domino-c-api-docs/reference/Func/IDEntries)
[IDEnumerate](/domino-c-api-docs/reference/Func/IDEnumerate)
[IDIsPresent](/domino-c-api-docs/reference/Func/IDIsPresent)
[IDScan](/domino-c-api-docs/reference/Func/IDScan)
[IDTableCopy](/domino-c-api-docs/reference/Func/IDTableCopy)
[IDTableSize](/domino-c-api-docs/reference/Func/IDTableSize)
---

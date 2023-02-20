##### Function : ID Table
##### IDEnumerate - Calls action routine for each ID in an ID Table.
---
```
#include <idtable.h>
STATUS LNPUBLIC IDEnumerate(

	DHANDLE  hTable,
	IDENUMERATEPROC  Routine,
	void far *Parameter);
```
**Description :**

This function takes a handle to an ID Table, the address of an action routine, 
and a pointer of your choosing.  It calls the action routine with each note ID 
in the ID Table and the user supplied parameter, until the ID Table is 
exhausted.  If the routine returns an error, IDEnumerate will halt and pass it 
back.

ID Tables are ordered by ID value. IDEnumerate calls the action routine in the 
order in which the IDs are stored in the table.

**Parameters :**
Input :
hTable  -  A handle to an ID Table containing the note IDs you wish the action routine to act on.

Routine  -  A pointer to the action routine.  The action routine must conform to the calling sequence defined in the following declaration:  
 
STATUS LNPUBLIC Routine(void far *Parameter, DWORD id);

Parameter  -  A pointer to an object of your choice.  NULL if you do not wish to take advantage of this feature.  The object could be a database handle, context/state structure, etc..

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully executed the action routine with each note ID in the ID Table.

ERR_xxx - Errors returned by lower level functions, including the action routine itself.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.



**Sample Usage :**
```
             IDENUMERATEPROC  lpIDProc;
           lpIDProc = (IDENUMERATEPROC) MakeProcInstance
               ((FARPROC)TouchNotes);
           error_status = IDEnumerate(cpytable_handle,
                                      lpIDProc,
                                      &db_handle_src);
           FreeProcInstance(lpIDProc);
           

```
**See Also :**
[IDENUMERATEPROC](/reference/Data/IDENUMERATEPROC)
[IDCreateTable](/reference/Func/IDCreateTable)
[IDDelete](/reference/Func/IDDelete)
[IDDeleteAll](/reference/Func/IDDeleteAll)
[IDEntries](/reference/Func/IDEntries)
[IDInsert](/reference/Func/IDInsert)
[IDIsPresent](/reference/Func/IDIsPresent)
[IDScan](/reference/Func/IDScan)
[IDTableCopy](/reference/Func/IDTableCopy)
[IDTableSize](/reference/Func/IDTableSize)
---

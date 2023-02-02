##### Function : ID Table
##### IDScan - Sequentially return each ID in an ID Table.
---
##### #include <idtable.h>
BOOL LNPUBLIC **IDScan(**

	DHANDLE  hTable,
	BOOL  fFirst,
	DWORD far *retID);
**Description :**
This function takes a HANDLE to an ID Table and a BOOL argument indicating 
whether or not you are asking for the first note ID in the table.  It returns 
either the first or next available note ID as requested.

ID Tables are ordered by value. IDScan returns Note IDs in the order they 
appear in the ID Table.
**Parameters :**
Input :
hTable  -  A HANDLE to the ID Table.

fFirst  -  A BOOL value indicating whether you wish to access the first note ID (fFirst = TRUE) or access the next note ID (fFirst = FALSE).

retID  -  If accessing the first note ID in an ID Table (i.e., fFirst == TRUE), this is simply the address of a DWORD in which the first note ID in the table is to be returned. 

If accessing the next note ID (i.e., fFirst = FALSE), *retID must contain the note ID most recently returned by IDScan. 

Output :
(routine)  -  Returns one of the following values:

TRUE - Successfully obtained note ID from ID Table.

FALSE - Could not obtain a note ID from ID Table.  Indicates either an empty ID Table or no additional notes can be located beyond the last one returned.


retID  -  The address of a DWORD in which the NOTEID obtained from the ID Table is returned.  If the ID Table was obtained with NSFDbGetModifiedNoteTable, then the note ID of each deleted note has been ORed with RRV_DELETED.  It is recommended that all of these IDs be checked before being passed on to a function that tries to use the ID as a note ID.

 If for some reason you need to clear the RRV_DELETED bit from a note ID returned by IDScan (for use by another function, for example), it is recommended that a copy of the note ID be made and the bit cleared from the copy. Clearing the RRV_DELETED bit in the note ID returned in noteid_ptr will cause subsequent calls to IDScan to fail.

**Sample Usage :**
```
    /*  Loop over note IDs in the table. Call ProcessNote on each. */
    fFirst = TRUE;

    while(IDScan(hNoteIDTable, fFirst, &NoteID))
    {
        fFirst = FALSE;
        printf ("\tProcessing note %lX.\n", NoteID);
        if (error = ProcessNote(NoteID))
            break;
    }
```
**See Also :**
[IDCreateTable](D:/md_files/IDCreateTable.md)
[IDInsert](D:/md_files/IDInsert.md)
[IDDelete](D:/md_files/IDDelete.md)
[IDDeleteAll](D:/md_files/IDDeleteAll.md)
[IDEnumerate](D:/md_files/IDEnumerate.md)
[IDEntries](D:/md_files/IDEntries.md)
[IDIsPresent](D:/md_files/IDIsPresent.md)
[IDTableSize](D:/md_files/IDTableSize.md)
[IDTableCopy](D:/md_files/IDTableCopy.md)
[IDTableSize](D:/md_files/IDTableSize.md)
---

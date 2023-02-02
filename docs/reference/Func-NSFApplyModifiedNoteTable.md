##### Function : Database
##### NSFApplyModifiedNoteTable - Apply table of modified notes to an unread list.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFApplyModifiedNoteTable(**

	DHANDLE  hModifiedNotes,
	DHANDLE  hTargetTable);
**Description :**
Given a handle to an ID Table of modified notes (obtained by calling 
NSFDbGetModifiedNoteTable()) and a handle to an ID Table of unread notes 
(obtained by calling NSFDbGetUnreadNoteTable()), this function will add any 
modified notes to and remove any deleted notes from the unread note table.
**Parameters :**
Input :
hModifiedNotes  -  Handle to an ID Table of modified notes.  This ID Table may be obtained by calling NSFDbGetModifiedNoteTable().

hTargetTable  -  Handle to an ID Table of unread notes.  This ID Table may be obtained by calling NSFDbGetUnreadNoteTable().

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully obtained the Modified Note Table.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


hTargetTable  -  The ID Table identified by the handle is updated.  Notes that have been modified are added to this ID Table.  Notes that have been deleted are removed from this ID Table.

**See Also :**
[NSFDbGetModifiedNoteTable](D:/md_files/NSFDbGetModifiedNoteTable.md)
[NSFDbGetUnreadNoteTable](D:/md_files/NSFDbGetUnreadNoteTable.md)
---

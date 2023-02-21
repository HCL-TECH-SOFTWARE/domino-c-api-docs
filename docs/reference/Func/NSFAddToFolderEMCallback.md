##### Function : Extension Manager
##### NSFAddToFolderEMCallback - Extension Manager callback for EM_NSFADDTOFOLDER
---
```
#include <extmgr.h>
STATUS LNPUBLIC NSFAddToFolderEMCallback(

	DBHANDLE  hViewDB,
	DBHANDLE  hDataDB,
	NOTEID  FolderNoteID,
	NOTEID  NoteID,
	UNID *NoteUNID,
	BOOL  IsAddOperation,
	TIMEDATE *RevisionTime);
```
**Description :**

EM_NSFADDTOFOLDER is called when a note is being added or removed  from a 
folder.  The IsAddOperation flag should be checked to determine if this note is 
being added or removed from the folder.

This notification is useful in the implementation of Unified Messaging 
functionality in the Domino and Notes environment.  See the Chapter on Unified 
Messaging Solutions in the User Guide for more information.

Note:  You must not call NSFFolderGetIDTable in this routine with the same 
Folder ID.  When this notification is trapped, the database semaphore is 
locked.  NSFFolderGetIDTable cannot acquire the database semaphore.  Attempting 
to call NSFFolderGetIDTable will result in a deadlock.

**Parameters :**
Input :
hViewDB  -  Handle of database containing folder

hDataDB  -  Handle of database containing notes being added to folder

FolderNoteID  -  NoteID of the folder note

NoteID  -  NoteID of the note being added to (removed from) the folder

NoteUNID  -  UNID of the note being added to (removed from) the folder

IsAddOperation  -  TRUE if note being added to the folder, FALSE if note being removed

RevisionTime  -  Time of original folder addition (OPTIONAL - may be NULL)

Output :
(routine)  -  ERR_EM_CONTINUE



**See Also :**
[EM_xxx](/domino-c-api-docs/reference/Symb/EM_xxx)
[NSFMarkReadEMCallback](/domino-c-api-docs/reference/Func/NSFMarkReadEMCallback)
---

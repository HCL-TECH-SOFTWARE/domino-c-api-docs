##### Function : Extension Manager
##### NSFMarkReadEMCallback - Extension Manager callback for EM_NSFMARKREAD
---
```
#include <extmgr.h>
STATUS LNPUBLIC NSFMarkReadEMCallback(

	DBHANDLE  hDB,
	HANDLE  hNote,
	NOTEID  NoteID);
```
**Description :**

EM_NSFMARKREAD is called when a note is opened for reading by the Notes 
client.  It is called every time a note is opened for reading by the Notes 
client, not just when a document changes from UNREAD to READ.  Note that this 
does not include other mechanisms that could result in a note being marked 
read.  For example, EM_NSFMARKREAD is not called when a message is marked READ 
via the <INSERT> key or Edit/Unread Marks.  It is also not called when a 
message is read or when a message is marked READ from a C API program.

This notification is useful in the implementation of Unified Messaging 
functionality in the Domino and Notes environment.  See the Chapter on Unified 
Messaging Solutions in the User Guide for more information.

Note: You must not call NSFDbGetUnreadNoteTable in this routine.  When this 
notification is trapped, the database semaphore is locked.  
NSFDbGetUnreadNoteTable cannot acquire the database semaphore.  Attempting to 
call NSFDbGetUnreadNoteTable will result in a deadlock.

**Parameters :**
Input :
hDB  -  Handle of database containing note being marked

hNote  -  Handle to note being marked read

NoteID  -  NoteID of the note being marked read

Output :
(routine)  -  ERR_EM_CONTINUE



**See Also :**
[EM_xxx](/reference/Symb/EM_xxx)
[NSFAddToFolderEMCallback](/reference/Func/NSFAddToFolderEMCallback)
---

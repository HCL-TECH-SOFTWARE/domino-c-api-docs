##### Function : Extension Manager
##### NSFNoteUpdateMailboxEMCallback - Extension Manager callback for EM_NSFNOTEUPDATEMAILBOX
---
```
#include <extmgr.h>
STATUS LNPUBLIC NSFNoteUpdateMailboxEMCallback(

	NOTEHANDLE  note_handle,
	WORD  update_flags);
```
**Description :**

EM_NSFNOTEUPDATEMAILBOX occurs when a NSFNoteUpdate is performed on any and all 
mailbox databases (e.g. a mail.box file).  This is true even if multiple 
mailboxes are enabled in the server configuration document.  The arguments are 
identical to those used for EM_NSFNOTEUPDATE.

**Parameters :**
Input :
note_handle  -  The handle of the note to be updated.

update_flags  -  Flags that control the manner in which the note update is done. The flags are defined in UPDATE_xxx and may be or'ed together to combine functionality.

Output :
(routine)  -  
ERR_EM_CONTINUE



**See Also :**
[EM_xxx](/reference/Symb/EM_xxx)
[UPDATE_xxx](/reference/Symb/UPDATE_xxx)
---

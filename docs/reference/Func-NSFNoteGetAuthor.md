##### Function : Note
##### NSFNoteGetAuthor - Return the author of the note.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteGetAuthor(**

	NOTEHANDLE  hNote,
	char far *retName,
	WORD far *retNameLength,
	BOOL far *retIsItMe);
**Description :**
Given a handle to an open note, return the first author item for the note.  If 
the pointer argument retIsItMe is non-NULL, this routine will also compare the 
author item to the current user's name, and store the result at that address.
**Parameters :**
Input :
hNote  -  Handle to an open note.

Output :
(routine)  -  Return status from this call:

NOERROR - Success

ERR_ITEM_NOT_FOUND - No author was found for this note.

ERR_xxx - Errors returned by lower level Notes functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


retName  -  Optional - if not NULL, the first author item is written to this address.  retName is not null-terminated.

retNameLength  -  Number of bytes in the first author item.

retIsItMe  -  Optional - if this pointer is non-NULL, TRUE is stored if the author item is the same as the current user, FALSE if not.

**See Also :**
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
---

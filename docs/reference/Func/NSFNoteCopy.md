##### Function : Note
##### NSFNoteCopy - Make an in-memory copy of a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteCopy(

	NOTEHANDLE  note_handle_src,
	NOTEHANDLE far *note_handle_dst_ptr);
```
**Description :**

This function takes a handle to an open note, creates a duplicate copy in 
memory, and returns a handle to the newly created note. The new copy has the 
same note header information as the original, including the same Note ID, 
Originator ID, and Database handle. Before calling NSFNoteUpdate to save the 
new copy, you must generate an Originator ID, set the Originator ID, and zero 
the Note ID. 

Use NSFNoteCopy to create a new copy of a source note in the same database as 
the source note. To copy the source note to a different database you may use 
either NSFDbCopyNote or NSFNoteCopy. NSFDbCopyNote is more convenient for 
copying many notes from one database to another, or when you have the Note IDs 
of the source notes but do not wish to open the source notes. NSFNoteCopy is 
more convenient if you have the source note open or if you will only be copying 
one note.  Use NSFNoteClose to close the note handle and deallocate the memory 
associated with it.

To copy a note to a different database using NSFNoteCopy, you must generate a 
new Originator ID, set the new Originator ID, zero the Note ID, and set the 
Database handle to that of the destination database before saving the new copy 
to the destination database. See the sample code below.

Preserving the OID of the in-memory copy of a note makes it a replica copy of 
the original note. A Domino database must not store two notes with the same 
OID.

**Parameters :**
Input :
note_handle_src  -  A NOTEHANDLE to a an existing note.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Note successfully copied.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


note_handle_dst_ptr  -  The address of a NOTEHANDLE  in which the handle to the newly allocated note copy is returned.


**Sample Usage :**
```
/* copy hOldNote to destination database hNotesDB2.*/
  
  if (yerr=NSFNoteCopy(hOldNote,&hNewNote))
  {
     MessageBox(GetFocus(),"Unable to copy Note!",
             "process one note",MB_OK);
     NSFNoteClose(hOldNote);
     return(yerr);
  }


  if (yerr=NSFDbGenerateOID(hNotesDB2,&oidNew))
  {
     MessageBox(GetFocus(),"Unable to generate id!",
             "process one note",MB_OK);
     NSFNoteClose(hNewNote);
     NSFNoteClose(hOldNote);
     return(yerr);
  }

  NSFNoteSetInfo(hNewNote,_NOTE_OID,&oidNew);
  NSFNoteSetInfo(hNewNote,_NOTE_ID,NULL);
  NSFNoteSetInfo(hNewNote,_NOTE_DB,&hNotesDB2);


  if (yerr=NSFNoteUpdate(hNewNote,UPDATE_FORCE))
     MessageBox(GetFocus(),"Unable to update Note!",
             "process one note",MB_OK);
```
**See Also :**
[NSFDbCopyNote](/domino-c-api-docs/reference/Func/NSFDbCopyNote)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteGetInfo](/domino-c-api-docs/reference/Func/NSFNoteGetInfo)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[NSFNoteSetInfo](/domino-c-api-docs/reference/Func/NSFNoteSetInfo)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
[_NOTE_xxx](/domino-c-api-docs/reference/Symb/_NOTE_xxx)
---

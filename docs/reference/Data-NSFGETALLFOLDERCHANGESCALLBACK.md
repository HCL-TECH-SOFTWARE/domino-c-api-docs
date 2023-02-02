##### Data Type : Database
##### NSFGETALLFOLDERCHANGESCALLBACK - Definition of the get notes callback function used from NSFGetAllFolderChanges.
---
##### #include <nsfdb.h>
**Description :**
This callback function is implemented with the following parameters:  

inputs:
Param - Callback parameter passed into function.
NoteUNID - Universal note ID of the folder.
AddedNoteTable - Table of notes added to folder.
RemovedNoteTable - Table of notes removed from folder.

outputs: 
STATUS - Status of the call: NOERROR. Any other status indicates an error 
condition.



**See Also :**
[NSFGetAllFolderChanges](D:/md_files/NSFGetAllFolderChanges.md)
---

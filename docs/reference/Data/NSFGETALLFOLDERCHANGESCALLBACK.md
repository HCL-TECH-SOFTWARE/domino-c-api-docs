##### Data Type : Database
##### NSFGETALLFOLDERCHANGESCALLBACK - Definition of the get notes callback function used from NSFGetAllFolderChanges.
---
```
#include <nsfdb.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR NSFGETALLFOLDERCHANGESCALLBACK) (
	void *Param, 
	UNID *NoteUNID, 
	HANDLE AddedNoteTable, 
	HANDLE RemovedNoteTable);

**Description :**

This callback function is implemented with the following parameters:  
<ul>
<ul><br>
inputs:
<ul>
<ul>Param - Callback parameter passed into function.<br>
NoteUNID - Universal note ID of the folder.<br>
AddedNoteTable - Table of notes added to folder.<br>
RemovedNoteTable - Table of notes removed from folder.</ul>
</ul>
<br>
outputs:	
<ul>
<ul>STATUS - Status of the call: NOERROR. Any other status indicates an error condition.<br>
<br>
</ul>
</ul>
</ul>
</ul>



**See Also :**
[NSFGetAllFolderChanges](/domino-c-api-docs/reference/Func/NSFGetAllFolderChanges)
---

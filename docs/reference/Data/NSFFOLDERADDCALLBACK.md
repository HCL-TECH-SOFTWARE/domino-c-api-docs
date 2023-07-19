##### Data Type : Database
##### NSFFOLDERADDCALLBACK - Definition of the add folder callback function used from NSFDbGetNotes.
---
```
#include <nsfnote.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR NSFFOLDERADDCALLBACK) (
	void *Param, 
	UNID *NoteUNID, 
	DHANDLE OpBlock, 
	DWORD OpBlockSize);"

**Description :**

This callback function is implemented with the following parameters:  
<ul>
<ul><br>
inputs:
<ul>
<ul>Param - Callback parameter.<br>
NoteUNID - Universal Note ID.<br>
OpBlock - Reserved for internal use.<br>
OpBlockSize - Reserved for internal use.<br>
</ul>
</ul>
outputs:	
<ul>
<ul>STATUS - Status of the call: NOERROR. Any other status indicates an error condition.</ul>
</ul>
</ul>
</ul>



**See Also :**
[NSFDbGetNotes](/domino-c-api-docs/reference/Func/NSFDbGetNotes)
---

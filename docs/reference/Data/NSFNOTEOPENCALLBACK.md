##### Data Type : Database
##### NSFNOTEOPENCALLBACK - Definition of the note open callback function used from NSFDbGetNotes.
---
```
#include <nsfnote.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR NSFNOTEOPENCALLBACK) (
	void *Param, 
	NOTEHANDLE hNote, 
	DWORD NoteID, 
	STATUS status);"
```

**Description :**

This callback function is implemented with the following parameters:  
<ul>
<ul><br>
inputs:
<ul>
<ul>Param - Callback parameter.<br>
hNote - Note handle.<br>
NoteID - Note ID.<br>
STATUS - Status of the call: NOERROR. Any other status indicates an error condition.</ul>
</ul>
<br>
outputs:	
<ul>
<ul>STATUS - Status of the call: NOERROR. Any other status indicates an error condition.</ul>
</ul>
</ul>
</ul>



**See Also :**
[NSFDbGetNotes](/domino-c-api-docs/reference/Func/NSFDbGetNotes)
---

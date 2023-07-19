##### Data Type : Database
##### NSFOBJECTALLOCCALLBACK - Definition of the get notes callback function used from NSFDbGetNotes.
---
```
#include <nsfnote.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR NSFOBJECTALLOCCALLBACK) (
	void *Param, 
	NOTEHANDLE hNote, 
	NOTEID OldRRV, 
	STATUS status, 
	DWORD ObjectSize);"

**Description :**

This callback function is implemented with the following parameters:  
<ul>
<ul><br>
inputs:
<ul>
<ul>Param - Callback parameter.<br>
hNote - Note handle.<br>
OldRRV - Old Record Relocation Vector.<br>
STATUS - Status of the call: NOERROR. Any other status indicates an error condition.<br>
ObjectSize - Size of allocated object.<br>
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

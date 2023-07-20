##### Data Type : Database
##### NSFOBJECTWRITECALLBACK - Definition of the object write callback function used from NSFDbGetNotes.
---
```
#include <nsfnote.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR NSFOBJECTWRITECALLBACK) (
	void *Param, 
	NOTEHANDLE hNote, 
	NOTEID OldRRV, 
	STATUS status, 
	BYTE *Buffer, 
	DWORD BufferSize);"
```

**Description :**

This callback function is implemented with the following parameters:  
<ul>
<ul><br>
inputs:
<ul>
<ul>Param - Callback parameter.<br>
hNote - Note handle.<br>
OldRRV - Old  Record Relocation Vector. <br>
STATUS - Status of the call: NOERROR. Any other status indicates an error condition.<br>
Buffer - Buffer containing a &quot;chunk&quot; of the object (as this function will be called one or more time for each object.)<br>
Buffersize - Size of Buffer.</ul>
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

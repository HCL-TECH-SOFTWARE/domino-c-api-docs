##### Data Type : Database
##### NSFGETNOTESCALLBACK - Definition of the get notes callback function used from NSFDbGetNotes.
---
```
#include <nsfnote.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR NSFGETNOTESCALLBACK) (
	void *Param, 
	DWORD TotalSizeLow, 
	DWORD TotalSizeHigh);"
```

**Description :**

This callback function is implemented with the following parameters:  
<ul>
<ul><br>
inputs:
<ul>
<ul>Param - Callback parameter.<br>
TotalSizeLow - The approximate total number of bytes that are going to be returned in the note stream.  Combined they represent a 64 bit quantity with TotalSizeLow being the low 32 bits.<br>
TotalSizeHigh - The approximate total number of bytes that are going to be returned in the note stream.  Combined they represent a 64 bit quantity with TotalSizeHigh being the upper 32 bits.</ul>
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

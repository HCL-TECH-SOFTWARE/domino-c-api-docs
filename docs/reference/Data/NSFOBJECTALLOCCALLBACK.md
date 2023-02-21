##### Data Type : Database
##### NSFOBJECTALLOCCALLBACK - Definition of the get notes callback function used from NSFDbGetNotes.
---
```
#include <nsfnote.h>
```
**Description :**

This callback function is implemented with the following parameters:  

inputs:
Param - Callback parameter.
hNote - Note handle.
OldRRV - Old Record Relocation Vector.
STATUS - Status of the call: NOERROR. Any other status indicates an error 
condition.
ObjectSize - Size of allocated object.

outputs: 
STATUS - Status of the call: NOERROR. Any other status indicates an error 
condition.


**See Also :**
[NSFDbGetNotes](/domino-c-api-docs/reference/Func/NSFDbGetNotes)
---

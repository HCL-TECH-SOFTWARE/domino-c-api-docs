##### Data Type : Database
##### NSFFOLDERADDCALLBACK - Definition of the add folder callback function used from NSFDbGetNotes.
---
```
#include <nsfnote.h>
```
**Description :**

This callback function is implemented with the following parameters:  

inputs:
Param - Callback parameter.
NoteUNID - Universal Note ID.
OpBlock - Reserved for internal use.
OpBlockSize - Reserved for internal use.

outputs: 
STATUS - Status of the call: NOERROR. Any other status indicates an error 
condition.

**See Also :**
[NSFDbGetNotes](/domino-c-api-docs/reference/Func/NSFDbGetNotes)
---

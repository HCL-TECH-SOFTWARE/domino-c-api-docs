##### Data Type : Database
##### NSFOBJECTWRITECALLBACK - Definition of the object write callback function used from NSFDbGetNotes.
---
##### #include <nsfnote.h>
**Description :**
This callback function is implemented with the following parameters:  

inputs:
Param - Callback parameter.
hNote - Note handle.
OldRRV - Old  Record Relocation Vector. 
STATUS - Status of the call: NOERROR. Any other status indicates an error 
condition.
Buffer - Buffer containing a "chunk" of the object (as this function will be 
called one or more time for each object.)
Buffersize - Size of Buffer.

outputs: 
STATUS - Status of the call: NOERROR. Any other status indicates an error 
condition.
**See Also :**
[NSFDbGetNotes](D:/md_files/NSFDbGetNotes.md)
---

##### Data Type : Database
##### NSFGETNOTESCALLBACK - Definition of the get notes callback function used from NSFDbGetNotes.
---
##### #include <nsfnote.h>
**Description :**
This callback function is implemented with the following parameters:  

inputs:
Param - Callback parameter.
TotalSizeLow - The approximate total number of bytes that are going to be 
returned in the note stream.  Combined they represent a 64 bit quantity with 
TotalSizeLow being the low 32 bits.
TotalSizeHigh - The approximate total number of bytes that are going to be 
returned in the note stream.  Combined they represent a 64 bit quantity with 
TotalSizeHigh being the upper 32 bits.

outputs: 
STATUS - Status of the call: NOERROR. Any other status indicates an error 
condition.
**See Also :**
[NSFDbGetNotes](D:/md_files/NSFDbGetNotes.md)
---

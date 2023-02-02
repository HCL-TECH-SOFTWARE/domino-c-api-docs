##### Data Type : Address Book
##### LOOKUP_INFO - Structure of the data records that are in the buffer returned from NAMELookup.
---
##### #include <lookup.h>
**Description :**
NAMELookup returns a handle to a buffer containing name information. The buffer 
consists of a header (LOOKUP_HEADER) followed by a series LOOKUP_INFO 
structures  The order of the LOOKUP_INFO structures correspond to the order of 
names specified in the Names parameter of the call to NAMELookup.  Each 
LOOKUP_INFO structure is followed by an array of LOOKUP_MATCH structures.
**See Also :**
[NAMELookup](D:/md_files/NAMELookup.md)
[LOOKUP_HEADER](D:/md_files/LOOKUP_HEADER.md)
---

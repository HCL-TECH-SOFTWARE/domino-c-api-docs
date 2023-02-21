##### Data Type : Rich Text
##### CDFILEHEADER - Structure which defines a CSS header.
---
```
#include <editods.h>
```
**Description :**

This structure is used to define a Cascading Style Sheet (CSS) that is part of 
a Domino database.  CDFILESEGMENT structure(s) follow the CDFILEHEADER.

The fields in this structure are:

Header - Defines this composite data item as a CDFILEHEADER item.

FileExtLen - Length of file extension

FileDataSize - Size (in bytes) of the file data

SegCount - Number of CDFILESEGMENT records expected to follow

Flags - Flags (currently unused)
 
Reserved - Reserved for future use

A non-null terminated variable length string follows. This string is the file 
extension for the file. For example: "css".

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note. 

**See Also :**
[CDFILESEGMENT](/domino-c-api-docs/reference/Data/CDFILESEGMENT)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---

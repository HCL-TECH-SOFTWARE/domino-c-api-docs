##### Data Type : Rich Text
##### CDFILESEGMENT - Structure which defines a CSS segment.
---
```
#include <editods.h>
```
**Description :**

This structure defines the file segment data of a Cascading Style Sheet (CSS) 
and follows a CDFILEHEADER structure.  The number of segments in the file is 
specified in the CDFILEHEADER record.

The fields in this structure are:

Header - Defines this composite data item as a CDFILESEGMENT item.

DataSize - Size of CSS in bytes

SegSize - Size of segment. This is equal to or larger than DataSize if a filler 
byte is added to maintain the word boundary.

Flags - Flags (currently unused)
 
Reserved - Reserved for future use

File bits for this segment (the CSS and the optional filler byte) follow this 
record.

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note. 

**See Also :**
[CDFILEHEADER](/domino-c-api-docs/reference/Data/CDFILEHEADER)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---

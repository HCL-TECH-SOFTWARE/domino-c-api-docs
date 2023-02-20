##### Data Type : MIME
##### MIME_PART - Mime parts record.
---
```
#include <mimeods.h>
```
**Description :**

The MIME_PART structure stores the mime parts for items of TYPE_MIME_PART.  The 
fields in this structure are:

wVersion  MIME_PART Version.
dwFlags  Flags - see MIME_PART_xxx.
cPartType  Type of MIME_PART body - see MIMEPARTTYPE.
cSpare  Spare BYTE.
wByteCount                 Bytes of variable length part data NOT including 
data in DB object.
wBoundaryLen Length of the boundary string.
wHeadersLen Length of the headers.
wSpare  Spare WORD.
dwSpare  Spare DWORD.


**See Also :**
[MIME_PART_VERSION](/reference/Symb/MIME_PART_VERSION)
[MIME_PART_xxx](/reference/Symb/MIME_PART_xxx)
---

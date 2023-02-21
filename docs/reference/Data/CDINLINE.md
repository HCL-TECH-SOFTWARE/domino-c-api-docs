##### Data Type : Composite Data
##### CDINLINE - Pertains to shared resources and/or shared code in a form.
---
```
#include <editods.h>
```
**Description :**

This CD Record gives information pertaining to shared resources and/or shared 
code in a form.  A CDINLINE record may be preceded by a CDBEGINRECORD and 
followed by a CDRESOURCE and then a CDENDRECORD.  The fields in this record are:

Header - Signature and Length of this CD record.
wDatalength - Reserved for future use. Must be zero. 
dwFlags - see INLINE_FLAG_xxx
dwReserved[4] - Reserved for future use.


**See Also :**
[CDBEGINRECORD](/domino-c-api-docs/reference/Data/CDBEGINRECORD)
[CDENDRECORD](/domino-c-api-docs/reference/Data/CDENDRECORD)
[CDRESOURCE](/domino-c-api-docs/reference/Data/CDRESOURCE)
[INLINE_FLAG_xxx](/domino-c-api-docs/reference/Symb/INLINE_FLAG_xxx)
[INLINE_VERSION1](/domino-c-api-docs/reference/Symb/INLINE_VERSION1)
---

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
[CDBEGINRECORD](/reference/Data/CDBEGINRECORD)
[CDENDRECORD](/reference/Data/CDENDRECORD)
[CDRESOURCE](/reference/Data/CDRESOURCE)
[INLINE_FLAG_xxx](/reference/Symb/INLINE_FLAG_xxx)
[INLINE_VERSION1](/reference/Symb/INLINE_VERSION1)
---

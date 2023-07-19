##### Data Type : Composite Data
##### CDINLINE - Pertains to shared resources and/or shared code in a form.
---
```
#include <editods.h>
```

**Definition :**

typedef struct
 {
 WSIG Header;
 WORD wDatalength;
 DWORD dwFlags;
 DWORD dwReserved[4];
 } CDINLINE;


**Description :**

This CD Record gives information pertaining to shared resources and/or shared code in a form.  A CDINLINE record may be preceded by a CDBEGINRECORD and followed by a CDRESOURCE and then a CDENDRECORD.  The fields in this record are:<br>

<ul>Header - Signature and Length of this CD record.<br>
wDatalength - Reserved for future use. Must be zero. <br>
dwFlags - see INLINE_FLAG_xxx<br>
dwReserved[4] - Reserved for future use.</ul>



**See Also :**
[CDBEGINRECORD](/domino-c-api-docs/reference/Data/CDBEGINRECORD)
[CDENDRECORD](/domino-c-api-docs/reference/Data/CDENDRECORD)
[CDRESOURCE](/domino-c-api-docs/reference/Data/CDRESOURCE)
[INLINE_FLAG_xxx](/domino-c-api-docs/reference/Symb/INLINE_FLAG_xxx)
[INLINE_VERSION1](/domino-c-api-docs/reference/Symb/INLINE_VERSION1)
---

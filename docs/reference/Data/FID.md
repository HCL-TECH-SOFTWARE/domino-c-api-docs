##### Data Type : Font
##### FID - Font ID union.
---
```
#include <fontid.h>
```

**Definition :**
```
typedef union FID {
   FONTIDFIELDS x;
   FONTID FontID;
}FID;
```

**Description :**

This data structure allows accessing a FONTID as either a DWORD value or as a structure containing 4 byte values.  The fields in this structure are:
<ul><br>

<ul>x - Access the FONTID as a FONTIDFIELDS structure.<br>
<br>
FontID - Access the FONTID as a single DWORD value.</ul>
</ul>



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
---

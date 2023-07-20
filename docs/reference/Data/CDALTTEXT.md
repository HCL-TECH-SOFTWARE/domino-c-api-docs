##### Data Type : Composite Data
##### CDALTTEXT - Alternate text for HTML Web browsers.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;    /* Tag and length */
   WORD wLength;   /* text length */
   WORD Reserved1; /* Reserved for future use */
/* The 8-bit text string follows... */
} CDALTTEXT;
```

**Description :**

Documents stored on a Lotus Domino server that are viewed via a Web browser may contain elements that cannot be displayed by the browser.  These elements may have alternate text that the browser will display in their place.  The alternate text is stored in a CDALTTEXT record.  The fields in this record are:
<ul><br>

<ul>Header		Identifies this as a CDALTTEXT record.<br>
wLength	Length of the text string, in bytes.<br>
Reserved1	Reserved;  must be 0.</ul>
<br>
This record is followed by the alternate text string.</ul>



**See Also :**
---

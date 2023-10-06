##### Data Type : Rich Text
##### CDSRC - Text string used for SRC= within <IMG> HTML tag.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
	WSIG Header;    /* Tag and length */
	WORD wLength;   /* text length */
	WORD Reserved1;   /* Reserved for future use */
	DWORD Reserved2;   /* Reserved for future use */
	     /* The 8-bit text string follows... */
} CDSRC;
```

**Description :**

Text string used for SRC= within &lt;IMG&gt; HTML tag.  The fields in this structure are:
<ul><br>

<ul>Header		Identifies this as a CDSRC record.<br>
dwFlags	Flags for this record;  see CDSRC_FLAG_xxx.<br>
cbLevel	<br>
cbReserved	Reserved;  must be 0.<br>
Reserved	Reserved;  must be 0.</ul>
<br>
This record is followed by the actual formula.</ul>



**See Also :**
[CDHTMLFORMULA_FLAG_xxx](/domino-c-api-docs/reference/Symb/CDHTMLFORMULA_FLAG_xxx)
---

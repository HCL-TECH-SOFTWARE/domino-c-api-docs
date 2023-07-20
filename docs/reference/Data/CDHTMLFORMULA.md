##### Data Type : Rich Text
##### CDHTMLFORMULA - Formula for attributes or alternate HTML text.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
	WSIG Header;   /* Tag and length */
	DWORD dwFlags;   /* Flags - denote what kind of formula this is */
	BYTE cbLevel;   /* */
	BYTE cbReserved;   /* Reserved for future use. */
	WORD Reserved;   /* Reserved for future use */
	     /* The formula follows... */
} CDHTMLFORMULA;
```

**Description :**

A CDHTMLFORMULA record contains a formula used to generate either an attribute or alternate HTML text for a Java applet.  The fields in this structure are:
<ul><br>

<ul>Header		Identifies this as a CDHTMLFORMULA record.<br>
dwFlags	Flags for this record;  see CDHTMLFORMULA_FLAG_xxx.<br>
cbLevel	<br>
cbReserved	Reserved;  must be 0.<br>
Reserved	Reserved;  must be 0.</ul>
<br>
This record is followed by the actual formula.</ul>



**See Also :**
[CDHTMLFORMULA_FLAG_xxx](/domino-c-api-docs/reference/Symb/CDHTMLFORMULA_FLAG_xxx)
---

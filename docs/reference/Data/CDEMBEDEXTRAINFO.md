##### Data Type : Composite Data
##### CDEMBEDEXTRAINFO - Structure to store any extra info about embedded elements.
---
```
#include <editods.h>
```

**Definition :**

typedef struct
	{
	WSIG Header;
	WORD NameLength;
	DWORD Flags;
	DWORD Reserved[5];
	} CDEMBEDEXTRAINFO;

**Description :**

This CD record stores extra info about embedded elements.  The fields in this structure are:
<ul><br>
<br>
Header - Signature and length of this record.<br>
NameLength - <br>
Flags - <br>
Reserved - Reserved for future use - must be zero.  <br>
<br>
These fields may be followed by an optional name. If you plan to use it, you will need to declare the variable and assign a value to its length.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.</ul>



**See Also :**
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---

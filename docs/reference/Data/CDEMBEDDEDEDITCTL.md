##### Data Type : Composite Data
##### CDEMBEDDEDEDITCTL - Specifies an embedded edit control.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct
 {
 WSIG   Header; /* Signature and length of this record. */
 DWORD  Flags;
 WORD  NameLength;
	WORD   SpareWORD[5];
 DWORD SpareDWORD[11];
	} CDEMBEDDEDEDITCTL;
```

**Description :**

This CD record defines an embedded element of type 'editor'. It is preceded by a CDHOTSPOTBEGIN and a CDPLACEHOLDER. The CD record, CDPLACEHOLDER, further defines the CDEMBEDDEDEDITCTL. The fields in this record are:<br>
<br>
	Header - Signature and Length of this CD record.<br>
	Flags - Embedded edit control flags, see EMBEDDEDEDITCTL_FLAG_xxx.<br>
	NameLength - Length of the optional embedded editor name. <br>
	SpareWord - Reserved for future use.<br>
	SpareDWord -  Reserved for future use.<br>

<ul>These fields are followed by the optional embedded editor name. If you plan to use it, you will need to declare the variable and assign a value to its length.</ul>



**See Also :**
[EMBEDDEDEDITCTL_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDEDITCTL_FLAG_xxx)
---

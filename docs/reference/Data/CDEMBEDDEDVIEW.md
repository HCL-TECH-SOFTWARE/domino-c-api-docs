##### Data Type : Composite Data
##### CDEMBEDDEDVIEW - Specifies an embedded view.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct
	{
	WSIG  Header; /* Signature and length of this record. */
	DWORD  Flags; 
	FONTID  SpareFontID;
	WORD RestrictFormulaLength;
	WORD WebLines;
	WORD NameLength;
	WORD wSpare;
	DWORD Spare[3];
	} CDEMBEDDEDVIEW;
```

**Description :**

This CD Record describes a view as an embedded element.  A CDEMBEDDEDVIEW record will be preceded by a CDPLACEHOLDER record.  Further description of the embedded view can be found in the CD record CDPLACEHOLDER.
<ul><br>
<br>
WSIG	Header			Signature and length of this record.<br>
DWORD	Flags			EMBEDDEDVIEW_FLAG_xxx<br>
FONTID	SpareFontID<br>
WORD	RestrictFormulaLength	If Formula length, then Formula follows CD record fixed length.<br>
WORD	WebLines<br>
WORD	NameLength;<br>
WORD	wSpare;<br>
DWORD	Spare[3]</ul>



**See Also :**
[CDPLACEHOLDER](/domino-c-api-docs/reference/Data/CDPLACEHOLDER)
[EMBEDDEDVIEW_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---

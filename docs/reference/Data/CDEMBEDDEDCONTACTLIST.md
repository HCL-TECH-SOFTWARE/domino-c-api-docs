##### Data Type : Composite Data
##### CDEMBEDDEDCONTACTLIST - Defines properties of an embedded contact list.
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
	COLOR_VALUE SelectedBackground;
	COLOR_VALUE SelectedText;
	COLOR_VALUE ControlBackground;
	  
	DWORD  Spare[10]; /* Reserved for future use - must be zero */  

	} CDEMBEDDEDCONTACTLIST;
```

**Description :**

This CD record defines properties of an embedded contact list.  The fields in this structure are:
<ul><br>
<br>
Header - Signature and length of this record.<br>
Flags - <br>
SelectedBackground - Selected background color.  <br>
SelectedText -  <br>
ControlBackground - Control background.<br>
Spare - Reserved for future use - must be zero.  <br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.</ul>



**See Also :**
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---

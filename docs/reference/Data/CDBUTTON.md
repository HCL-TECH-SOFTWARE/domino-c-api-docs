##### Data Type : Composite Data
##### CDBUTTON - Defines the appearance of a button in a rich text field.
---
```
#include <editods.h>
```

**Definition :**

typedef struct
 {
 WSIG  Header; /* Signature and length of this record. */
 WORD  Flags; 
 WORD  Width;
 WORD  Height;
 WORD Lines;
 FONTID  FontID;
 /* Button Text Follows */
 } CDBUTTON;


**Description :**

This structure defines the appearance of a button in a rich text field. <br>
<br>
Header:	Defines this composite data item as a CDBUTTON item.<br>
Flags:	Optional. See BUTTON_xxx for optional values. <br>
Width:	Specifies the width of the button in TWIPS (see the symbolic definition for ONEINCH for more information).<br>
Height:	Reserved.  Should be set to NULL.<br>
Lines:	Specifies the maximum number of lines of text to use to display the button text.<br>
FontID:	Specifies the font, size, and color of the text on the face of the button. See FONTIDFIELDS for the definition of FontID.<br>
<br>
Immediately following this structure is a packed string containing the text that appears on the face of the button.<br>
<br>
	For a button with type information, the CDBUTTON record may be followed by a CDDATAFLAGS structure.<br>
<br>
Note that CDBUTTON records reside in items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on structures of this type when accessing these records in an item in a note.


**See Also :**
[BUTTON_xxx](/domino-c-api-docs/reference/Symb/BUTTON_xxx)
[CDDATAFLAGS](/domino-c-api-docs/reference/Data/CDDATAFLAGS)
[ONEINCH](/domino-c-api-docs/reference/Symb/ONEINCH)
---

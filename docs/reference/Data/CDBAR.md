##### Data Type : Composite Data
##### CDBAR - Defines the appearance of a collapsible section in a rich text field.
---
```
#include <editods.h>
```
**Description :**

This structure defines the appearance of the bar used with collapsible sections.

	Header:  Defines this composite data item as a CDBAR item.
	Flags:  This can be set to any of the values that begin with BARREC_
	FontID:  Specifies the font, size, and color of the bar title. See 
FONTIDFIELDS for the definition of FontID.

	If the BARREC_HAS_COLOR bit is set in the Flags field then immediately 
following this structure there will be a WORD that identifies the value of the 
color. This color value comes from the defines in the file COLORID.H that begin 
with NOTES_COLOR_xxx. If the BARREC_ISFORMULA bit is set in the Flags field 
then the next thing will be a formula, otherwise it will be the text of the 
title.

	For collapsible sections indicated by a tab or a tab with a diagonal 
border, the CDBAR record (with its Flags member set to BARREC_BORDER_OTHER) is 
followed by a CDDATAFLAGS structure with its variable Flags data border set to 
BARREC_DATA_BORDER_TAB (for tab) or BARREC_DATA_BORDER_DIAG (for diagonal). 

	Note that CDBAR records reside in items of type TYPE_COMPOSITE. 
Therefore, API programs that run on non-Intel architecture platforms must 
perform host/canonical conversion on structures of this type when accessing 
these records in an item in a note.

**See Also :**
[BARREC_xxx](/domino-c-api-docs/reference/Symb/BARREC_xxx)
[BAR_VERSIONxxx](/domino-c-api-docs/reference/Symb/BAR_VERSIONxxx)
[CDDATAFLAGS](/domino-c-api-docs/reference/Data/CDDATAFLAGS)
[GETBORDERTYPE](/domino-c-api-docs/reference/Func/GETBORDERTYPE)
[SETBORDERTYPE](/domino-c-api-docs/reference/Func/SETBORDERTYPE)
---

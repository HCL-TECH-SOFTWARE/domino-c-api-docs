##### Data Type : Composite Data
##### CDDOCUMENT - Defines the attributes of a form.
---
```
#include <editods.h>
```
**Description :**

This defines the structure of the document information field in a form note. A 
document information field is an item with name $INFO (ITEM_NAME_DOCUMENT) and 
data type TYPE_COMPOSITE. The document information field defines attributes of 
documents created with that form.

Header: Defines this composite data item as a CDDOCUMENT item.
PaperColor: Background color of document:
	0 black
	1 white
	2 gray
	3 lt. green
	4 green
	5 lt. yellow
	6 yellow
	7 cyan
	8 lt. cyan
	9 red
	10 green
	11 blue
	12 magenta
	13 yellow
	14 cyan
	15 dk read
	16 dk green
	17  dk blue 
	18  dk magenta
	19 dk yellow
	20 dk cyan
	21 - 240 palette color table index

FormFlags: Defines various attributes.  See TPL_FLAG_xxx for details.
NotePrivileges: Privileges for notes created with this form.
FormFlags2: Defines various attributes.  See TPL_FLAG_xxx for details.
InherFieldNameLength:
PaperColorExt: PaperColor value overrides PaperColorExt. 
PaperColorValue: RGB 3 Component Color value (Please see COLOR_VALUE).
FormFlags3: Defines various attributes.  See TPL_FLAG_xxx for details.

Since this field is of type TYPE_COMPOSITE, API programs that run on non-Intel 
architecture platforms must perform host/canonical conversion when accessing a 
CDDOCUMENT structure in a document information field item.

**See Also :**
[COLOR_VALUE](/reference/Data/COLOR_VALUE)
[TPL_FLAG_xxx](/reference/Symb/TPL_FLAG_xxx)
---

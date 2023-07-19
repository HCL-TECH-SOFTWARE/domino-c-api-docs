##### Data Type : Composite Data
##### CDDOCUMENT - Defines the attributes of a form.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BSIG Header;
   WORD PaperColor;   /* Color of the paper being used */
   WORD FormFlags;   /* Form Flags */
   WORD NotePrivileges;  /* Privs for notes created when
                                    using form */
/*
   WARNING!!! Fields below this comment were not zeroed in builds
   prior to 100.  A mechanism has been set up to use them however.
   dload checks the TPL_FLAG_SPARESOK bit in the flags word.  If it
   is not set, all of the storage after this comment is zeroed.  On
   save, dsave makes sure the unused storage is zero and sets the bit.
*/
   WORD FormFlags2;             /* more Form Flags */
   WORD InherFieldNameLength;   /* Length of the name, which follows
                                   this struct */

   WORD PaperColorExt;          /* Palette Color of the paper being
                                   used. Index into 240 color table.
	       New in V4. */
 COLOR_VALUE PaperColorValue; /* Paper Color: As of v5.0 stored as
                                   RGB, other formats possible */
	WORD FormFlags3;
	WORD Spare[1];

/* ... now the Inherit Field Name string */
/* ... now the Text Field Name string indicating which field to
       append version number to */
} CDDOCUMENT;

**Description :**

This defines the structure of the document information field in a form note. A document information field is an item with name $INFO (ITEM_NAME_DOCUMENT) and data type TYPE_COMPOSITE. The document information field defines attributes of documents created with that form.<br>
<br>
Header:	Defines this composite data item as a CDDOCUMENT item.<br>
PaperColor:	Background color of document:
<ul><br>
	0	black<br>
	1	white<br>
	2	gray<br>
	3	lt. green<br>
	4	green<br>
	5	lt. yellow<br>
	6	yellow<br>
	7	cyan<br>
	8	lt. cyan<br>
	9	red<br>
	10	green<br>
	11	blue<br>
	12	magenta<br>
	13	yellow<br>
	14	cyan<br>
	15	dk read<br>
	16	dk green<br>
	17 	dk blue <br>
	18 	dk magenta<br>
	19	dk yellow<br>
	20	dk cyan<br>
	21 - 240	palette color table index<br>
<br>
FormFlags:	Defines various attributes.  See TPL_FLAG_xxx for details.<br>
NotePrivileges:	Privileges for notes created with this form.<br>
FormFlags2:	Defines various attributes.  See TPL_FLAG_xxx for details.<br>
InherFieldNameLength:<br>
PaperColorExt:	PaperColor value overrides PaperColorExt. <br>
PaperColorValue:	RGB 3 Component Color value (Please see COLOR_VALUE).<br>
FormFlags3:	Defines various attributes.  See TPL_FLAG_xxx for details.<br>
<br>
Since this field is of type TYPE_COMPOSITE, API programs that run on non-Intel architecture platforms must perform host/canonical conversion when accessing a CDDOCUMENT structure in a document information field item.</ul>



**See Also :**
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[TPL_FLAG_xxx](/domino-c-api-docs/reference/Symb/TPL_FLAG_xxx)
---

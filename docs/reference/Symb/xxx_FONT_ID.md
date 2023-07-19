##### Symbolic Value : Font
##### xxx_FONT_ID - Font ID values for pre-defined fonts
---
```
#include <fontid.h>
```

**Symbolic Values :**

	DEFAULT_FONT_ID	  -  FONTID for the Domino default font. This default is normally plain black 10-point Helvetica.

	DEFAULT_BOLD_FONT_ID	  -  FONTID for the Domino default font with the bold attribute set.

	DEFAULT_SMALL_FONT_ID	  -  FONTID for the Domino default "small" font. This font is normally plain black 9-point Helvetica.

	DEFAULT_PPEN_FONT_ID	  -  FONTID for the default permanent pen font. This font is a bold red version of the default font; some systems may not be able to display this font in red.

	FOREIGN_FONT_ID	  -  FONTID for the default font for "foreign" text. This font is normally a plain black 10-point fixed-pitch font.


**Description :**

These macros return FONTID values for the predefined Domino fonts.


**Sample Usage :**
```
nError = CompoundTextAddTextExt (
hCompound,                 /* handle to CompoundText context */
dwStyleID,                 /* style ID */
DEFAULT_FONT_ID,           /* font ID */
StatText,                  /* text to add */
(DWORD) strlen (StatText), /* length of text */
"\r\n",                    /* newline delimiter - handle \r \n 
                                and combinations of \r\n */
COMP_PRESERVE_LINES,       /* preserve line breaks */
NULL);                     /* optional NLS_PINFO */
```

**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONT_FACE_xxx](/domino-c-api-docs/reference/Symb/FONT_FACE_xxx)
[NOTES_COLOR_xxx](/domino-c-api-docs/reference/Symb/NOTES_COLOR_xxx)
---

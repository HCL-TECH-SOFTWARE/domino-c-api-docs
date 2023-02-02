##### Symbolic Value : Font
##### xxx_FONT_ID - Font ID values for pre-defined fonts
---
##### #include <fontid.h>
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
[FONTID](D:/md_files/FONTID.md)
[FONT_FACE_xxx](D:/md_files/FONT_FACE_xxx.md)
[NOTES_COLOR_xxx](D:/md_files/NOTES_COLOR_xxx.md)
---

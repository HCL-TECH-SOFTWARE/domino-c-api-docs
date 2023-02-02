##### Data Type : Composite Data
##### CDTABLEBEGIN - Specifies the beginning of a table.
---
##### #include <editods.h>
**Description :**
This structure specifies the beginning of a table.  It contains information 
about the format and size of the table.    Use this structure when accessing a 
table in a rich text field.  As of R5, this structure is preceded by a 
CDPRETABLEBEGIN structure.  The CDPRETABLEBEGIN structure specifies additional 
table properties.

Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.
**See Also :**
[CDTABLEEND](D:/md_files/CDTABLEEND.md)
[CDTABLECELL](D:/md_files/CDTABLECELL.md)
[CDTABLE_xxx](D:/md_files/CDTABLE_xxx.md)
[CDPRETABLEBEGIN](D:/md_files/CDPRETABLEBEGIN.md)
---

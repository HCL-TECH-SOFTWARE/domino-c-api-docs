##### Data Type : Composite Data
##### CDTABLEEND - Specifies the end of a table.
---
##### #include <editods.h>
**Description :**
This structure specifies the end of a table. Use this structure when accessing 
a table in a rich text field.

Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.
**See Also :**
[CDTABLEBEGIN](D:/md_files/CDTABLEBEGIN.md)
[CDTABLECELL](D:/md_files/CDTABLECELL.md)
[ODSReadMemory](D:/md_files/ODSReadMemory.md)
[ODSWriteMemory](D:/md_files/ODSWriteMemory.md)
---

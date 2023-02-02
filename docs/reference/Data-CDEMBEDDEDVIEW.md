##### Data Type : Composite Data
##### CDEMBEDDEDVIEW - Specifies an embedded view.
---
##### #include <editods.h>
**Description :**
This CD Record describes a view as an embedded element.  A CDEMBEDDEDVIEW 
record will be preceded by a CDPLACEHOLDER record.  Further description of the 
embedded view can be found in the CD record CDPLACEHOLDER.

WSIG Header   Signature and length of this record.
DWORD Flags   EMBEDDEDVIEW_FLAG_xxx
FONTID SpareFontID
WORD RestrictFormulaLength If Formula length, then Formula follows CD record 
fixed length.
WORD WebLines
WORD NameLength;
WORD wSpare;
DWORD Spare[3]

**See Also :**
[CDPLACEHOLDER](D:/md_files/CDPLACEHOLDER.md)
[EMBEDDEDVIEW_FLAG_xxx](D:/md_files/EMBEDDEDVIEW_FLAG_xxx.md)
---

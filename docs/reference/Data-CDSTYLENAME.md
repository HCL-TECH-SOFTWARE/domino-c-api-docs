##### Data Type : Composite Data
##### CDSTYLENAME - Stores the style name for a PAB
---
##### #include <editods.h>
**Description :**
This structure stores the style name for a Paragraph Attributes Block (PAB).

        Header              Defines this composite data item as a CDSTYLENAME 
item.
        Flags                  Optional.  May be set to 0 or to one or more of 
STYLE_FLAG_xxx values.
        PABID                ID number of the Paragraph Attributes Block being 
named
                                     (see CDPABDEFINITION).
        StyleName       Style name character array.

If the flag STYLE_FLAG_FONTID is set, the record is followed by a FONTID.

If the flag STYLE_FLAG_PERMANENT is set, the record is followed by a word 
containing the length of the user name, then the user name (padded with a null 
byte if the user name is an odd length).  The user name is the name of the user 
who defined this named style.

**See Also :**
[CDPABDEFINITION](D:/md_files/CDPABDEFINITION.md)
[STYLE_FLAG_xxx](D:/md_files/STYLE_FLAG_xxx.md)
---

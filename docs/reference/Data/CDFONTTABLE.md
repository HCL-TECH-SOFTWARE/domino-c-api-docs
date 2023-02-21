##### Data Type : Composite Data
##### CDFONTTABLE - Used in creating a font table.
---
```
#include <editods.h>
```
**Description :**

This defines part of the structure of a font table item in a note.  A font 
table item in a note allows rich text in the note to be displayed using fonts 
other than those defined in FONT_FACE_xxx.

Font table items are items with name $Fonts (ITEM_NAME_FONTS) and data type 
TYPE_COMPOSITE.  A font table consists of a CDFONTTABLE structure followed by 
any number of CDFACE structures.

Note that font tables are items of type TYPE_COMPOSITE. Therefore, API programs 
that run on non-Intel architecture platforms must perform host/canonical 
conversion on CDFONTTABLE and CDFACE structures when accessing these records in 
a font table item in a note.

        Header        Tag identifying this as a CDFONTTABLE record
        Fonts            Number of CDFACE records following this header record


**Sample Usage :**
```
typedef struct {
   WSIG  Header;           /* Tag and length */
   WORD  Fonts;            /* Number of CDFACEs following */
} CDFONTTABLE;             /* Now come the CDFACE records... */

```
**See Also :**
[CDFACE](/domino-c-api-docs/reference/Data/CDFACE)
---

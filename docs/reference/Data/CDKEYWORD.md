##### Data Type : Composite Data
##### CDKEYWORD - Keyword values for a field
---
```
#include <editods.h>
```
**Description :**

This structure is the header of a record containing the predefined keywords 
allowed for a field (defined by a CDFIELD record).

        Header  Defines this composite data item as a CDKEYWORD item.
        FontID  Defines the font to be used in this field.  See FONTID.
        Keywords Number of keyword values
        Flags  If CDKEYWORD_RADIO, only one keyword value may be selected;  
otherwise, any number
                                     of values may be selected.

This record structure is followed by an array of bytes, one byte per keyword, 
indicating whether or not the corresponding keyword is enabled, '1' for On or 
'0' for Off.  Following this array is a Text_List containing the text of the 
allowable keywords.

**See Also :**
[CDFIELD](/domino-c-api-docs/reference/Data/CDFIELD)
[TYPE_xxx [TEXT_LIST]](/domino-c-api-docs/reference/Symb/TYPE_xxx [TEXT_LIST])
[CDKEYWORD_xxx](/domino-c-api-docs/reference/Symb/CDKEYWORD_xxx)
---

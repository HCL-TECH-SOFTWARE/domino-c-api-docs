##### Data Type : Composite Data
##### CDKEYWORD - Keyword values for a field
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG   Header;    /* Tag and length */
   FONTID FontID;    /* Font ID */
   WORD   Keywords;  /* number of keywords */
   WORD   Flags;     /* see CDKEYWORD_xxx */
/* char   OnOff[];      array indicating state */
/* char   TextValues[]; packed buffer of keyword text */
} CDKEYWORD;

**Description :**

This structure is the header of a record containing the predefined keywords allowed for a field (defined by a CDFIELD record).<br>
<br>
        Header 	Defines this composite data item as a CDKEYWORD item.<br>
        FontID		Defines the font to be used in this field.  See FONTID.<br>
        Keywords	Number of keyword values<br>
        Flags		If CDKEYWORD_RADIO, only one keyword value may be selected;  otherwise, any number<br>
                                     of values may be selected.<br>
<br>
This record structure is followed by an array of bytes, one byte per keyword, indicating whether or not the corresponding keyword is enabled, '1' for On or '0' for Off.  Following this array is a Text_List containing the text of the allowable keywords.


**See Also :**
[CDFIELD](/domino-c-api-docs/reference/Data/CDFIELD)
[TYPE_xxx [TEXT_LIST]](/domino-c-api-docs/reference/Symb/TYPE_xxx [TEXT_LIST])
[CDKEYWORD_xxx](/domino-c-api-docs/reference/Symb/CDKEYWORD_xxx)
---

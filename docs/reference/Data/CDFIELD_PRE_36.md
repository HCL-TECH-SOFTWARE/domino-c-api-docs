##### Data Type : Composite Data
##### CDFIELD_PRE_36 - * OBSOLETE * Defines the attributes of a field in a form.
---
```
#include <editods.h>
```

**Definition :**
```

/* 
 * (*** OBSOLETE ***) Pre-V1 Field Reference Record, 
 *  used in Forms (*** OBSOLETE ***) 
 */

typedef struct {
 WSIG Header;
 WORD Flags;  /* Field Flags */
 WORD DataType;  /* Alleged NSF Data Type */
 WORD ListDelim;  /* List Delimiters */
 NFMT NumberFormat; /* Number format, if applicable */ 
 TFMT TimeFormat; /* Time format, if applicable */
 FONTID FontID;  /* displayed font */
 WORD DVLength;  /* Default Value Formula */
 WORD ITLength;  /* Input Translation Formula */
 WORD Unused1;  /* Unused */
 WORD IVLength;  /* Input Validity Check Formula */
 WORD NameLength; /* NSF Item Name */
 WORD DescLength; /* Description of the item */
    /* Now comes variable part of the struct... */

} CDFIELD_PRE_36;  /* List of Text Values was added... */

```

**Description :**

This item is an obsolete definition of the attributes of a field in a form note. It is included in this reference for compatibility with forms created with pre-V1 releases of Notes.<br>
<br>
Header:                  Defines this composite data item as a CDFIELD item.<br>
Flags:                      Defines some field attributes (see Fxxx).<br>
DataType              Defines the datatype of the field being defined (see FIELD_TYPE_xxx).<br>
ListDelim                Defines the delimiters used to separate multi-values in a field. See LDELIM_xxx, LDDELIM_xxx.<br>
NumberFormat    If this is a number field, defines the number format.  See NFMT.<br>
TimeFormat          If this is a timedate field, defines the time format. See TFMT.<br>
FontID                      Defines the font to be used in this field.  See FONTID.<br>
DVLength               Length of this field's compiled Default Value formula.<br>
ITLength                 Length of this field's compiled Input Translation formula.    <br>
Unused1                 This field is unused, and should be set to zero.<br>
IVLength                 Length of this field's compiled Default Value formula.<br>
NameLength         Length of the name of this field.<br>
DescLength           Length of the description of this field.<br>
<br>
The above items are then followed by a series of zero or more packed strings, corresponding to the &quot;length&quot; parameters listed above. These packed strings must appear in the same order as the &quot;length&quot; parameters<br>



**See Also :**
[CDFIELD](/domino-c-api-docs/reference/Data/CDFIELD)
---

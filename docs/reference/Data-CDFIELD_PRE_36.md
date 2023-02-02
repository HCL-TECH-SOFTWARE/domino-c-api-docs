##### Data Type : Composite Data
##### CDFIELD_PRE_36 - * OBSOLETE * Defines the attributes of a field in a form.
---
##### #include <editods.h>
**Description :**
This item is an obsolete definition of the attributes of a field in a form 
note. It is included in this reference for compatibility with forms created 
with pre-V1 releases of Notes.

Header:                  Defines this composite data item as a CDFIELD item.
Flags:                      Defines some field attributes (see Fxxx).
DataType              Defines the datatype of the field being defined (see 
FIELD_TYPE_xxx).
ListDelim                Defines the delimiters used to separate multi-values 
in a field. See LDELIM_xxx, LDDELIM_xxx.
NumberFormat    If this is a number field, defines the number format.  See NFMT.
TimeFormat          If this is a timedate field, defines the time format. See 
TFMT.
FontID                      Defines the font to be used in this field.  See 
FONTID.
DVLength               Length of this field's compiled Default Value formula.
ITLength                 Length of this field's compiled Input Translation 
formula.    
Unused1                 This field is unused, and should be set to zero.
IVLength                 Length of this field's compiled Default Value formula.
NameLength         Length of the name of this field.
DescLength           Length of the description of this field.

The above items are then followed by a series of zero or more packed strings, 
corresponding to the "length" parameters listed above. These packed strings 
must appear in the same order as the "length" parameters

**See Also :**
[CDFIELD](D:/md_files/CDFIELD.md)
---

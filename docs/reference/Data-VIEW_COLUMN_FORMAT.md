##### Data Type : Views
##### VIEW_COLUMN_FORMAT - View column format descriptor.
---
##### #include <viewfmt.h>
**Description :**
This structure describes the format of one column in a view. This structure is 
one of the components of a $VIEWFORMAT item in a view note. A $VIEWFORMAT item 
contains one view column format descriptor per column.

All view notes contain a $VIEWFORMAT item (also known as a "View Table Format" 
item). A $VIEWFORMAT item is an item of TYPE_VIEW_FORMAT with item name 
VIEW_VIEW_FORMAT_ITEM. The item value of a $VIEWFORMAT item consists of a 
single VIEW_TABLE_FORMAT structure, followed by one VIEW_COLUMN_FORMAT 
structure for each column, followed by an  item name/formula/column title set 
for each column, followed by a VIEW_TABLE_FORMAT2 structure, followed by one 
VIEW_COLUMN_FORMAT2 structure for each column, followed by a VIEW_TABLE_FORMAT3 
structure.
**Sample Usage :**
```
VIEW_COLUMN_FORMAT ViewColumnFormat;

/*
 Create the VIEW_COLUMN_FORMAT item for column 1. Since this column
 is neither a TIME field or a NUMBER field, we don't need to set the
 TimeFormat or the NumberFormat fields.
 */

ViewColumnFormat.Signature = VIEW_COLUMN_FORMAT_SIGNATURE;
ViewColumnFormat.Flags1 = (VCF1_M_Sort | VCF1_M_SortCategorize);

ViewColumnFormat.DisplayWidth = 8;
ViewColumnFormat.FontID = DEFAULT_BOLD_FONT_ID;
ViewColumnFormat.Flags2 = 0;

ViewColumnFormat.FormatDataType = VIEW_COL_TEXT;
ViewColumnFormat.ListSep = LDDELIM_COMMA;

ViewColumnFormat.FormulaSize = wFormula_1_Len;
ViewColumnFormat.ItemNameSize = wItemName_1_Len;
ViewColumnFormat.TitleSize = 0;   /* No column title for categories */
ViewColumnFormat.ConstantValueSize = 0; /* RESERVED _ SHOULD BE 0 */

/*
 Convert the View Column Format structure for Col 1 to Domino canonical
 format and append it to the buffer. This increments pVFBuf to point
 to the next byte in the buffer after the View Column Format.
 */

ODSWriteMemory( &pVFBuf, _VIEW_COLUMN_FORMAT, &ViewColumnFormat, 1 );
```
**See Also :**
[VIEW_COLUMN_FORMAT2](D:/md_files/VIEW_COLUMN_FORMAT2.md)
[VIEW_TABLE_FORMAT](D:/md_files/VIEW_TABLE_FORMAT.md)
[VIEW_TABLE_FORMAT2](D:/md_files/VIEW_TABLE_FORMAT2.md)
---

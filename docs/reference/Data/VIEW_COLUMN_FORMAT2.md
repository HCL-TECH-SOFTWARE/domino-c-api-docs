##### Data Type : Views
##### VIEW_COLUMN_FORMAT2 - Extended View column format descriptor.
---
```
#include <viewfmt.h>
```

**Definition :**

typedef struct
{
   WORD   Signature;                  /* VIEW_COLUMN_FORMAT_SIGNATURE2 */
   FONTID HeaderFontID;               /* FontID of column header. */
   UNID   ResortToViewUNID;           /* UNID of view to switch to. */
   WORD   wSecondResortColumnIndex;   /* 0 based index of secondary resort 
column. */
   WORD   Flags3;      
   WORD   wHideWhenFormulaSize;
   WORD   wTwistieResourceSize;
   WORD   wCustomOrder;               /* V6 View Customization support */
   WORD   wCustomHiddenFlags;         /* V6 View Customization support */
	 COLOR_VALUE ColumnColor;      /* V6 - Column Text Color */
	COLOR_VALUE HeaderFontColor;      /* V6 - column header color */
} VIEW_COLUMN_FORMAT2;

**Description :**

This structure describes the format of one column in a view as of Notes Release 4. This structure is one of the components of a $VIEWFORMAT item in a view note. A $VIEWFORMAT item contains one extended view column format descriptor per column. Note: If you add variable data to this structure, store the packed, variable data AFTER the array of structures.  All view notes contain a $VIEWFORMAT item (also known as a &quot;View Table Format&quot; item).  A $VIEWFORMAT item is an item of TYPE_VIEW_FORMAT with item name VIEW_VIEW_FORMAT_ITEM. The item value of a $VIEWFORMAT item consists of a single VIEW_TABLE_FORMAT structure, followed by one VIEW_COLUMN_FORMAT structure for each column, followed by an item name/formula/column title set for each column, followed by a  VIEW_TABLE_FORMAT2 structure, followed by one VIEW_COLUMN_FORMAT2 structure for each column, followed by a VIEW_TABLE_FORMAT3 structure.


**See Also :**
[VCF3_xxx](/domino-c-api-docs/reference/Symb/VCF3_xxx)
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
[VIEW_TABLE_FORMAT](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT)
[VIEW_TABLE_FORMAT2](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT2)
---

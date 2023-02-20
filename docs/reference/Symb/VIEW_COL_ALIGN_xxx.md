##### Symbolic Value : Views
##### VIEW_COL_ALIGN_xxx - View column display alignment and header alignment.
---
```
#include <viewfmt.h>
```
**Description :**

View column display alignment and header alignment.

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
   ViewColumnFormat.Flags2 = VIEW_COL_ALIGN_RIGHT << VCF2_S_HeaderAlignment | 
VCF2_M_DisplayAlignment & VIEW_COL_ALIGN_RIGHT| VIEW_COL_RTL << 
VCF2_S_DisplayReadingOrder | VIEW_COL_RTL << VCF2_S_HeaderReadingOrder;

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
[VCF2_xxx](/reference/Symb/VCF2_xxx)
[VIEW_COLUMN_FORMAT](/reference/Data/VIEW_COLUMN_FORMAT)
---

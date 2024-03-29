##### Data Type : Views
##### VIEW_TABLE_FORMAT - View table format descriptor.
---
```
#include <viewfmt.h>
```

**Definition :**
```
typedef struct {
   VIEW_FORMAT_HEADER Header;
   WORD Columns;            /* Number of columns */
   WORD ItemSequenceNumber; /* Seq. number for unique item names */
   WORD Flags;              /* (see VIEW_TABLE_xxx) */
   WORD Flags2;             /* Flags */
} VIEW_TABLE_FORMAT;
```

**Description :**

This structure contains the view table format descriptor.  All view notes contain a $VIEWFORMAT item (also known as a &quot;View Table Format&quot; item). A $VIEWFORMAT item is an item of TYPE_VIEW_FORMAT with item name VIEW_VIEW_FORMAT_ITEM. The item value of a $VIEWFORMAT item consists of a single VIEW_TABLE_FORMAT structure, followed by one VIEW_COLUMN_FORMAT structure for each column, followed by an  item name/formula/column title set for each column, followed by a VIEW_TABLE_FORMAT2 structure, followed by one VIEW_COLUMN_FORMAT2 structure for each column, followed by a VIEW_TABLE_FORMAT3 structure.


**Sample Usage :**
```
/*
 Initialize the VIEW_TABLE_FORMAT structure.
 */

ViewTableFormat.Header.Version = VIEW_FORMAT_VERSION;
ViewTableFormat.Header.ViewStyle = VIEW_STYLE_TABLE;
ViewTableFormat.Columns = wNumColumns;
ViewTableFormat.ItemSequenceNumber = 0;  /* Reserved - should be 0 */
    
ViewTableFormat.Flags = VIEW_TABLE_FLAG_FLATINDEX |
                        VIEW_TABLE_FLAG_DISP_UNREADDOCS;

ViewTableFormat.Flags2 = VIEW_TABLE_FLAT_HEADINGS;

/*
 Call ODSWriteMemory to convert the VIEW_TABLE_FORMAT structure from
 host-specific format to Domino canonical format, and copy it into the 
 buffer at location pVFBuf. ODSWriteMemory increments pVFBuf to point
 to the next byte in the buffer after the written data structure.
 */

ODSWriteMemory( &pVFBuf, _VIEW_TABLE_FORMAT, &ViewTableFormat, 1 );
```

**See Also :**
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
[VIEW_FORMAT_HEADER](/domino-c-api-docs/reference/Data/VIEW_FORMAT_HEADER)
[VIEW_TABLE_FORMAT2](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT2)
[VIEW_TABLE_xxx (VIEW_TABLE_FORMAT)](/domino-c-api-docs/reference/Symb/VIEW_TABLE_xxx (VIEW_TABLE_FORMAT))
[VIEW_TABLE_xxx (VIEW_TABLE_FORMAT)](/domino-c-api-docs/reference/Symb/VIEW_TABLE_xxx (VIEW_TABLE_FORMAT))
---

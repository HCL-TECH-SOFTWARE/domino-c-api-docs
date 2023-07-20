##### Data Type : Views
##### IXCOLDESC - Specifies an entry in the column descriptor block set up by a view.
---
```
#include <ixview.h>
```

**Definition :**
```
typedef struct
	{
	FLAG Sort:1;      /* Add column to sort */
	FLAG SortCategorize:1;    /* Make column a category */
	FLAG SortPermute:1;     /* Make column permuted if multi-valued. */
	FLAG SortDescending:1;    /* Sort in descending order (ascending if 
FALSE) */
	FLAG Hidden:1;      /* Normally hide column */
	FLAG Response:1;     /* Response column */
	FLAG Selected:1;     /* Column is selected */
	FLAG HideDetail:1;     /* Do not show detail on subtotalled columns */
	FLAG Icon:1;      /* Icon column. */
	FLAG spare1:8;      /* spare flags */

	WORD ColumnTitleLength;    /* Column title string length */
	DHANDLE hColumnTitle;    /* Column title string handle */
	WORD ItemNameLength;    /* Column item name string length */
	DHANDLE hItemName;     /* NSF Item name for column */
	WORD FormulaLength;     /* Formula buffer length */ 
	FORMULAHANDLE hFormula;    /* Formula buffer handle */
	WORD ConstantValueLength;   /* Constant value length */
	DHANDLE hConstantValue;    /* Constant value handle */
	WORD ColumnWidth;     /* Column width in characters */
	WORD TextMax;      /* Maximum text string size */
	WORD Alignment;      /* Column alignment */
	NFMT NumberFormat;     /* Number format specification */
	TFMT TimeFormat;     /* Time format specification */
	WORD FormatDataType;    /* Last specified format data type */
	WORD ListSep;      /* List Separator */
	WORD SubtotalCode;     /* Subtotalling code */
	} IXCOLDESC;

```

**Description :**

This structure specifies an entry in the column descriptor block set up by a view for imports/exports (one entry per view column).  The structure, VIEWIXDATA, contains a handle to the column descriptor block.


**See Also :**
[VIEWIXDATA](/domino-c-api-docs/reference/Data/VIEWIXDATA)
---

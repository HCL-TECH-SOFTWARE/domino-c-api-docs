##### Symbolic Value : Rich Text
##### CDTABLECELL_xxx - CDTABLECELL - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	CDTABLECELL_USE_BKGCOLOR	  -  A cell background color is specified.

	CDTABLECELL_USE_V42BORDERS	  -  The table was created with Domino or Notes Release 4.5 or later and contains border width information not available in previous releases.

	CDTABLECELL_INVISIBLEH	  -  Set if this cell is one of a group of merged cells, is spanned (made invisible) and is in the same row as the cell that is doing the spanning.

	CDTABLECELL_INVISIBLEV	  -  Set if this cell is one of a group of merged cells, is spanned (made invisible) and is not in the same row as the cell that is doing the spanning.

	CDTABLECELL_USE_GRADIENT	  -  The cell background uses a top to bottom gradient.

	CDTABLECELL_VALIGNCENTER	  -  Align cell contents vertically to the center.

	CDTABLECELL_GRADIENT_LTR	  -  The cell background uses a gradient left to right gradient.

	CDTABLECELL_VALIGNBOTTOM	  -  Align cell contents vertically to the bottom.

	CDTABLECELL_COLUMN_HEADER	  -  The cell column header.

	CDTABLECELL_ROW_HEADER	  -  The cell row header.


**Description :**

Flags that further describe a cell in a table.


**See Also :**
[CDTABLECELL](/domino-c-api-docs/reference/Data/CDTABLECELL)
---

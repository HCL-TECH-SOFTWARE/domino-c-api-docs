##### Symbolic Value : Rich Text
##### PARADELIM_xxx - Paragraph recognition method.
---
```
#include <ods.h>
```

**Symbolic Values :**

	PARADELIM_BLANKLINE	  -  New paragraph on each blank line.

	PARADELIM_INDENTEDLINE	  -  New paragraph on any indented line.

	PARADELIM_ANYBLANKLINE	  -  New paragraph on each blank line, hard CRs on each line. Note: PARADELIM_ANYBLANKLINE sets justification = None.

	PARADELIM_ANYLINE	  -  New paragraph on each line.

	PARADELIM_COLON	  -  New paragraph on lines of the form "fieldname: text".

	PARADELIM_RTLREADING	  -  New paragraph on RTL reading order.


**Description :**

WORD flag used as 5th argument to ConvertItemToCompositeExt.  During conversion of plain LMBCS text or an existing TYPE_TEXT item to a TYPE_COMPOSITE item, the location of logical paragraphs must be determined and their presentation preserved by building the appropriate Composite Data records into the converted item.  The Notes Workstation application uses this information to correctly present the Rich Text body to the user.


**See Also :**
[ConvertItemToCompositeExt](/domino-c-api-docs/reference/Func/ConvertItemToCompositeExt)
---

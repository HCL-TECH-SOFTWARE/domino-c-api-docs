##### Symbolic Value : Rich Text
##### PABFLAG2_xxx - CDPABDEFINITION - Flags2
---
```
#include <editdflt.h>
```

**Symbolic Values :**

	PABFLAG2_HIDE_WEB	  -  Hide paragraph when viewed with a Web browser.

	PABFLAG2_CHECKEDLIST	  -  Set if check list is checked off.

	PABFLAG2_LM_OFFSET	  -  LeftMargin is an offset value.

	PABFLAG2_LM_PERCENT	  -  LeftMargin is a percentage value.

	PABFLAG2_FLLM_OFFSET	  -  First Line LeftMargin is an offset value.

	PABFLAG2_FLLM_PERCENT	  -  First Line LeftMargin is a percentage value.

	PABFLAG2_RM_OFFSET	  -  RightMargin is an offset value.

	PABFLAG2_RM_PERCENT	  -  RightMargin is a percentage value.

	PABFLAG2_LM_DEFAULT	  -  LeftMargin Default.

	PABFLAG2_FLLM_DEFAULT	  -  First Line LeftMargin Default.

	PABFLAG2_RM_DEFAULT	  -  RightMargin Default.

	PABFLAG2_CIRCLELIST	  -  Paragraph contains a circle list.

	PABFLAG2_SQUARELIST	  -  Paragraph contains a square list.

	PABFLAG2_UNCHECKEDLIST	  -  Set if check list is unchecked.

	PABFLAG2_BIDI_RTLREADING	  -  Set if right to left reading order.

	PABFLAG2_MORE_FLAGS	  -  Set if one or two DWORD extensions follow CDPABDEFINITION.

	PABFLAG2_HIDEBITS	  -  PABFLAG2_HIDE_WEB

	PABFLAG2_CHECKLIST	  -  Paragraph contains a check list - PABFLAG2_UNCHECKEDLIST | PABFLAG2_CHECKEDLIST

	PABFLAG2_MARGIN_DEFAULTS_MASK	  -  PABFLAG2_LM_DEFAULT | PABFLAG2_RM_DEFAULT | PABFLAG2_FLLM_DEFAULT

	PABFLAG2_MARGIN_MASK	  -  PABFLAG2_MARGIN_STYLES_MASK | PABFLAG2_MARGIN_DEFAULTS_MASK

	PABFLAG2_MARGIN_STYLES_MASK	  -  PABFLAG2_LM_OFFSET | PABFLAG2_LM_PERCENT | PABFLAG2_FLLM_OFFSET | PABFLAG2_FLLM_PERCENT | PABFLAG2_RM_OFFSET | PABFLAG2_RM_PERCENT

	PABFLAG2_ROMANUPPERLIST	  -  PABFLAG2_CHECKEDLIST | PABFLAG2_CIRCLELIST

	PABFLAG2_ROMANLOWERLIST	  -  PABFLAG2_CHECKEDLIST | PABFLAG2_SQUARELIST

	PABFLAG2_ALPHAUPPERLIST	  -  PABFLAG2_SQUARELIST | PABFLAG2_CIRCLELIST

	PABFLAG2_ALPHALOWERLIST	  -  PABFLAG2_CHECKEDLIST | PABFLAG2_SQUARELIST | PABFLAG2_CIRCLELIST


**Description :**

Possible optional values for the Flags2 member of the CDPABDEFINITION structure.  These symbols specify additional paragraph attribute flags.  If the Flags2 member of CDPABDEFINITION is set to PABFLAG2_MORE_FLAGS, the CDPABDEFINITION may be followed by a DWORD extension. If the value of this DWORD extension is EXTENDEDPABFLAGS3, then a second DWORD extension may be present with a value of PABFLAG3_HIDE_EE. These DWORD extensions follow the six R5 margin extension WORDs, if they are present.


**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[EXTENDEDPABFLAGS3](/domino-c-api-docs/reference/Symb/EXTENDEDPABFLAGS3)
---

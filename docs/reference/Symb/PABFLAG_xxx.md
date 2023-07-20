##### Symbolic Value : Rich Text
##### PABFLAG_xxx - CDPABDEFINITION - Flags
---
```
#include <editdflt.h>
```

**Symbolic Values :**

	PABFLAG_PAGINATE_BEFORE	  -  Start new page with this paragraph

	PABFLAG_KEEP_WITH_NEXT	  -  Don't separate this and next paragraph

	PABFLAG_KEEP_TOGETHER	  -  Don't split lines in paragraph

	PABFLAG_PROPAGATE	  -  Propagate even PAGINATE_BEFORE and KEEP_WITH_NEXT

	PABFLAG_HIDE_RO	  -  Hide paragraph in R/O mode

	PABFLAG_HIDE_RW	  -  Hide paragraph in R/W mode

	PABFLAG_HIDE_PR	  -  Hide paragraph when printing

	PABFLAG_DISPLAY_RM	  -  Not used in Relase 5.0 and later. In earlier releases, this flag had to be set if the paragraph is in a table.

	PABFLAG_HIDE_UNLINK	  -  The pab was saved in Release 4. Set this bit or the Notes client will assume the pab was saved pre-Release 4 and will thus "link" these bit definitions (assign the right one to the left one) since preview did not exist pre-Release 4:
PABFLAG_HIDE_PV = PABFLAG_HIDE_RO
PABFLAG_HIDE_PVE = PABFLAG_HIDE_RW

	PABFLAG_HIDE_CO	  -  Hide paragraph when copying/forwarding

	PABFLAG_BULLET	  -  Display paragraph with bullet

	PABFLAG_HIDE_IF	  -  Use the hide when formula (if the formula is present)

	PABFLAG_NUMBEREDLIST	  -  Display paragraph with number

	PABFLAG_HIDE_PV	  -  Hide paragraph when previewing

	PABFLAG_HIDE_PVE	  -  Hide paragraph when editing in the preview pane

	PABFLAG_HIDE_NOTES	  -  Hide paragraph from Notes clients

	PABFLAG_HIDEBITS	  -  (PABFLAG_HIDE_RO | PABFLAG_HIDE_RW | PABFLAG_HIDE_CO | PABFLAG_HIDE_PR | PABFLAG_HIDE_PV | PABFLAG_HIDE_PVE | PABFLAG_HIDE_IF | PABFLAG_HIDE_NOTES)


**Description :**

These symbols may be used to set paragraph attributes in the Flags member of the CDPABDEFINITION record.  They may be OR'd together for multiple attributes.


**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
---

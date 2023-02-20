##### Symbolic Value : Miscellaneous
##### JUSTIFY_xxx - Definitions for the JustifyMode member of the CDPABDEFINITION structure.
---
```
#include <editdflt.h>
```
**Description :**

These symbols define how paragraphs will be aligned or justified in a rich text 
field.

**Sample Usage :**
```
   pabdef.Header.Signature = SIG_CD_PABDEFINITION;
    pabdef.Header.Length = ODSLength( _CDPABDEFINITION );
    pabdef.PABID = PARA_STYLE_ID;
    pabdef.JustifyMode = JUSTIFY_CENTER;
    pabdef.LineSpacing = DEFAULT_LINE_SPACING;
    pabdef.ParagraphSpacingBefore = DEFAULT_ABOVE_PAR_SPACING;
    pabdef.ParagraphSpacingAfter = DEFAULT_BELOW_PAR_SPACING;
    pabdef.LeftMargin = DEFAULT_LEFT_MARGIN;
    pabdef.RightMargin = DEFAULT_RIGHT_MARGIN;
    pabdef.FirstLineLeftMargin = DEFAULT_FIRST_LEFT_MARGIN;
    pabdef.Tabs = DEFAULT_TABS;
    pabdef.Tab[0] = DEFAULT_TAB_INTERVAL;
    pabdef.Flags = 0;
```
**See Also :**
[CDPABDEFINITION](/reference/Data/CDPABDEFINITION)
---

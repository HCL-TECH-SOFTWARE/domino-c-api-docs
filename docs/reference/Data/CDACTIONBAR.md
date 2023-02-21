##### Data Type : Composite Data
##### CDACTIONBAR - Action button bar attributes for a form or view
---
```
#include <actods.h>
```
**Description :**

The designer of a form or view may define custom actions for that form or 
view.  The attributes for the button bar are stored in the CDACTIONBAR record 
in the $ACTIONS and/or $V5ACTIONS item for the design note describing the form 
or view.

The fields in this structure are:

Header      Identifies this as a CDACTIONBAR record
BackColor      Background color
LineColor      Line color
LineStyle      Line style code (see ACTION_LINE_xxx)
BorderStyle      Border style code (see ACTION_BORDER_xxx)
BorderWidth    Width of the border, in pixels
dwFlags      Flag values (see ACTION_BAR_FLAG_xxx)
ShareID      Last ID of Shared Actions
FontID
BtnHeight          Height of the button
HeightSpc        Height spacing

This record is followed by CDACTIONBAREXT, then CDACTION records defining the 
available actions.

**See Also :**
[ACTION_BAR_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTION_BAR_FLAG_xxx)
[ACTION_BORDER_xxx](/domino-c-api-docs/reference/Symb/ACTION_BORDER_xxx)
[ACTION_LINE_xxx](/domino-c-api-docs/reference/Symb/ACTION_LINE_xxx)
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
[CDACTIONBAREXT](/domino-c-api-docs/reference/Data/CDACTIONBAREXT)
---

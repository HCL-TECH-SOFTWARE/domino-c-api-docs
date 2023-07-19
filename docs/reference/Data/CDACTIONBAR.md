##### Data Type : Composite Data
##### CDACTIONBAR - Action button bar attributes for a form or view
---
```
#include <actods.h>
```

**Definition :**

typedef struct {
   BSIG   Header;      /* Signature and Length */
 WORD   BackColor;   /* Background color index */
 WORD   LineColor;   /* Line color index */
 WORD   LineStyle;   /* Style of line */
 WORD   BorderStyle; /* Border style */
 WORD   BorderWidth; /* Border width (twips) */
 DWORD  dwFlags;
 DWORD  ShareID;     /* ID of Shared Action */
   FONTID FontID;
   WORD   BtnHeight;   /* Height of the Button */
   WORD   HeightSpc;   /* Height spacing */
} CDACTIONBAR;

**Description :**

The designer of a form or view may define custom actions for that form or view.  The attributes for the button bar are stored in the CDACTIONBAR record in the $ACTIONS and/or $V5ACTIONS item for the design note describing the form or view.
<ul><br>
<br>
The fields in this structure are:<br>
<br>
Header	     Identifies this as a CDACTIONBAR record<br>
BackColor	     Background color<br>
LineColor	     Line color<br>
LineStyle	     Line style code (see ACTION_LINE_xxx)<br>
BorderStyle	     Border style code (see ACTION_BORDER_xxx)<br>
BorderWidth    Width of the border, in pixels<br>
dwFlags	     Flag values (see ACTION_BAR_FLAG_xxx)<br>
ShareID	     Last ID of Shared Actions<br>
FontID<br>
BtnHeight          Height of the button<br>
HeightSpc        Height spacing<br>
<br>
This record is followed by CDACTIONBAREXT, then CDACTION records defining the available actions.</ul>



**See Also :**
[ACTION_BAR_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTION_BAR_FLAG_xxx)
[ACTION_BORDER_xxx](/domino-c-api-docs/reference/Symb/ACTION_BORDER_xxx)
[ACTION_LINE_xxx](/domino-c-api-docs/reference/Symb/ACTION_LINE_xxx)
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
[CDACTIONBAREXT](/domino-c-api-docs/reference/Data/CDACTIONBAREXT)
---

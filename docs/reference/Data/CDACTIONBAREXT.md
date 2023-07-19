##### Data Type : Composite Data
##### CDACTIONBAREXT - Action bar attributes.
---
```
#include <actods.h>
```

**Definition :**

typedef struct {
	WSIG  Header;
	COLOR_VALUE BackColor;
	COLOR_VALUE LineColor;
	COLOR_VALUE FontColor;
	COLOR_VALUE ButtonColor;
	WORD  BtnBorderDisplay;
	WORD  wAppletHeight;  /* This is always recalculated on save */
	WORD  wBarBackgroundRepeat; /* See ACTION_BAR_BACKGROUND_xxx types. */
	BYTE  BtnWidthStyle;
	BYTE  BtnTextJustify;
	WORD  wBtnWidthAbsolute; /* Valid only if BtnWidthStyle is 
ACTIONBAR_BUTTON_WIDTH_ABSOLUTE */
	WORD  wBtnInternalMargin; /* Extra margin on the inside right and 
	         left edges of a button to space image and text away from 
	         the right and left edges. */
	DWORD  dwFlags;   /* See ACTIONBAREXT_xxx flags */
	FONTID barFontID;   /* Used in conjunction with barHeight */
	LENGTH_VALUE barHeight;
	DWORD  Spare[12];
	/* Leaving many spares for future mouse down/ mouse over colors and 
whatever else we want */
} CDACTIONBAREXT;

**Description :**

This CD record defines the Action Bar attributes.  It is an extension of the CDACTIONBAR record.  It is found within a <b>$V5ACTIONS </b>item and is preceded by a CDACTIONBAR record.<br>
<br>
The fields in this record are:<br>
<br>
Header - Signature and Length of this CD record<br>
BackColor - Background color of action bar<br>
LineColor - Color of action bar bottom border (this &quot;old&quot; border style has been deprecated in Notes/Domino 6)<br>
FontColor - Font color of text on action buttons <br>
ButtonColor - Background color of action butons<br>
BtnBorderDisplay - Border display properties of action buttons, see ACTION_SET_3D_xxx<br>
wAppletHeight - Applet height. This is always recalculated on save<br>
wBarBackgroundRepeat - See ACTION_BAR_BACKGROUND_xxx types<br>
BtnWidthStyle -  See ACTIONBAR_BUTTON_WIDTH_xxx<br>
BtnTextJustify -  See ACTIONBAR_BUTTON_TEXT_<br>
wBtnWidthAbsolute - Reflects the fixed width of an action button if BtnWidthStyle member is set to ACTIONBAR_BUTTON_WIDTH_ABSOLUTE<br>
wBtnInternalMargin - Extra margin on the inside right and left edges of a button to space image and text away from the right and left edges<br>
dwFlags - See ACTIONBAREXT_xxx flags<br>
barFontID - Used in conjunction with barHeight<br>
barHeight<br>
Spare[12]


**See Also :**
[ACTIONBAR_BACKGROUND_xxx](/domino-c-api-docs/reference/Symb/ACTIONBAR_BACKGROUND_xxx)
[ACTIONBAR_BUTTON_TEXT_](/domino-c-api-docs/reference/Symb/ACTIONBAR_BUTTON_TEXT_)
[ACTIONBAR_BUTTON_WIDTH_xxx](/domino-c-api-docs/reference/Symb/ACTIONBAR_BUTTON_WIDTH_xxx)
[ACTION_SET_3D_xxx](/domino-c-api-docs/reference/Symb/ACTION_SET_3D_xxx)
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
[CDACTIONBAR](/domino-c-api-docs/reference/Data/CDACTIONBAR)
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
---

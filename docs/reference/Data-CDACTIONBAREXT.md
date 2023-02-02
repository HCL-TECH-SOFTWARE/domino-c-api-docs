##### Data Type : Composite Data
##### CDACTIONBAREXT - Action bar attributes.
---
##### #include <actods.h>
**Description :**
This CD record defines the Action Bar attributes.  It is an extension of the 
CDACTIONBAR record.  It is found within a $V5ACTIONS item and is preceded by a 
CDACTIONBAR record.

The fields in this record are:

Header - Signature and Length of this CD record
BackColor - Background color of action bar
LineColor - Color of action bar bottom border (this "old" border style has been 
deprecated in Notes/Domino 6)
FontColor - Font color of text on action buttons 
ButtonColor - Background color of action butons
BtnBorderDisplay - Border display properties of action buttons, see 
ACTION_SET_3D_xxx
wAppletHeight - Applet height. This is always recalculated on save
wBarBackgroundRepeat - See ACTION_BAR_BACKGROUND_xxx types
BtnWidthStyle -  See ACTIONBAR_BUTTON_WIDTH_xxx
BtnTextJustify -  See ACTIONBAR_BUTTON_TEXT_
wBtnWidthAbsolute - Reflects the fixed width of an action button if 
BtnWidthStyle member is set to ACTIONBAR_BUTTON_WIDTH_ABSOLUTE
wBtnInternalMargin - Extra margin on the inside right and left edges of a 
button to space image and text away from the right and left edges
dwFlags - See ACTIONBAREXT_xxx flags
barFontID - Used in conjunction with barHeight
barHeight
Spare[12]
**See Also :**
[ACTIONBAR_BACKGROUND_xxx](D:/md_files/ACTIONBAR_BACKGROUND_xxx.md)
[ACTIONBAR_BUTTON_TEXT_](D:/md_files/ACTIONBAR_BUTTON_TEXT_.md)
[ACTIONBAR_BUTTON_WIDTH_xxx](D:/md_files/ACTIONBAR_BUTTON_WIDTH_xxx.md)
[ACTION_SET_3D_xxx](D:/md_files/ACTION_SET_3D_xxx.md)
[CDACTION](D:/md_files/CDACTION.md)
[CDACTIONBAR](D:/md_files/CDACTIONBAR.md)
[COLOR_VALUE](D:/md_files/COLOR_VALUE.md)
---

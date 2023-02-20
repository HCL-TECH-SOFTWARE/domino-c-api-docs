##### Data Type : Composite Data
##### CDFRAME - Used to specify an HTML FRAME element
---
```
#include <fsods.h>
```
**Description :**

Header
Flags   see fFRxxx
DataFlags	  see fFRNotesxxx
BorderEnable  Frame Border Attribute specified.
NoResize   Specifies the NoReSize attribute to this Frame.
ScrollBarStyle  see xxx_ScrollStyle
MarginWidth  Margin Width of this Frame in pixels.
MarginHeight  Margin Height of this Frame in pixels.
dwReserved  Reserved, must be 0.
FrameNameLength  Length of the frame name string.
Reserved1   Reserved, must be 0.
FrameTargetLength  Length of the default target frame name.
FrameBorderColor  Specifies the Border Color.
wReserved   Reserved, must be 0.

Frame Name String and Target Name string follow the fixed portion of this CD 
Record.  The strings are not null terminated.




**See Also :**
[CDFRAMESETHEADER](/reference/Data/CDFRAMESETHEADER)
[COLOR_VALUE](/reference/Data/COLOR_VALUE)
[fFRNotesxxx](/reference/Symb/fFRNotesxxx)
[fFRxxx](/reference/Symb/fFRxxx)
[xxx_ScrollStyle](/reference/Symb/xxx_ScrollStyle)
---

##### Symbolic Value : Constants
##### BUTTON_xxx - CDBUTTON - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	BUTTON_UNUSED	  -  Button is unused.

	BUTTON_RUNFLAG_SCRIPT	  -  Script is attached to this button.

	BUTTON_RUNFLAG_NOWRAP	  -  Works with width flags BUTTON_RUNFLAG_FIXED, BUTTON_FUNFLAG_MINIMUM, BUTTON_RUNFLAG_CONTENT and BUTTON_RUNFLAG_WIDTHMASK.. If text doesn't "fit" in the specified width, determines if text should be wrapped (and button made taller) or not.

	BUTTON_ODS_MASK	  -  Determines which of the flag bits are written to disk as opposed to just being used while the button "is running" to record the current state of the button (e.g., if the button has been pressed and is currently executing script bits). In other words, it's the AND mask for all the bits that are going to be written to disk.		

	BUTTON_RUNFLAG_RTL	  -  Button uses right-to-left reading order.

	BUTTON_RUNFLAG_FIXED	  -  Button has a fixed width of specified size.

	BUTTON_RUNFLAG_MINIMUM	  -  Button has a fixed width of specified size UNLESS text is too wide to fit in which case it's made wider to accommodate the text.

	BUTTON_RUNFLAG_CONTENT	  -  Button is as wide as is necessary to accommodate the text.

	BUTTON_RUNFLAG_PROPORTIONAL	  -  Button width is a fixed number of characters.

	BUTTON_FOCUS_ON	  -  Button has focus.

	BUTTON_RUNFLAG_WIDTH_MASK	  -  AND mask to see if BUTTON_RUNFLAG_FIXED, BUTTON_RUNFLAG_MINIMUM, BUTTON_RUNFLAG_CONTENT, BUTTON_RUNFLAG_NOWRAP and BUTTON_RUNFLAG_PROPORTIONAL flags are set. If none of these flags are set, the button is "MAXIMUM" size. "Maximum" means the button is as wide as is necessary to accommodate the text up-to the specified maximum width. If the text doesn't fit at the maximum width, it's wrapped onto a second (third, fourth, ...) line and the button is made correspondingly taller. Minimum allowed value is "2.00".

	BUTTON_EDGE_ROUNDED	  -  Button edges are rounded.

	BUTTON_EDGE_SQUARE	  -  Button edges are square.


**Description :**

Possible values for the Flags member of the CDBUTTON structure.


**See Also :**
[CDBUTTON](/domino-c-api-docs/reference/Data/CDBUTTON)
---

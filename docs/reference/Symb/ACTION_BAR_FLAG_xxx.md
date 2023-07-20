##### Symbolic Value : Form
##### ACTION_BAR_FLAG_xxx - Flags for the CDACTIONBAR record
---
```
#include <actods.h>
```

**Symbolic Values :**

	ACTION_BAR_FLAG_NO_SYS_COLOR	  -  Do not use the system color for the action bar.

	ACTION_BAR_FLAG_ALIGN_RIGHT	  -  Right justify buttons

	ACTION_BAR_FLAG_TRANS_BUTTONS	  -  Buttons are transparent

	ACTION_BAR_FLAG_SYS_BUTTONS	  -  Buttons use system color

	ACTION_BAR_FLAG_BTNBCK_IMGRSRC	  -  Image resource used for button background

	ACTION_BAR_FLAG_BARBCK_IMGRSRC	  -  Image resource used for bar background

	ACTION_BAR_FLAG_SET_PADDING	  -  Use the Padding setting instead of default 2 pixels.

	ACTION_BAR_FLAG_USE_APPLET	  -  Use applet in browser.

	ACTION_BAR_FLAG_SET_HEIGHT	  -  Use Height setting instead of default ICON_DEFAULT_HEIGHT

	ACTION_BAR_FLAG_ABSOLUTE_HEIGHT	  -  If ACTION_BAR_FLAG_SET_HEIGHT, use absolute height specified by user.

	ACTION_BAR_FLAG_BACKGROUND_HEIGHT	  -  If ACTION_BAR_FLAG_SET_HEIGHT, use background image's height.

	ACTION_BAR_FLAG_SET_WIDTH	  -  Use Width setting instead of default width.

	ACTION_BAR_FLAG_BACKGROUND_WIDTH	  -  If ACTION_BAR_FLAG_SET_WIDTH, use background image's width.

	ACTION_BAR_FLAG_SHOW_HINKY_ALWAYS	  -  Always show the drop down hinky if a button has a menu no matter what the border style is.


**Description :**

These flags are stored in the dwFlags field of the CDACTIONBAR record.


**See Also :**
[CDACTIONBAR](/domino-c-api-docs/reference/Data/CDACTIONBAR)
---

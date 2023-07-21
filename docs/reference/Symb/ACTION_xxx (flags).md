##### Symbolic Value : Form
##### ACTION_xxx (flags) - CDACTION Flags
---
```
#include <actods.h>
```

**Symbolic Values :**

	ACTION_SHOW_IN_MENU	  -  Display in the "Actions" pull-down menu.

	ACTION_SHOW_IN_BAR	  -  Display in the action button bar.

	ACTION_SHOW_WHEN_PREVIEWING	  -  Show the action when previewing the document.

	ACTION_SHOW_WHEN_READING	  -  Show the action when reading the document.

	ACTION_SHOW_WHEN_EDITING	  -  Show the action when editing the document.

	ACTION_SHOW_ON_OLE_LAUNCH	  -  Show when launching OLE object.

	ACTION_OLE_CLOSE_WHEN_CHOSEN	  -  Close the OLE object when this action is selected.

	ACTION_NO_FORMULA	  -  No "hide when" formula is stored for this action.

	ACTION_SHOW_WHEN_PREVEDITING	  -  Show when editing in the preview window.

	ACTION_OLE_DOC_WINDOW_TO_FRONT	  -  Bring the OLE document window to the front when this action is selected.

	ACTION_HIDE_FROM_NOTES	  -  Do not display in Notes.

	ACTION_HIDE_FROM_WEB	  -  Do not display in Web browsers.

	ACTION_READING_ORDER_RTL	  -  Action reading order from right.

	ACTION_SHARED	  -  Action is shared.

	ACTION_MODIFIED	  -  Action has been modified (not saved on disk).

	ACTION_ALWAYS_SHARED	  -  Flag not saved on disk.

	ACTION_ALIGN_ICON_RIGHT	  -  Right align action button

	ACTION_IMAGE_RESOURCE_ICON	  -  Use graphic image icon.

	ACTION_FRAME_TARGET	  -  Use target frame.

	ACTION_TEXT_ONLY_IN_MENU	  -  Shows only icon in button bar. (Displays text in the Action menu if ACTION_SHOW_IN_MENU flag is set).

	ACTION_BUTTON_TO_RIGHT	  -  Show button on opposite side from action bar direction.

	ACTION_SHOW_IN_POPUPMENU	  -  Show action in pop-up menu.

	ACTION_HIDE_FROM_MOBILE	  -  Hide action from mobile users.

	ACTION_ODS_FLAG_MASK	  -  Bit mask for the CDACTION flag bits.


**Description :**

Possible values for the Flags member of the CDACTION structure.  These values further describe attributes for the action.


**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---

##### Symbolic Value : Hotspot
##### HOTSPOTREC_RUNFLAG_xxx - CDHOTSPOTBEGIN - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	HOTSPOTREC_RUNFLAG_BEGIN	  -  Signals the beginning of a hotspot.

	HOTSPOTREC_RUNFLAG_END	  -  Signals the end of a hotspot.

	HOTSPOTREC_RUNFLAG_BOX	  -  Display a box around the popup.

	HOTSPOTREC_RUNFLAG_NOBORDER	  -  Do not display a box around the popup.

	HOTSPOTREC_RUNFLAG_FORMULA	  -  The text associated with a popup is generated using a formula.

	HOTSPOTREC_RUNFLAG_MOVIE	  -  File is a QuickTime movie.

	HOTSPOTREC_RUNFLAG_IGNORE	  -  Run is for backward compatibility (i.e. ignore the run).

	HOTSPOTREC_RUNFLAG_ACTION	  -  Hot region executes a canned action.

	HOTSPOTREC_RUNFLAG_SCRIPT	  -  Hot region executes a script.

	HOTSPOTREC_RUNFLAG_INOTES	  -  Hotspot is a URL and will bring up the appropriate web page.

	HOTSPOTREC_RUNFLAG_ISMAP	  -  Contains hot regions that map to different URLs.

	HOTSPOTREC_RUNFLAG_INOTES_AUTO	  -  A hotspot generated automatically during document load when a document has a text stream that is recognizable as a URL.

	HOTSPOTREC_RUNFLAG_ISMAP_INPUT	  -  Not currently used

	HOTSPOTREC_RUNFLAG_SIGNED	  -  Hotspot contains signature.

	HOTSPOTREC_RUNFLAG_ANCHOR	  -  Not currently used

	HOTSPOTREC_RUNFLAG_COMPUTED	  -  Hotspot is computed text.

	HOTSPOTREC_RUNFLAG_TEMPLATE	  -  Used in conjunction with embedded navigator panes.

	HOTSPOTREC_RUNFLAG_HIGHLIGHT	  -  Hotspot is highlighted.

	HOTSPOTREC_RUNFLAG_EXTACTION	  -  Hot Region executes an extended action.

	HOTSPOTREC_RUNFLAG_NAMEDELEM	  -  Hot link to a named element.

	HOTSPOTREC_RUNFLAG_WEBJAVASCRIPT	  -  Allow Notes/Domino 6 dual action type buttons (e.g. client LotusScript, web JS.)

	HOTSPOTREC_RUNFLAG_ODSMASK	  -  Mask for flag bits actually stored on disk. In addition, the flag bits HOTSPOTREC_RUNFLAG_BEGIN and HOTSPOTREC_RUNFLAG_END are also stored on disk.


**Description :**

These flags are used to define some of the attributes of a popup in a rich text field.


**See Also :**
[CDHOTSPOTBEGIN](/domino-c-api-docs/reference/Data/CDHOTSPOTBEGIN)
---

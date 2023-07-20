##### Symbolic Value : Hotspot
##### HOTSPOTREC_TYPE_xxx - CDHOTSPOTBEGIN - Type
---
```
#include <editods.h>
```

**Symbolic Values :**

	HOTSPOTREC_TYPE_POPUP	  -  The hotspot is a popup

	HOTSPOTREC_TYPE_HOTREGION	  -  The hotspot is a button whose presentation is an arbitrary region of the rich text field. This region is bounded by the CDHOTSPOTBEGIN and CDHOTSPOTEND records.

	HOTSPOTREC_TYPE_BUTTON	  -  The hotspot is a button.

	HOTSPOTREC_TYPE_FILE	  -  The hotspot is a file attachment.

	HOTSPOTREC_TYPE_SECTION	  -  The hotspot is a Notes Release 3 section field hotspot.

	HOTSPOTREC_TYPE_ANY	  -  Unused.

	HOTSPOTREC_TYPE_HOTLINK	  -  The hotspot is a document, database, or view link hotspot. The presentation of this hotspot is an arbitrary region of the rich text field. This region is bounded by the CDHOTSPOTBEGIN and CDHOTSPOTEND records.

	HOTSPOTREC_TYPE_BUNDLE	  -  The hotspot is a standard collapsible section which is not access controlled.

	HOTSPOTREC_TYPE_V4_SECTION	  -  The hotspot is an access controlled collapsible section.

	HOTSPOTREC_TYPE_SUBFORM	  -  The hotspot is a subform.

	HOTSPOTREC_TYPE_ACTIVEOBJECT	  -  The hotspot is an active object.

	HOTSPOTREC_TYPE_OLERICHTEXT	  -  The hotspot is an OLE rich text object.

	HOTSPOTREC_TYPE_EMBEDDEDVIEW	  -  The hotspot is an embedded view.

	HOTSPOTREC_TYPE_EMBEDDEDFPANE	  -  The hotspot is an embedded folder pane.

	HOTSPOTREC_TYPE_EMBEDDEDNAV	  -  The hotspot is an embedded navigator.

	HOTSPOTREC_TYPE_MOUSEOVER	  -  The hotspot is mouse over text popup.

	HOTSPOTREC_TYPE_FILEUPLOAD	  -  The hotspot is a file upload placeholder.

	HOTSPOTREC_TYPE_EMBEDDEDOUTLINE	  -  The hotspot is an embedded outline.

	HOTSPOTREC_TYPE_EMBEDDEDCTL	  -  The hotspot is an embedded control window.

	HOTSPOTREC_TYPE_EMBEDDEDCALENDARCTL	  -  The hotspot is an embedded calendar control (date picker).

	HOTSPOTREC_TYPE_EMBEDDEDSCHEDCTL	  -  The hotspot is an embedded scheduling control.

	HOTSPOTREC_TYPE_RCLINK	  -  The hotspot is a resource link.

	HOTSPOTREC_TYPE_EMBEDDEDEDITCTL	  -  The hotspot is an embedded editor control.

	HOTSPOTREC_TYPE_CONTACTLISTCTL	  -  Embeddable buddy list.


**Description :**

These flags are used to define what type of hotspot is being defined by a CDHOTSPOTBEGIN data structure.


**See Also :**
[CDHOTSPOTBEGIN](/domino-c-api-docs/reference/Data/CDHOTSPOTBEGIN)
---

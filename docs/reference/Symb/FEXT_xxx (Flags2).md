##### Symbolic Value : Rich Text
##### FEXT_xxx (Flags2) - CDEXTFIELD - Flags2
---
```
#include <editods.h>
```

**Symbolic Values :**

	FEXT_KW_CHOICE_RECALC	  -  TRUE to recalc the value choices.

	FEXT_HTML_IN_FIELDDEF	  -  An HTML Attribute formula follows the CDEXTFIELD record.

	FEXT_HIDEDELIMITERS	  -  Set if hiding delimeters.

	FEXT_KW_RTL_READING_ORDER	  -  Right to Left Reading Order.

	FEXT_ALLOWTABBINGOUT	  -  Set if tab will exit field.

	FEXT_PASSWORD	  -  Set if field is a password field.

	FEXT_USEAPPLETINBROWSER	  -  Set if applet should be used for a browser.

	FEXT_CONTROL	  -  Set if field is a control.

	FEXT_LITERALIZE	  -  Set if this is a formula field which should have item substitution based on items on the form. This is the counterpart to a computed formula which is a formula programmatically generated through @formulas.

	FEXT_CONTROLDYNAMIC	  -  TRUE if field is a dynamic control.

	FEXT_RUNEXITINGONCHANGE	  -  TRUE if should run exiting event when value changes. Currently only implemented for native date/time.

	FEXT_TIMEZONE	  -  TRUE if this is a time zone field.

	FEXT_PROPORTIONALHEIGHT	  -  TRUE if field has proportional height.

	FEXT_PROPORTIONALWIDTH	  -  TRUE if field has proportional width.

	FEXT_SHOWIMSTATUS	  -  TRUE if a names type field displays im online status.


**Description :**

These options are stored in the Flags2 field of the CDEXTFIELD record.


**See Also :**
[CDEXTFIELD](/domino-c-api-docs/reference/Data/CDEXTFIELD)
---

##### Symbolic Value : Composite Data
##### EMBEDDEDCTL_xxx - CDEMBEDDEDCTL - CtlType
---
```
#include <editods.h>
```

**Symbolic Values :**

	EMBEDDEDCTL_EDIT	  -  Control type is edit.

	EMBEDDEDCTL_COMBO	  -  Control type is a combobox.

	EMBEDDEDCTL_LIST	  -  Control type is a listbox.

	EMBEDDEDCTL_TIME	  -  Control type describes calendar/scheduling.

	EMBEDDEDCTL_KEYGEN	  -  Control type also a combobox.

	EMBEDDEDCTL_FILE	  -  Control type also edit.

	EMBEDDEDCTL_TIMEZONE	  -  Control type is timezone.

	EMBEDDEDCTL_COLOR	  -  Control type is a color picker.


**Description :**

Implemented as an enumerated type:
<ul><br>
<br>
<tt><font size="2">enum {</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;EMBEDDEDCTL_EDIT = 0,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;EMBEDDEDCTL_COMBO = 1,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;EMBEDDEDCTL_LIST = 2,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;EMBEDDEDCTL_TIME = 3,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;EMBEDDEDCTL_KEYGEN = 4,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;EMBEDDEDCTL_FILE = 5,</font></tt><br>
<tt>&nbsp; &nbsp;EMBEDDEDCTL_TIMEZONE = 6,</tt></ul>
<tt>	EMBEDDEDCTL_COLOR = 7</tt>
<ul><tt><font size="2">};</font></tt></ul>



**See Also :**
[CDEMBEDDEDCTL](/domino-c-api-docs/reference/Data/CDEMBEDDEDCTL)
---

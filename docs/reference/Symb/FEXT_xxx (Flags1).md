##### Symbolic Value : Rich Text
##### FEXT_xxx (Flags1) - CDEXTFIELD - Flags1
---
```
#include <editods.h>
```

**Symbolic Values :**

	FEXT_LOOKUP_EACHCHAR	  -  Lookup name as each character is typed.

	FEXT_KWSELRECALC	  -  Recalc on new keyword selection.

	FEXT_KWHINKYMINKY	  -  Suppress showing field hinky minky.

	FEXT_AFTERVALIDATION	  -  Recalc after validation.

	FEXT_ACCEPT_CARET	  -  The first field with this bit set will accept the caret.

	FEXT_KEYWORD_COLS_SHIFT	  -  Number of bits to shift the Keyword Columns sub-field.

	FEXT_KEYWORD_COLS_MASK	  -  Bitmask used to read and write the Keyword Columns sub-field.

	FEXT_KEYWORD_FRAME_3D	  -  Display 3D background for keyword choices.

	FEXT_KEYWORD_FRAME_STANDARD	  -  Display simple frame around keyword choices.

	FEXT_KEYWORD_FRAME_NONE	  -  Display no background for keyword choices.

	FEXT_KEYWORD_FRAME_MASK	  -  Bitmask used to read and write the Keyword Frame Type sub-field.

	FEXT_KEYWORD_FRAME_SHIFT	  -  Number of bits to shift the Keyword Frame Type sub-field.

	FEXT_KEYWORDS_UI_COMBO	  -  Display keywords in a combo box.

	FEXT_KEYWORDS_UI_LIST	  -  Display keywords in a list box.


**Description :**

Flags for CDEXTFIELD Flags1.  Note that the low word in Flags1 is not used.<br>
<br>
The Keyword Columns sub-field specifies the number of columns to be used when displaying the options in a field of type Keyword as either checkboxes or radio buttons.  The number of columns ranges from 1 through 8;  the actual field value stored is (number of columns) - 1.<br>
<br>
The Frame Type subfield specifies the type of background when checkbox or radio button keyword fields are displayed.  &quot;None&quot; means no special background is displayed.  &quot;Standard&quot; draws an outline around the options.  &quot;3D&quot; draws a background as a box with 3-dimensional depth cues.


**See Also :**
[CDEXTFIELD](/domino-c-api-docs/reference/Data/CDEXTFIELD)
---

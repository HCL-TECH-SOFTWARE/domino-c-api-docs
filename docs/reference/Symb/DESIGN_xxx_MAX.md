##### Symbolic Value : Limits
##### DESIGN_xxx_MAX - Maximum lengths of various design note elements.
---
```
#include <names.h>
```

**Symbolic Values :**

	DESIGN_LEVEL_MAX	  -  Maximum length per level of the name of a design element. The names of some design elements can cascade one level (and therefore be longer), while the names of other design elements cannot cascade.

	DESIGN_NAME_MAX	  -  The maximum length for the name of a design note. Will always be the largest of DESIGN_FORM_MAX, DESIGN_VIEW_MAX, and DESIGN_MACRO_MAX.

	DESIGN_FORM_MAX	  -  The maximum length for the name of a form note. Can cascade one level.

	DESIGN_VIEW_MAX	  -  The maximum length for the name of a view note. Can cascade one level.

	DESIGN_MACRO_MAX	  -  The maximum length for the name of a macro note. Can cascade one level.

	DESIGN_FIELD_MAX	  -  The maximum length for the name of a field. Cannot cascade.

	DESIGN_COMMENT_MAX	  -  The maximum length of a design note's comment element.

	DESIGN_ALL_NAMES_MAX	  -  The maximum cumulative length of all names of a design note, including synonyms.

	DESIGN_FOLDER_MAX	  -  The maximum length for the name of a folder note. Can cascade one level.

	DESIGN_FOLDER_MAX_NAME	  -  Maximum length per level of the name of a folder.

	DESIGN_FLAGS_MAX	  -  The maximum length of the DESIGN_FLAGS ($Flags) item in a design note.


**Description :**

Maximum lengths of various design note elements.


**See Also :**
---

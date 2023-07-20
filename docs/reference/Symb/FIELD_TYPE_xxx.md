##### Symbolic Value : Add-In DLL
##### FIELD_TYPE_xxx - Editor field types.
---
```
#include <editdflt.h>
```

**Symbolic Values :**

	FIELD_TYPE_ERROR	  -  Field type cannot be determined.

	FIELD_TYPE_NUMBER	  -  Number field.

	FIELD_TYPE_TIME	  -  Time field.

	FIELD_TYPE_RICH_TEXT	  -  Rich text field.

	FIELD_TYPE_AUTHORS	  -  Authors field.

	FIELD_TYPE_READERS	  -  Readers field.

	FIELD_TYPE_NAMES	  -  Names field.

	FIELD_TYPE_KEYWORDS	  -  Keyword field.

	FIELD_TYPE_TEXT	  -  Plain text field.

	FIELD_TYPE_SECTION	  -  Section field.

	FIELD_TYPE_PASSWORD	  -  Password field.

	FIELD_TYPE_FORMULA	  -  Formula field.

	FIELD_TYPE_TIMEZONE	  -  Time zone field

	FIELD_TYPE_COLORCTL	  -  Color control field


**Description :**

This information is passed to the NAMM_COMMAND message processing routine in an Add-In DLL via the CaretFieldType member of the EDITIXDATA structure.  It identifies the field type of the field containing the cursor when the Add-In's menu item was chosen.


**See Also :**
[EDITIXDATA](/domino-c-api-docs/reference/Data/EDITIXDATA)
---

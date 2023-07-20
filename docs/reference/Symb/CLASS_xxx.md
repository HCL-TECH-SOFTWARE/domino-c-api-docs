##### Symbolic Value : Field
##### CLASS_xxx - Item Class definitions.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	CLASS_NOCOMPUTE	  -  Non-computable data types. See nsfdata.h for a full list of the data types that are in this class. These data types include:
 TYPE_INVALID_OR_UNKNOWN
 TYPE_COMPOSITE
TYPE_COLLATION
TYPE_OBJECT
TYPE_NOTEREF_LIST
TYPE_VIEW_FORMAT
TYPE_ICON 
TYPE_NOTELINK_LIST
TYPE_SIGNATURE
TYPE_SEAL 
TYPE_SEALDATA
TYPE_SEAL_LIST
TYPE_HIGHLIGHTS
TYPE_WORKSHEET_DATA
TYPE_USERDATA
TYPE_QUERY
TYPE_ACTION
TYPE_ASSISTANT_INFO
TYPE_VIEWMAP_DATASET
TYPE_VIEWMAP_LAYOUT
 TYPE_LSOBJECT
 TYPE_HTML
TYPE_SCHED_LIST
TYPE_CALENDAR_FORMAT

	CLASS_ERROR	  -  Data type is TYPE_ERROR

	CLASS_UNAVAILABLE	  -  Data type is TYPE_UNAVAILABLE

	CLASS_NUMBER	  -  Data type is TYPE_NUMBER or TYPE_NUMBER_RANGE

	CLASS_TIME	  -  Data type is TYPE_TIME or TYPE_TIME_RANGE

	CLASS_TEXT	  -  Data type is TYPE_TEXT or TYPE_TEXT_LIST

	CLASS_FORMULA	  -  Data type is TYPE_FORMULA

	CLASS_USERID	  -  Data type is TYPE_USERID

	CLASS_MASK	  -  Masks out the lower byte of an item's data type to reveal the item's class


**Description :**

Classes are defined to be the &quot;generic&quot; classes of data type that the internal formula computation mechanism recognizes when doing recalcs.


**See Also :**
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
---

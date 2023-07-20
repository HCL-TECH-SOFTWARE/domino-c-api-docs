##### Symbolic Value : Constants
##### CDRESOURCE_FLAGS_xxx - Flags defined in a CDRESOURCE.
---
```
#include <rsrcods.h>
```

**Symbolic Values :**

	CDRESOURCE_FLAGS_FORMULA	  -  The type's data is a formula valid for CDRESOURCE_TYPE_URL and CDRESOURCE_TYPE_NAMEDELEMENT.

	CDRESOURCE_FLAGS_NOTELINKINLINE	  -  The notelink variable length data contains the notelink itself - not an index into a $Links items.

	CDRESOURCE_FLAGS_ABSOLUTE	  -  If specified, the link is to an absolute database or thing. Used to make a hard link to a specific DB.

	CDRESOURCE_FLAGS_USEHINTFIRST	  -  If specified, the server and file hint are filled in and should be attempted before trying other copies.

	CDRESOURCE_FLAGS_CANNEDIMAGE	  -  The type's data is a canned image file (data/domino/icons/[*].gif) valid for CDRESOURCE_TYPE_URL && CDRESOURCE_CLASS_IMAGE only.

	CDRESOURCE_FLAGS_PRIVATE_DATABASE	  -  The object is private in its database.
NOTE: CDRESOURCE_FLAGS_PRIVATE_DATABASE and CDRESOURCE_FLAGS_PRIVATE_DESKTOP are mutually exclusive.

	CDRESOURCE_FLAGS_PRIVATE_DESKTOP	  -  The object is private in the desktop database.
NOTE: CDRESOURCE_FLAGS_PRIVATE_DATABASE and CDRESOURCE_FLAGS_PRIVATE_DESKTOP are mutually exclusive.

	CDRESOURCE_FLAGS_REPLICA_WILDCARD	  -  The replica in the CD resource

	CDRESOURCE_FLAGS_SIMPLE	  -  Used with class view and folder to mean "Simple View"

	CDRESOURCE_FLAGS_DESIGN_MODE	  -  Open this up in design mode.

	CDRESOURCE_FLAGS_RESERVED1	  -  Reserved meaning for each resource link class.

	CDRESOURCE_FLAGS_RESERVED2	  -  Reserved meaning for each resource link class.

	CDRESOURCE_FLAGS_RESERVED3	  -  Reserved meaning for each resource link class.

	CDRESOURCE_FLAGS_RESERVED4	  -  Reserved meaning for each resource link class.


**Description :**




**See Also :**
[CDRESOURCE](/domino-c-api-docs/reference/Data/CDRESOURCE)
---

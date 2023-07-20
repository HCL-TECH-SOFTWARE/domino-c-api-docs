##### Symbolic Value : RFC822
##### RFC822_xxx - RFC822ITEMDESC - dwFlags
---
```
#include <mimeods.h>
```

**Symbolic Values :**

	RFC822_ITEM_FORMAT_MASK	  -  Format mask.

	RFC822_ITEM_FORMAT_ADDR	  -  822-header is an address.

	RFC822_ITEM_FORMAT_DATE	  -  822-header is a date.

	RFC822_ITEM_FORMAT_TEXT	  -  822-header is text.

	RFC822_ITEM_STORAGE_STRICT	  -  STRICT storage format.

	RFC822_ITEM_TEXT_LIST	  -  Text item is TEXT_LIST.

	RFC822_TEXT_UNUSED	  -  First available flag.


**Description :**

Possible TYPE_822_TEXT values for the dwFlags member of the RFC822ITEMDESC structure.  The first three bits are reserved for the RFC822_ITEM_FORMAT_MASK format mask,  the formats defined include: RFC822_ITEM_FORMAT_ADDR, RFC822_ITEM_FORMAT_DATE and RFC822_ITEM_FORMAT_TEXT.  The remaining bits are flags which include: RFC822_ITEM_STORAGE_STRICT, RFC822_ITEM_TEXT_LIST and RFC822_TEXT_UNUSED.


**See Also :**
[RFC822ITEMDESC](/domino-c-api-docs/reference/Data/RFC822ITEMDESC)
---

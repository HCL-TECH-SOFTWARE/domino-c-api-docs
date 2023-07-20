##### Symbolic Value : MIME
##### MIME_HEADER_FORMAT_xxx - information on how to map an Internet header to a Notes/Domino item.

---
```
#include <mime.h>
```

**Symbolic Values :**

	MIME_HEADER_FORMAT_ADDRESS	  -  header is an RFC822 address header.

	MIME_HEADER_FORMAT_DAT	  -  header is an RFC822 date/time header.

	MIME_HEADER_FORMAT_NOTES_ITEM	  -  header is an X-Notes-Item header used to preserve Notes/Domino items across SMTP transfers.

	MIME_HEADER_FORMAT_TEXT	  -  header is text; map to TYPE_TEXT.

	MIME_HEADER_FORMAT_TEXT_LIST	  -  header is a list; map to TYPE_TEXT_LIST.


**Description :**

information on how to map an Internet header to a Notes/Domino item.


**See Also :**
---

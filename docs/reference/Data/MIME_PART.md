##### Data Type : MIME
##### MIME_PART - Mime parts record.
---
```
#include <mimeods.h>
```

**Definition :**
```
typedef struct {
 WORD wVersion;      /* MIME_PART Version */
 DWORD dwFlags;
 BYTE cPartType;     /* Type of MIME_PART body */
 BYTE cSpare;
 WORD wByteCount;    /* Bytes of variable length part data
     NOT including data in DB object*/

	WORD wBoundaryLen;  /* Length of the boundary string */
 WORD wHeadersLen;   /* Length of the headers */
 WORD wSpare;
 DWORD dwSpare;

	/* Followed by the actual part data */
} MIME_PART;
```

**Description :**

The MIME_PART structure stores the mime parts for items of TYPE_MIME_PART.  The fields in this structure are:
<ul><br>
<br>
wVersion		MIME_PART Version.<br>
dwFlags		Flags - see MIME_PART_xxx.<br>
cPartType		Type of MIME_PART body - see MIMEPARTTYPE.<br>
cSpare		Spare BYTE.<br>
wByteCount	                Bytes of variable length part data NOT including data in DB object.<br>
wBoundaryLen	Length of the boundary string.<br>
wHeadersLen	Length of the headers.<br>
wSpare		Spare WORD.<br>
dwSpare		Spare DWORD.</ul>



**See Also :**
[MIME_PART_VERSION](/domino-c-api-docs/reference/Symb/MIME_PART_VERSION)
[MIME_PART_xxx](/domino-c-api-docs/reference/Symb/MIME_PART_xxx)
---

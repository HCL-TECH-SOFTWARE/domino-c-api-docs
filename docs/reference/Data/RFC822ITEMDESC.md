##### Data Type : RFC822
##### RFC822ITEMDESC - TYPE_822_TEXT item RFC822 header information.
---
```
#include <mimeods.h>
```

**Definition :**

typedef struct {
 WORD wVersion;  /* ODSSizeof this structure for versioning */
 DWORD dwFlags;  /* TYPE_822_TEXT flags.  The first three bits
        are reserved for the format mask,the remaining bits are flags */
 WORD wNotesNativeLen; /* Length of the Notes version which is either
        a LMBCS string or a TIMEDATE. */
 WORD w822NameLen; /* Length of the original 822 header name */
 WORD w822DelimLen; /* Length of the original 822 header delimiter */
	WORD w822BodyLen; /* Length of the original 822 header body in
        it's native charset and encoding (RFC2047) */
} RFC822ITEMDESC;

**Description :**

The RFC822ITEMDESC structure stores the message header for items of TYPE_RFC822_TEXT.  The fields in this structure are:
<ul><br>
<br>
wVersion		ODSSizeof this structure for versioning.<br>
dwFlags		TYPE_822_TEXT flags.  The first three bits are reserved for the format mask, the remaining bits are flags (See RFC822_xxx). <br>
wNotesNativeLen	Length of the Notes version which is either a LMBCS string or a TIMEDATE.<br>
w822NameLen	Length of the original 822 header name.<br>
w822DelimLen	Length of the original 822 header delimiter.<br>
w822BodyLen	Length of the original 822 header body in it's native charset and encoding (RFC2047).</ul>



**See Also :**
[RFC822_xxx](/domino-c-api-docs/reference/Symb/RFC822_xxx)
---

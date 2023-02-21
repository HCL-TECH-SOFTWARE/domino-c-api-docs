##### Data Type : RFC822
##### RFC822ITEMDESC - TYPE_822_TEXT item RFC822 header information.
---
```
#include <mimeods.h>
```
**Description :**

The RFC822ITEMDESC structure stores the message header for items of 
TYPE_RFC822_TEXT.  The fields in this structure are:

wVersion  ODSSizeof this structure for versioning.
dwFlags  TYPE_822_TEXT flags.  The first three bits are reserved for the format 
mask, the remaining bits are flags (See RFC822_xxx). 
wNotesNativeLen Length of the Notes version which is either a LMBCS string or a 
TIMEDATE.
w822NameLen Length of the original 822 header name.
w822DelimLen Length of the original 822 header delimiter.
w822BodyLen Length of the original 822 header body in it's native charset and 
encoding (RFC2047).


**See Also :**
[RFC822_xxx](/domino-c-api-docs/reference/Symb/RFC822_xxx)
---

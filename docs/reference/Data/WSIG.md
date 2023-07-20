##### Data Type : Rich Text
##### WSIG - CD record header of type, W(ORD).
---
```
#include <ods.h>
```

**Definition :**
```
typedef struct {
   WORD Signature; /* ORed with WORDRECORDLENGTH */
   WORD Length;    /* (length is inclusive with this struct) */
} WSIG;
```

**Description :**

Every CD record begins with a header.  There are three types of headers, BSIG, WSIG, and LSIG.  The first byte of the header is a signature which identifies the type of the header and the type of the CD record that follows.


**See Also :**
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---

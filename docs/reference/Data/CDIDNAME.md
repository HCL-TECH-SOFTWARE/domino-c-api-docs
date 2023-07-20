##### Data Type : Composite Data
##### CDIDNAME - Defines an HTML ID.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;    /* Signature and length of this record */
   WORD Length;    /* Length of ID */
   WORD wClassLen; /* Length of CLASS */
   WORD wStyleLen; /* Length of STYLE */
   WORD wTitleLen; /* Length of TITLE */
   WORD wExtraLen; /* Length of extra attribute/value pairs */
   WORD wNameLen;  /* Length of NAME */
   BYTE  reserved[10];
/* id follows */
/* class follows */
/* style follows */
/* title follows */
/* extra attrib/value pairs of object follows */
/* name follows */
} CDIDNAME;
```

**Description :**

This CD record describes the HTML field properties, ID, Class, Style, Title, Other and Name associated for any given field defined within a Domino Form.


**See Also :**
---

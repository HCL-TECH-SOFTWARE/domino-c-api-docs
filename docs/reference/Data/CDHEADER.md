##### Data Type : Composite Data
##### CDHEADER - Header/Footer record
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;   /* Tag and length */
   BYTE FontPitchAndFamily; /* Font pitch and family */
   char FontName[MAXFACESIZE]; /* Font name */
   FONTID Font;    /* Font ID */
   WORD HeadLength;   /* total header string length */
 /* ... now comes the string */
} CDHEADER;
```

**Description :**

Contains the header or footer used in a document.<br>
<br>
        Header                                Tag identifying this as a header or footer record<br>
        FontPitchAndFamily        Pitch and font family of font used to display the data<br>
        FontName                           Name of font to use<br>
        Font                                       ID of font to use<br>
        HeadLength                       Total string length of header or footer<br>
<br>
This header structure is followed by the string for the header or footer.


**See Also :**
[CDDOCUMENT](/domino-c-api-docs/reference/Data/CDDOCUMENT)
---

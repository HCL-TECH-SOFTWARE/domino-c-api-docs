##### Data Type : Composite Data
##### CDCAPTION - Text to display with an object (e.g., a graphic)
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG        Header;       /* Tag and length */
   WORD        wLength;      /* Text length */
   BYTE        Position;     /* One of the position flags above */
   FONTID      FontID;       /* Font to use for the text */
   COLOR_VALUE FontColor;    /* RGB font color info */
   BYTE        Reserved[11]; /* Reserved for future use */
/* The 8-bit text string follows... */
} CDCAPTION;

**Description :**

This CD record defines the properties of a caption for a grapic record.  The actual caption text follows the fixed part of the record.
<ul><br>
<br>
WSIG		Header		Signature and length<br>
WORD		wLength	Caption text length<br>
BYTE		Position	see CAPTION_POSITION_xxx	<br>
FONTID		FontID		Font to use for the text<br>
COLOR_VALUE 	FontColor	RGB font color information<br>
BYTE		Reserved[11]</ul>



**See Also :**
[CAPTION_POSITION_xxx](/domino-c-api-docs/reference/Symb/CAPTION_POSITION_xxx)
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
---

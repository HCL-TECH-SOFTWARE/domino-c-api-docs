##### Data Type : Composite Data
##### CDCAPTION - Text to display with an object (e.g., a graphic)
---
```
#include <editods.h>
```
**Description :**

This CD record defines the properties of a caption for a grapic record.  The 
actual caption text follows the fixed part of the record.

WSIG  Header  Signature and length
WORD  wLength Caption text length
BYTE  Position see CAPTION_POSITION_xxx 
FONTID  FontID  Font to use for the text
COLOR_VALUE  FontColor RGB font color information
BYTE  Reserved[11]

**See Also :**
[CAPTION_POSITION_xxx](/domino-c-api-docs/reference/Symb/CAPTION_POSITION_xxx)
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
---

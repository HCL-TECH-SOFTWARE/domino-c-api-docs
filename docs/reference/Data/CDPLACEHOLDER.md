##### Data Type : Composite Data
##### CDPLACEHOLDER - Additional information for an embedded element.
---
```
#include <editods.h>
```
**Description :**

A CDPLACEHOLDER record stores additional information about various embedded 
type CD records, such as CDEMBEDDEDCTL, CDEMBEDDEDOUTLINE and other embedded CD 
record types defined in HOTSPOTREC_TYPE_xxx.

WSIG   Header   Signature and length
WORD   Type   see HOTSPOTREC_TYPE_xxx (Note: only the 
HOTSPOTREC_TYPE_EMBEDDEDxxx)
DWORD  Flags   see PLACEHOLDER_FLAG_xxx
WORD   Width   Width of embedded element
WORD   Height   Height of embedded element
FONTID  FontID   Font information of embedded element
WORD   Characters
WORD   SpaceBetween  Space between
WORD   TextAlignment  see PLACEHOLDER_ALIGN_xxx
WORD   SpaceWord
FONTID  SubFontID[2]  Sub Font information of embedded element
WORD   DataLength  Data Length
COLOR_VALUE BackgroundColor Background Color
COLOR_VALUE ColorRGB  Color 
WORD   SpareWord
DWORD  Spare[3]



**See Also :**
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[HOTSPOTREC_TYPE_xxx](/domino-c-api-docs/reference/Symb/HOTSPOTREC_TYPE_xxx)
[PLACEHOLDER_ALIGN_xxx](/domino-c-api-docs/reference/Symb/PLACEHOLDER_ALIGN_xxx)
[PLACEHOLDER_FLAG_xxx](/domino-c-api-docs/reference/Symb/PLACEHOLDER_FLAG_xxx)
---

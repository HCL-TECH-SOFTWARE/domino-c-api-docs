##### Data Type : Rich Text
##### FONTID - Controls how text is displayed in Rich Text.
---
```
#include <global.h>
```
**Description :**

Identifier used to select a particular font to be used when displaying a 
portion of a Rich Text item.  Each portion or 'text run' you construct may 
reference any one of the commonly available typefaces used by the Notes 
workstation application.  If you are dealing with existing Rich Text, then the 
typeface was probably established by the form designer, another API 
application, or the latest document author.  

The particular font value is contained in one byte of the FONTID portion of the 
header of each CDTEXT record.  Other bytes in the FONTID control the point 
size, display attributes, and color to be used.  For a description of these 
fields, see the entry FONTIDFIELDS.  The Notes workstation application uses 
this information to present each text run in each Rich Text field of a 
document.  There are several convenient macros in FONTID.H that allow you to 
modify the individual bits of a FONTID, thereby controlling how text will be 
displayed.

**See Also :**
[CDTEXT](/domino-c-api-docs/reference/Data/CDTEXT)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[xxx_FONT_ID](/domino-c-api-docs/reference/Symb/xxx_FONT_ID)
---

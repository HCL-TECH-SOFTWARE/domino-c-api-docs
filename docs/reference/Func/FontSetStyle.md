##### Function : Font
##### FontSetStyle - Sets the FONTID's Attrib byte as specified in the styleid argument.
---
```
#include <fontid.h>
FONTID FontSetStyle(

	FONTID  fontid,
	DWORD  styleid);
```
**Description :**

Sets all of the font's style characteristics (ITALIC, BOLD, etc) as specified 
in the styleid argument by setting the FONTID's Attrib byte appropriately. The 
values the Attrib byte can take are defined by the symbolic definition ISxxx., 
so the styleid argument should consist of one or more of those values bitwise 
OR-ed together.  Implemented as a macro:

#define FontSetStyle(fontid,styleid) (((DWORD)(fontid) & 
~BYTEMASK(FONT_STYLE_SHIFT)) | ((DWORD)(styleid)<<FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to set the Attrib byte.

styleid  -  ID of the style to set.

Output :
(routine)  -  The specified FONTID with the Attrib byte set appropriately.


fontid  -  The specified FONTID with the style attributes appropriately set.


**Sample Usage :**
```
pCDText->FontID = FontSetStyle(pCDText->FontID, ISBOLD | ISITALIC | 
ISUNDERLINE);
```
**See Also :**
[FontGetStyle](/domino-c-api-docs/reference/Func/FontGetStyle)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[ISxxx](/domino-c-api-docs/reference/Symb/ISxxx)
---

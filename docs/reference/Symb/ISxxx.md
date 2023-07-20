##### Symbolic Value : Miscellaneous
##### ISxxx - Bit field values for STYLE member of FONTIDFIELDS.
---
```
#include <fontid.h>
```

**Symbolic Values :**

	ISBOLD	  -  Text in the CDTEXT item will be in boldface.

	ISITALIC	  -  Text in the CDTEXT item will be in italics.

	ISUNDERLINE	  -  Text in the CDTEXT item will be underlined.

	ISSTRIKEOUT	  -  Text in the CDTEXT item will be Struck out.

	ISSUPER	  -  Text in the CDTEXT item will be superscripted

	ISSUB	  -  Text in the CDTEXT item will be subscripted.

	ISEFFECT	  -  Text in the following CDTEXT item will be of a special effect style: shadowed, embossed, or extruded.

	ISSHADOW	  -  Text in the following CDTEXT item will be shadowed.

	ISEMBOSS	  -  Text in the following CDTEXT item will be embossed. Embossed text is text that appears to be sticking out of the page.

	ISEXTRUDE	  -  Text in the following CDTEXT item will be extruded. Extruded text is text that appears to be pushed into the page.


**Description :**

These defines are used to specify font style attributes (bold, italic, etc.) in the FONTID field in a CDTEXT item.  These values may be combined by bitwise OR-ing them together.


**See Also :**
[CDTEXT](/domino-c-api-docs/reference/Data/CDTEXT)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FONT_FACE_xxx](/domino-c-api-docs/reference/Symb/FONT_FACE_xxx)
[NOTES_COLOR_xxx](/domino-c-api-docs/reference/Symb/NOTES_COLOR_xxx)
---

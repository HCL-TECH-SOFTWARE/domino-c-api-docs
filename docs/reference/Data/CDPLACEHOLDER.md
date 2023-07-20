##### Data Type : Composite Data
##### CDPLACEHOLDER - Additional information for an embedded element.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct
	{
	WSIG   Header; /* Signature and length of this record. */
	WORD  Type;
	DWORD  Flags; 
	WORD   Width;
	WORD   Height;
	FONTID   FontID;
	WORD  Characters;
	WORD  SpaceBetween;
	WORD  TextAlignment;
	WORD  SpaceWord;
	FONTID SubFontID[2];
	WORD   DataLength;
	COLOR_VALUE BackgroundColor;
	COLOR_VALUE ColorRGB;
	WORD  SpareWord;
	DWORD  Spare[3];
	} CDPLACEHOLDER;
```

**Description :**

A CDPLACEHOLDER record stores additional information about various embedded type CD records, such as CDEMBEDDEDCTL, CDEMBEDDEDOUTLINE and other embedded CD record types defined in HOTSPOTREC_TYPE_xxx.<br>
<br>
WSIG			Header			Signature and length<br>
WORD			Type			see HOTSPOTREC_TYPE_xxx	(Note: only the HOTSPOTREC_TYPE_EMBEDDEDxxx)<br>
DWORD		Flags			see PLACEHOLDER_FLAG_xxx<br>
WORD			Width			Width of embedded element<br>
WORD			Height			Height of embedded element<br>
FONTID		FontID			Font information of embedded element<br>
WORD			Characters<br>
WORD			SpaceBetween		Space between<br>
WORD			TextAlignment		see PLACEHOLDER_ALIGN_xxx<br>
WORD			SpaceWord<br>
FONTID		SubFontID[2]		Sub Font information of embedded element<br>
WORD			DataLength		Data Length<br>
COLOR_VALUE	BackgroundColor	Background Color<br>
COLOR_VALUE	ColorRGB		Color	<br>
WORD			SpareWord<br>
DWORD		Spare[3]<br>



**See Also :**
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[HOTSPOTREC_TYPE_xxx](/domino-c-api-docs/reference/Symb/HOTSPOTREC_TYPE_xxx)
[PLACEHOLDER_ALIGN_xxx](/domino-c-api-docs/reference/Symb/PLACEHOLDER_ALIGN_xxx)
[PLACEHOLDER_FLAG_xxx](/domino-c-api-docs/reference/Symb/PLACEHOLDER_FLAG_xxx)
---

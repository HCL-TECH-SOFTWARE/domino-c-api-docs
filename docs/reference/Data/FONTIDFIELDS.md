##### Data Type : Rich Text
##### FONTIDFIELDS - Component elements of a FONTID.
---
```
#include <fontid.h>
```

**Definition :**
```
typedef struct {
#ifdef LITTLE_ENDIAN_ORDER
 BYTE Face;  /* Font face (FONT_FACE_xxx) */
 BYTE Attrib;  /* Attributes (ISBOLD,etc) */
 BYTE Color;  /* Color index (NOTES_COLOR_xxx) */
 BYTE PointSize; /* Size of font in points */
#else
 BYTE PointSize; /* Size of font in points */
 BYTE Color;  /* Color index (NOTES_COLOR_xxx) */
 BYTE Attrib;  /* Attributes (ISBOLD,etc) */
 BYTE Face;  /* Font face (FONT_FACE_xxx) */
#endif
} FONTIDFIELDS;
```

**Description :**

This structure allows access to the fields within a FONTID. Overlay this structure onto the FontID field to set or read the font information for the rich text field, or more preferably, use the FontSetxxx macros using a FONTID directly.<br>
<br>
The Face member of the FONTIDFIELDS structure may be one of three standard font faces - - FONT_FACE_ROMAN, FONT_FACE_SWISS, or FONT_FACE_TYPEWRITER - - or a font ID resolved by a font table.  A Face member value greater than or equal to STATIC_FONT_FACES (5) refers to an entry in a font table.<br>
<br>
To resolve a non standard font face, the note must contain a font table.  A font table is an item with name $FONT (ITEM_NAME_FONTS) and data type TYPE_COMPOSITE. A font table consists of a CDFONTTABLE structure followed by any number of CDFACE structures.  If the Face member value is greater than or equal to STATIC_FONT_FACES, then it must identify one of the CDFACE entries in the font table.


**Sample Usage :**
```
    CDTEXT          cdtext;     /* rich-text text header */
    FONTIDFIELDS   *pFontID;    /* font definitions in text header */
    char            szString1[] = "Hello world... ";
    WORD            wString1Len = strlen( szString1 );

    wString1Len += (wString1Len%2);

    /* ... steps missing ... */

    cdtext.Header.Signature = SIG_CD_TEXT;
    cdtext.Header.Length = ODSLength( _CDTEXT ) + wString1Len ;

    pFontID = (FONTIDFIELDS *) &(cdtext.FontID);
    
    pFontID->Face = FONT_FACE_SWISS;
    pFontID->Attrib = ISBOLD;
    pFontID->Color = NOTES_COLOR_BLUE;
    pFontID->PointSize = 24;

    ODSWriteMemory( &buff_ptr, _CDTEXT, &cdtext, 1 );
```

**See Also :**
[CDFACE](/domino-c-api-docs/reference/Data/CDFACE)
[CDFONTTABLE](/domino-c-api-docs/reference/Data/CDFONTTABLE)
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[CDPABREFERENCE](/domino-c-api-docs/reference/Data/CDPABREFERENCE)
[CDPARAGRAPH](/domino-c-api-docs/reference/Data/CDPARAGRAPH)
[CDTEXT](/domino-c-api-docs/reference/Data/CDTEXT)
[FONT_FACE_xxx](/domino-c-api-docs/reference/Symb/FONT_FACE_xxx)
[ISxxx](/domino-c-api-docs/reference/Symb/ISxxx)
[NOTES_COLOR_xxx](/domino-c-api-docs/reference/Symb/NOTES_COLOR_xxx)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
[xxx_FONT_ID](/domino-c-api-docs/reference/Symb/xxx_FONT_ID)
---

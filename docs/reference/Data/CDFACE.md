##### Data Type : Composite Data
##### CDFACE - Used in creating a font table.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BYTE Face;              /* ID number of face */
   BYTE Family;            /* Font Family */
   char Name[MAXFACESIZE];
} CDFACE;

**Description :**

This defines part of the structure of a font table item in a note.  A font table item in a note allows rich text in the note to be displayed using fonts other than those defined in FONT_FACE_xxx.<br>
<br>
Font table items are items with name $FONT (ITEM_NAME_FONTS) and data type TYPE_COMPOSITE. a font table consists of a CDFONTTABLE structure followed by any number of CDFACE structures.  Each CDFACE entry in the font table defines one font face.<br>
<br>
Note that font tables are items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CDFACE structures when accessing these records in a font table item in a note.<br>
<br>
The Face member of the CDFACE structure is an application assigned byte, greater than or equal to STATIC_FONT_FACES (5).   <br>
<br>
The Family member of the CDFACE structure is a bit mask byte.  The two low order bits (0-1) specify the pitch of the font.  The four high-order bits (4-7) specify the font family.  Bit 2 is set for Microsoft TrueType fonts.  For Windows 32-bit, bit 3 is set for monospaced fonts.<br>
<br>
/* Family member values of the CDTEXT structure */<br>
/* The Family member (a BYTE) is a bit mask */<br>
/* These definitions are in WINDOWS.H */ <br>

<ul><br>
/* TrueType flag (bit 2) */<br>
#define TRUETYPE_FONTTYPE   0x004<br>
<br>
/* &quot;pitch&quot; values (low 2 bits) */<br>
#define DEFAULT_PITCH    0x00<br>
#define FIXED_PITCH            0x01<br>
#define VARIABLE_PITCH   0x02<br>
#if(WINVER &gt;= 0x0400)<br>
#define MONO_FONT               8	/* Monospace flag (bit 3) */<br>
#endif /* WINVER &gt;= 0x0400 */<br>
<br>
/* &quot;family&quot; values (high 4 bits) */<br>
#define FF_DONTCARE      0x00<br>
#define FF_ROMAN               0x10<br>
#define FF_SWISS                 0x20<br>
#define FF_MODERN           0x30<br>
#define FF_SCRIPT               0x40<br>
#define FF_DECORATIVE  0x50<br>
<br>
The Name member of the CDFACE structure is the IfFaceName member of the LOGFONT structure in Windows.<br>
<br>
To use a font from the font table in a rich text field run of text, set the Face member of the FONTIDFIELDS structure of the FontID member of the CDTEXT structure to the font table's application assigned byte in the Face member of the CDFACE structure.<br>
</ul>



**See Also :**
[CDFONTTABLE](/domino-c-api-docs/reference/Data/CDFONTTABLE)
[CDTEXT](/domino-c-api-docs/reference/Data/CDTEXT)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
---

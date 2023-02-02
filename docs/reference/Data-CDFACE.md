##### Data Type : Composite Data
##### CDFACE - Used in creating a font table.
---
##### #include <editods.h>
**Description :**
This defines part of the structure of a font table item in a note.  A font 
table item in a note allows rich text in the note to be displayed using fonts 
other than those defined in FONT_FACE_xxx.
Font table items are items with name $FONT (ITEM_NAME_FONTS) and data type 
TYPE_COMPOSITE. a font table consists of a CDFONTTABLE structure followed by 
any number of CDFACE structures.  Each CDFACE entry in the font table defines 
one font face.

Note that font tables are items of type TYPE_COMPOSITE. Therefore, API programs 
that run on non-Intel architecture platforms must perform host/canonical 
conversion on CDFACE structures when accessing these records in a font table 
item in a note.

The Face member of the CDFACE structure is an application assigned byte, 
greater than or equal to STATIC_FONT_FACES (5).   

The Family member of the CDFACE structure is a bit mask byte.  The two low 
order bits (0-1) specify the pitch of the font.  The four high-order bits (4-7) 
specify the font family.  Bit 2 is set for Microsoft TrueType fonts.  For 
Windows 32-bit, bit 3 is set for monospaced fonts.

/* Family member values of the CDTEXT structure */
/* The Family member (a BYTE) is a bit mask */
/* These definitions are in WINDOWS.H */ 

/* TrueType flag (bit 2) */
#define TRUETYPE_FONTTYPE   0x004

/* "pitch" values (low 2 bits) */
#define DEFAULT_PITCH    0x00
#define FIXED_PITCH            0x01
#define VARIABLE_PITCH   0x02
#if(WINVER >= 0x0400)
#define MONO_FONT               8 /* Monospace flag (bit 3) */
#endif /* WINVER >= 0x0400 */

/* "family" values (high 4 bits) */
#define FF_DONTCARE      0x00
#define FF_ROMAN               0x10
#define FF_SWISS                 0x20
#define FF_MODERN           0x30
#define FF_SCRIPT               0x40
#define FF_DECORATIVE  0x50

The Name member of the CDFACE structure is the IfFaceName member of the LOGFONT 
structure in Windows.

To use a font from the font table in a rich text field run of text, set the 
Face member of the FONTIDFIELDS structure of the FontID member of the CDTEXT 
structure to the font table's application assigned byte in the Face member of 
the CDFACE structure.

**See Also :**
[CDFONTTABLE](D:/md_files/CDFONTTABLE.md)
[CDTEXT](D:/md_files/CDTEXT.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
---

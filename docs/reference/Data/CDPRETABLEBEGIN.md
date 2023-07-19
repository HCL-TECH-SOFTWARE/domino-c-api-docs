##### Data Type : Composite Data
##### CDPRETABLEBEGIN - Specifies additional table properties.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG        Header;
   DWORD       Flags;
   BYTE        Rows;
   BYTE        Columns;
   DWORD       ColumnSizingBits1;
   DWORD       ColumnSizingBits2;
   BYTE        ViewerType;
   BYTE        Spare;
   WORD        MinRowHeight;
   WORD        Spares[1];
   DWORD       StyleColor1;
   DWORD       StyleColor2;
   COLOR_VALUE InnerBorderColor;
   WORD        NameLength;
	/* NOTE: The following lengths can not be used.  Previous versions of 
Notes
	  are not setup to deal with any length beyond the name length.
	  Hang will occur if they are used and you try to open the document
	  on a previous version of Notes.  In the same light, this sturcture's
	  size can not be changed, no additional items of variable length
	  can be added.

	  The words could simply be used as word storage.  They just can
	  not be useds as lengths.
	*/
   WORD        ImagePacketLength;
   WORD        RowLabelDataLength;
} CDPRETABLEBEGIN;

**Description :**

This CD record provides additional table properties, expanding the information provided in CDTABLEBEGIN.  It will only be recognized in Domino versions 5.0 and greater.  This record will be ignored in pre 5.0 versions.<br>
<br>
	WSIG	Header	Signature and length of this record<br>
	DWORD	Flags	See CDPRETABLE_xxx flags<br>
	BYTE	Rows	Number of rows<br>
	BYTE	Columns	Number of columns<br>
	DWORD	ColumnSizingBits1	Keep track of variable or fixed length columns<br>
	DWORD	ColumnSizingBits2	Keep track of variable or fixed length columns<br>
	BYTE	ViewerType	Special table row display values.  SeeCDTABLEVIEWER_xxx flags	<br>
	BYTE	Spare	Not currently used.  Set to 0.<br>
	WORD	MinRowHeight	Minimum row height<br>
	WORD	Spares[1]	Not currently used.  Set to 0.<br>
	DWORD	StyleColor1	First color in table/cell background color scheme<br>
	DWORD	StyleColor2	Second color in table/cell background color scheme<br>
	COLOR_VALUE	InnerBorderColor	Inner border color<br>
	WORD	NameLength	HTML Tag Name/ID Length	<br>
	WORD	ImagePacketLength	Image Packet Length<br>
	WORD	RowLabelDataLength	Row Label Data Length<br>
<br>
If the NameLength member of this structure is greater than 0, then the table's HTML Tag Name/ID immediately follows this structure.  This is then followed by the Image Packet data (if ImagePacketLength is greater than 0), followed by the Row Label data (if RowLabelDataLength is greater than 0).<br>
<br>
The SyleColor1 and StyleColor2 members of this structure are each stored as a 3-byte RGB value:  Red (byte 0), Green (byte 1), and Blue (byte 2).  Each byte is a color value in the range 0 to 0xff.  For example, 0xff0000 specifies blue, 0x00ff00 specifies green, and 0x0000ff specifies red.  The Flags setting in the CDTABLEBEGIN structure determines how StyleColor1 and StyleColor2 are used by the Notes client.  For example, if you specify CDTABLE_ALTERNATINGROWS in the Flags member of the CDTABLEBEGIN structure, then StyleColor1 and StyleColor2 specify the two alternating background colors of the rows.<br>

<ul><br>
<tt><font size="2">&nbsp; </font></tt></ul>



**See Also :**
[CDPRETABLE_xxx](/domino-c-api-docs/reference/Symb/CDPRETABLE_xxx)
[CDTABLEVIEWER_xxx](/domino-c-api-docs/reference/Symb/CDTABLEVIEWER_xxx)
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[CDTABLEBEGIN](/domino-c-api-docs/reference/Data/CDTABLEBEGIN)
[CDTABLE_xxx](/domino-c-api-docs/reference/Symb/CDTABLE_xxx)
---

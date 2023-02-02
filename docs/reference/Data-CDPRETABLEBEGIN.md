##### Data Type : Composite Data
##### CDPRETABLEBEGIN - Specifies additional table properties.
---
##### #include <editods.h>
**Description :**
This CD record provides additional table properties, expanding the information 
provided in CDTABLEBEGIN.  It will only be recognized in Domino versions 5.0 
and greater.  This record will be ignored in pre 5.0 versions.

	WSIG Header Signature and length of this record
	DWORD Flags See CDPRETABLE_xxx flags
	BYTE Rows Number of rows
	BYTE Columns Number of columns
	DWORD ColumnSizingBits1 Keep track of variable or fixed length columns
	DWORD ColumnSizingBits2 Keep track of variable or fixed length columns
	BYTE ViewerType Special table row display values.  SeeCDTABLEVIEWER_xxx 
flags 
	BYTE Spare Not currently used.  Set to 0.
	WORD MinRowHeight Minimum row height
	WORD Spares[1] Not currently used.  Set to 0.
	DWORD StyleColor1 First color in table/cell background color scheme
	DWORD StyleColor2 Second color in table/cell background color scheme
	COLOR_VALUE InnerBorderColor Inner border color
	WORD NameLength HTML Tag Name/ID Length 
	WORD ImagePacketLength Image Packet Length
	WORD RowLabelDataLength Row Label Data Length

If the NameLength member of this structure is greater than 0, then the table's 
HTML Tag Name/ID immediately follows this structure.  This is then followed by 
the Image Packet data (if ImagePacketLength is greater than 0), followed by the 
Row Label data (if RowLabelDataLength is greater than 0).

The SyleColor1 and StyleColor2 members of this structure are each stored as a 
3-byte RGB value:  Red (byte 0), Green (byte 1), and Blue (byte 2).  Each byte 
is a color value in the range 0 to 0xff.  For example, 0xff0000 specifies blue, 
0x00ff00 specifies green, and 0x0000ff specifies red.  The Flags setting in the 
CDTABLEBEGIN structure determines how StyleColor1 and StyleColor2 are used by 
the Notes client.  For example, if you specify CDTABLE_ALTERNATINGROWS in the 
Flags member of the CDTABLEBEGIN structure, then StyleColor1 and StyleColor2 
specify the two alternating background colors of the rows.


  
**See Also :**
[CDPRETABLE_xxx](D:/md_files/CDPRETABLE_xxx.md)
[CDTABLEVIEWER_xxx](D:/md_files/CDTABLEVIEWER_xxx.md)
[COLOR_VALUE](D:/md_files/COLOR_VALUE.md)
[CDTABLEBEGIN](D:/md_files/CDTABLEBEGIN.md)
[CDTABLE_xxx](D:/md_files/CDTABLE_xxx.md)
---

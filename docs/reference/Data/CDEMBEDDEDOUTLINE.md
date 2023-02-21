##### Data Type : Composite Data
##### CDEMBEDDEDOUTLINE - Structure for an embedded outline within a pane.
---
```
#include <editods.h>
```
**Description :**

This CD Record defines the attributes of an embedded outline.  It is preceded 
by a CDHOTSPOTBEGIN and a CDPLACEHOLDER.  The CD record, CDPLACEHOLDER, further 
defines the CDEMBEDDEDOUTLINE.

 WSIG           Header;     Signature and length of this record
   DWORD      Flags;    see EMBEDDEDOUTLINE_FLAG_xxx
   DWORD      Unused[3];
   WORD        Alignment;   
   WORD        SpaceBetweenEntries;  Space between entries
   WORD        LabelLength;   Label Length
   WORD        Style;    Title Style: 0 - Hide; 1 - Simple; 2 - Hiearchical
   WORD        Title_VOffset;   Title Vertical Offset
   WORD        Title_HOffset;   Title Horizontal Offset
   WORD        Title_Height;   Title Height
   WORD        TopLevel_VOffset;  Top level Vertical Offset
   WORD        TopLevel_HOffset;  Top level Horizontal Offset
   WORD        TopLevel_Height;  Top level height
   WORD        SubLevel_VOffset;  Sub level Vertical Offset
   WORD        SubLevel_HOffset;  Sub level Horizontal Offset
   WORD        SubLevel_Height;  Sub level height
   WORD        NameLength;   Named length
   WORD        TargetFrameLength;  Target Frame length
   FONTID      SelectFontID[3];  see CDFONTID
   FONTID      MouseFontID[3];  see CDFONTID
   WORD        Font_VOffset[3];  Font vertical offset
   WORD        Font_HOffset[3];  Font horizontal offset
   WORD        Align[3];   see ALIGNMENT_xxx
   COLOR_VALUE Control_BackColor; see COLOR_VALUE
   COLOR_VALUE BackColor[9];  see COLOR_VALUE, xxx_BACK_COLOR_OFFSET and 
xxx_BACK_COLOR
   COLOR_VALUE SelectFontColor[3]; see COLOR_VALUE
   WORD        Repeat[4];
   WORD        Background_Align[4];  Background align
   WORD        Background_VOffset[4]; Background vertical offset
   WORD        Background_HOffset[4]; Background horizontal offset
   WORD        wBackground_Image[4];
   COLOR_VALUE NormalFontColor[3]; see COLOR_VALUE
   COLOR_VALUE MouseFontColor[3]; see COLOR_VALUE
   WORD        RootLength;   Root Length
   WORD        TopLevel_PixelHeight;
   WORD   wColWidth;
   WORD   SpareWord;
   DWORD      Spare[4];



**See Also :**
[ALIGNMENT_xxx](/domino-c-api-docs/reference/Symb/ALIGNMENT_xxx)
[CDPLACEHOLDER](/domino-c-api-docs/reference/Data/CDPLACEHOLDER)
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[EMBEDDEDOUTLINE_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDOUTLINE_FLAG_xxx)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[xxx_BACK_COLOR_OFFSET](/domino-c-api-docs/reference/Symb/xxx_BACK_COLOR_OFFSET)
---

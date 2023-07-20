##### Data Type : Composite Data
##### CDEMBEDDEDOUTLINE - Structure for an embedded outline within a pane.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG        Header; /* Signature and length of this record */
   DWORD       Flags; 
   DWORD       Unused[3];
   WORD        Alignment;
   WORD        SpaceBetweenEntries;
   WORD        LabelLength; 
   WORD        Style;
   WORD        Title_VOffset;
   WORD        Title_HOffset;
   WORD        Title_Height;
   WORD        TopLevel_VOffset;
   WORD        TopLevel_HOffset;
   WORD        TopLevel_Height;
   WORD        SubLevel_VOffset;
   WORD        SubLevel_HOffset;
   WORD        SubLevel_Height;
   WORD        NameLength;
   WORD        TargetFrameLength;
   FONTID      SelectFontID[3];
   FONTID      MouseFontID[3];
   WORD        Font_VOffset[3];
   WORD        Font_HOffset[3];
   WORD        Align[3];
   COLOR_VALUE Control_BackColor;
   COLOR_VALUE BackColor[9];
   COLOR_VALUE SelectFontColor[3];
   WORD        Repeat[4];
   WORD        Background_Align[4];
   WORD        Background_VOffset[4];
   WORD        Background_HOffset[4];
   WORD        wBackground_Image[4];
   COLOR_VALUE NormalFontColor[3];
   COLOR_VALUE MouseFontColor[3];
   WORD        RootLength;
   WORD        TopLevel_PixelHeight;
	WORD  wColWidth;
	WORD  SpareWord;
   DWORD       Spare[4];
} CDEMBEDDEDOUTLINE;
```

**Description :**

This CD Record defines the attributes of an embedded outline.  It is preceded by a CDHOTSPOTBEGIN and a CDPLACEHOLDER.  The CD record, CDPLACEHOLDER, further defines the CDEMBEDDEDOUTLINE.
<ul><br>
<br>
 WSIG           Header; 			 Signature and length of this record<br>
   DWORD      Flags;				see EMBEDDEDOUTLINE_FLAG_xxx<br>
   DWORD      Unused[3];<br>
   WORD        Alignment;			<br>
   WORD        SpaceBetweenEntries;		Space between entries<br>
   WORD        LabelLength;			Label Length<br>
   WORD        Style;				Title Style: 0 - Hide; 1 - Simple; 2 - Hiearchical<br>
   WORD        Title_VOffset;			Title Vertical Offset<br>
   WORD        Title_HOffset;			Title Horizontal Offset<br>
   WORD        Title_Height;			Title Height<br>
   WORD        TopLevel_VOffset;		Top level Vertical Offset<br>
   WORD        TopLevel_HOffset;		Top level Horizontal Offset<br>
   WORD        TopLevel_Height;		Top level height<br>
   WORD        SubLevel_VOffset;		Sub level Vertical Offset<br>
   WORD        SubLevel_HOffset;		Sub level Horizontal Offset<br>
   WORD        SubLevel_Height;		Sub level height<br>
   WORD        NameLength;			Named length<br>
   WORD        TargetFrameLength;		Target Frame length<br>
   FONTID      SelectFontID[3];		see CDFONTID<br>
   FONTID      MouseFontID[3];		see CDFONTID<br>
   WORD        Font_VOffset[3];		Font vertical offset<br>
   WORD        Font_HOffset[3];		Font horizontal offset<br>
   WORD        Align[3];			see ALIGNMENT_xxx<br>
   COLOR_VALUE Control_BackColor;	see COLOR_VALUE<br>
   COLOR_VALUE BackColor[9];		see COLOR_VALUE, xxx_BACK_COLOR_OFFSET and xxx_BACK_COLOR<br>
   COLOR_VALUE SelectFontColor[3];	see COLOR_VALUE<br>
   WORD        Repeat[4];<br>
   WORD        Background_Align[4];		Background align<br>
   WORD        Background_VOffset[4];	Background vertical offset<br>
   WORD        Background_HOffset[4];	Background horizontal offset<br>
   WORD        wBackground_Image[4];<br>
   COLOR_VALUE NormalFontColor[3];	see COLOR_VALUE<br>
   COLOR_VALUE MouseFontColor[3];	see COLOR_VALUE<br>
   WORD        RootLength;			Root Length<br>
   WORD        TopLevel_PixelHeight;<br>
   WORD	  wColWidth;<br>
   WORD	  SpareWord;<br>
   DWORD      Spare[4];<br>
</ul>



**See Also :**
[ALIGNMENT_xxx](/domino-c-api-docs/reference/Symb/ALIGNMENT_xxx)
[CDPLACEHOLDER](/domino-c-api-docs/reference/Data/CDPLACEHOLDER)
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[EMBEDDEDOUTLINE_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDOUTLINE_FLAG_xxx)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[xxx_BACK_COLOR_OFFSET](/domino-c-api-docs/reference/Symb/xxx_BACK_COLOR_OFFSET)
---

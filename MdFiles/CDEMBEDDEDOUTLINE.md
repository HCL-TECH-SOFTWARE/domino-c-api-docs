




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 5.0**



**Data Type : Composite Data; Rich
Text**



**CDEMBEDDEDOUTLINE** **-** Structure
for an embedded outline within a pane.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


   WSIG        Header;
/\* Signature and length of this record \*/


   DWORD       Flags;     


   DWORD      
Unused[3];


   WORD       
Alignment;


   WORD       
SpaceBetweenEntries;


   WORD       
LabelLength;       


   WORD        Style;


   WORD       
Title\_VOffset;


   WORD       
Title\_HOffset;


   WORD       
Title\_Height;


   WORD       
TopLevel\_VOffset;


   WORD       
TopLevel\_HOffset;


   WORD       
TopLevel\_Height;


   WORD       
SubLevel\_VOffset;


   WORD       
SubLevel\_HOffset;


   WORD       
SubLevel\_Height;


   WORD       
NameLength;


   WORD       
TargetFrameLength;


   FONTID     
SelectFontID[3];


   FONTID     
MouseFontID[3];


   WORD       
Font\_VOffset[3];


   WORD       
Font\_HOffset[3];


   WORD       
Align[3];


   COLOR\_VALUE
Control\_BackColor;


   COLOR\_VALUE
BackColor[9];


   COLOR\_VALUE
SelectFontColor[3];


   WORD        Repeat[4];


   WORD       
Background\_Align[4];


   WORD       
Background\_VOffset[4];


   WORD       
Background\_HOffset[4];


   WORD       
wBackground\_Image[4];


   COLOR\_VALUE
NormalFontColor[3];


   COLOR\_VALUE
MouseFontColor[3];


   WORD       
RootLength;


   WORD       
TopLevel\_PixelHeight;


        WORD           wColWidth;


        WORD           SpareWord;


   DWORD      
Spare[4];


} CDEMBEDDEDOUTLINE;


 


**Description :**



This CD
Record defines the attributes of an embedded outline.  It is preceded by a
CDHOTSPOTBEGIN and a CDPLACEHOLDER.  The CD record, CDPLACEHOLDER, further
defines the CDEMBEDDEDOUTLINE.


 


 WSIG          
Header;                            Signature and length of this record


  
DWORD      Flags;                                          see
EMBEDDEDOUTLINE\_FLAG\_xxx


   DWORD      Unused[3];


  
WORD        Alignment;                                   


  
WORD        SpaceBetweenEntries;                 Space between entries


  
WORD        LabelLength;                                Label Length


  
WORD        Style;                                           Title Style: 0 -
Hide; 1 - Simple; 2 - Hiearchical


  
WORD        Title\_VOffset;                               Title Vertical Offset


  
WORD        Title\_HOffset;                              Title Horizontal Offset


  
WORD        Title\_Height;                                Title Height


  
WORD        TopLevel\_VOffset;                       Top level Vertical Offset


  
WORD        TopLevel\_HOffset;                       Top level Horizontal Offset


  
WORD        TopLevel\_Height;             Top level height


  
WORD        SubLevel\_VOffset;                       Sub level Vertical Offset


  
WORD        SubLevel\_HOffset;                       Sub level Horizontal Offset


   WORD     
  SubLevel\_Height;             Sub level height


  
WORD        NameLength;                               Named length


  
WORD        TargetFrameLength;                    Target Frame length


  
FONTID      SelectFontID[3];                see CDFONTID


  
FONTID      MouseFontID[3];               see CDFONTID


  
WORD        Font\_VOffset[3];               Font vertical offset


  
WORD        Font\_HOffset[3];              Font horizontal offset


  
WORD        Align[3];                           see ALIGNMENT\_xxx


  
COLOR\_VALUE Control\_BackColor;       see COLOR\_VALUE


  
COLOR\_VALUE BackColor[9];                see COLOR\_VALUE, xxx\_BACK\_COLOR\_OFFSET
and xxx\_BACK\_COLOR


  
COLOR\_VALUE SelectFontColor[3];       see COLOR\_VALUE


  
WORD        Repeat[4];


  
WORD        Background\_Align[4];                   Background align


  
WORD        Background\_VOffset[4];   Background vertical offset


  
WORD        Background\_HOffset[4];   Background horizontal offset


  
WORD        wBackground\_Image[4];


  
COLOR\_VALUE NormalFontColor[3];      see COLOR\_VALUE


  
COLOR\_VALUE MouseFontColor[3];       see COLOR\_VALUE


  
WORD        RootLength;                                 Root Length


  
WORD        TopLevel\_PixelHeight;


   WORD    
wColWidth;


   WORD    
SpareWord;


  
DWORD      Spare[4];


 


 


 **See Also :**


**[ALIGNMENT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1D7A040FE8C0B701852566C5004E2220)**


**[CDPLACEHOLDER](CDPLACEHOLDER.md)**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**


**[EMBEDDEDOUTLINE\_FLAG\_xxx](EMBEDDEDOUTLINE_FLAG_xxx.md)**


**[FONTID](FONTID.md)**


**[xxx\_BACK\_COLOR\_OFFSET](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/EF01D5BD35461B1785256678004BAA61)**



----------------------------------------------------------------------------------------------------------


 






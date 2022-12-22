




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




**Initial Release 4.1**



**Data Type : Composite Data; Rich
Text**



**CDLAYOUTTEXT** **-** Text element
definition within a layout region.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BSIG           Header;  

    ELEMENTHEADER  ElementHeader;  

    DWORD          Flags;  

    BYTE           Reserved[16];  

/\*  For records saved with builds prior to 134,


   the 8-bit text
string follows... \*/  

} CDLAYOUTTEXT;


 


**Description :**



A text
element in a layout region of a form is defined by a CDLAYOUTTEXT record.  This
record must be between a CDLAYOUT record and a CDLAYOUTEND record.  This record
is usually followed by other CD records identifying text,  graphical, or action
elements associated with the element.  The fields in this record are:


 


Header                   Defines
this composite data item as a CDLAYOUTTEXT item.


ElementHeader       Structure
containing graphical attributes of the field (see ELEMENTHEADER).


Flags                      Flags
for this field (see LAYOUT\_TEXT\_FLAG\_xxx).


 


This record
may be followed by 8-bit text data, if the record was created by an early Test
Build of Notes Release 4.0.  Normally, other CD records will follow containing
the text and graphical elements associated with this text element.


 


 **See Also :**


**[CDLAYOUT](CDLAYOUT.md)**


**[CDLAYOUTBUTTON](CDLAYOUTBUTTON.md)**


**[CDLAYOUTEND](CDLAYOUTEND.md)**


**[CDLAYOUTFIELD](CDLAYOUTFIELD.md)**


**[CDLAYOUTGRAPHIC](CDLAYOUTGRAPHIC.md)**


**[ELEMENTHEADER](ELEMENTHEADER.md)**


**[LAYOUT\_TEXT\_FLAG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F82A683E07C1D453852563040076023C)**



----------------------------------------------------------------------------------------------------------


 






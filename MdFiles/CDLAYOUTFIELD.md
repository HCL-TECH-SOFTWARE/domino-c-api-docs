




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



**CDLAYOUTFIELD** **-** Field
definition within a layout region.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BSIG           Header;  

   ELEMENTHEADER  ElementHeader;  

   DWORD          Flags;  

   BYTE           bFieldType;  

   BYTE           Reserved[15];  

} CDLAYOUTFIELD;


 


**Description :**



A field in a
layout region of a form is defined by a CDLAYOUTFIELD record.  This record must
be between a CDLAYOUT record and a CDLAYOUTEND record.  This record is usually
followed by other CD records identifying text,  graphical, or action elements
associated with the field.  The fields in this record are:


 


Header                   Defines
this composite data item as a CDLAYOUTFIELD item.


ElementHeader       Structure
containing graphical attributes of the field (see ELEMENTHEADER).


Flags                      Flags
for this field (see LAYOUT\_FIELD\_FLAG\_xxx).


bFieldType             Type
of user interface for this element (see LAYOUT\_FIELD\_TYPE\_xxx).


 


 **See Also :**


**[CDLAYOUT](CDLAYOUT.md)**


**[CDLAYOUTBUTTON](CDLAYOUTBUTTON.md)**


**[CDLAYOUTEND](CDLAYOUTEND.md)**


**[CDLAYOUTGRAPHIC](CDLAYOUTGRAPHIC.md)**


**[CDLAYOUTTEXT](CDLAYOUTTEXT.md)**


**[ELEMENTHEADER](ELEMENTHEADER.md)**


**[LAYOUT\_FIELD\_FLAG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2AB64B916BC38E60852563040076D519)**


**[LAYOUT\_FIELD\_TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C2E3AC497B95BB4C8525630400767D84)**



----------------------------------------------------------------------------------------------------------


 











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



**CDLAYOUTBUTTON** **-** Button
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

} CDLAYOUTBUTTON;


 


**Description :**



A button in
a layout region of a form is defined by a CDLAYOUTBUTTON record.  This record
must be between a CDLAYOUT record and a CDLAYOUTEND record.  This record is
usually followed by other CD records identifying text,  graphical, or action
elements associated with the button.  The fields in this record are:


 


Header                   Defines
this composite data item as a CDLAYOUTBUTTON item.


ElementHeader       Structure
containing graphical attributes of the button (see ELEMENTHEADER).


Flags                      Flags
for this button (no flags are currently defined).


 


 **See Also :**


**[CDLAYOUT](CDLAYOUT.md)**


**[CDLAYOUTEND](CDLAYOUTEND.md)**


**[CDLAYOUTFIELD](CDLAYOUTFIELD.md)**


**[CDLAYOUTGRAPHIC](CDLAYOUTGRAPHIC.md)**


**[CDLAYOUTTEXT](CDLAYOUTTEXT.md)**


**[ELEMENTHEADER](ELEMENTHEADER.md)**



----------------------------------------------------------------------------------------------------------


 






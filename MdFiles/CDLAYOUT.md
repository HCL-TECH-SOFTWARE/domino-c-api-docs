




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



**CDLAYOUT** **-** Start record
for layout region on a form


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct{  

   BSIG   Header;  

   WORD   wLeft;  

   WORD   wWidth;  

   WORD   wHeight;  

   DWORD  Flags;  

   WORD   wGridSize;  

   BYTE   Reserved[14];  

} CDLAYOUT;


 


**Description :**



The
definition for a layout region on a form is stored as CD records in the $Body
item of the form note.  The layout region begins with a CDLAYOUT record and
ends with a CDLAYOUTEND record.  Other records in the layout region define
buttons, graphics, fields, or other rich text elements.  The fields in this
record are:


 


Header             Defines
this composite data item as a CDLAYOUT item.


wLeft                Left
margin of the layout region in "twips"


wWidth             Width
of the layout region in "twips"


wHeight            Height
of the layout region in "twips"


Flags                Flags
for this layout region (see LAYOUT\_FLAG\_xxx)


wGridSize         Spacing
of grid points in "twips"


 


 **See Also :**


**[CDLAYOUTBUTTON](CDLAYOUTBUTTON.md)**


**[CDLAYOUTEND](CDLAYOUTEND.md)**


**[CDLAYOUTFIELD](CDLAYOUTFIELD.md)**


**[CDLAYOUTGRAPHIC](CDLAYOUTGRAPHIC.md)**


**[CDLAYOUTTEXT](CDLAYOUTTEXT.md)**


**[LAYOUT\_FLAG\_xxx](LAYOUT_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 











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



**Data Type : Rich Text**



**ELEMENTHEADER** **-** Common
fields in CDLAYOUTxxx records.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


   WORD        wLeft;


   WORD        wTop;


   WORD        wWidth;


   WORD        wHeight;


   FONTID     
FontID;          /\* Font ID \*/


   BYTE       
byBackColor;     /\* Background color \*/


   BYTE        bSpare;


   COLOR\_VALUE
BackgroundColor; /\* v5.0 background color \*/


} ELEMENTHEADER;


 


**Description :**



This
structure contains the common fields for the graphical elements in a layout
region of a form.  The fields in this structure are:


 


wLeft                      Location
of the left edge of the element in twips


wTop                      Location
of the top of the element in twips


wWidth                   Width
of the element in twips


wHeight                  Height
of the element in twips


FontID                    Font
used to display text in the element


byBackColor           Background
color for the element


bSpare


BackgroundColor    Release
5.0 Backgroun color


 


 **See Also :**


**[CDLAYOUTBUTTON](CDLAYOUTBUTTON.md)**


**[CDLAYOUTFIELD](CDLAYOUTFIELD.md)**


**[CDLAYOUTGRAPHIC](CDLAYOUTGRAPHIC.md)**


**[CDLAYOUTTEXT](CDLAYOUTTEXT.md)**



----------------------------------------------------------------------------------------------------------


 






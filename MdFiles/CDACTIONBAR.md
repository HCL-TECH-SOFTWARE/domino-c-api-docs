




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




**Initial Release 4.5**



**Data Type : Composite Data; Form**



**CDACTIONBAR** **-** Action
button bar attributes for a form or view


**----------------------------------------------------------------------------------------------------------**



**#include
<actods.h>**



**Definition :**



typedef struct {  

   BSIG   Header;      /\* Signature and Length \*/  

    WORD   BackColor;   /\* Background color index \*/  

    WORD   LineColor;   /\* Line color index \*/  

    WORD   LineStyle;   /\* Style of line \*/  

    WORD   BorderStyle; /\* Border style \*/  

    WORD   BorderWidth; /\* Border width (twips) \*/  

    DWORD  dwFlags;  

    DWORD  ShareID;     /\* ID of Shared Action \*/  

   FONTID FontID;  

   WORD   BtnHeight;   /\* Height of the Button \*/  

   WORD   HeightSpc;   /\* Height spacing \*/


} CDACTIONBAR;


 


**Description :**



The designer
of a form or view may define custom actions for that form or view.  The
attributes for the button bar are stored in the CDACTIONBAR record in the
$ACTIONS and/or $V5ACTIONS item for the design note describing the form or
view.


 


The fields
in this structure are:


 


Header           
Identifies this as a CDACTIONBAR record


BackColor      
Background color


LineColor        
Line color


LineStyle        
Line style code (see ACTION\_LINE\_xxx)


BorderStyle     
Border style code (see ACTION\_BORDER\_xxx)


BorderWidth  
 Width of the border, in pixels


dwFlags         
Flag values (see ACTION\_BAR\_FLAG\_xxx)


ShareID          
Last ID of Shared Actions


FontID


BtnHeight         
Height of the button


HeightSpc       
Height spacing


 


This record
is followed by CDACTIONBAREXT, then CDACTION records defining the available
actions.


 **See Also :**


**[ACTION\_BAR\_FLAG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/02F4B1A7D140E99585256A2A0060E836)**


**[ACTION\_BORDER\_xxx](ACTION_BORDER_xxx.md)**


**[ACTION\_LINE\_xxx](ACTION_LINE_xxx.md)**


**[CDACTION](CDACTION.md)**


**[CDACTIONBAREXT](CDACTIONBAREXT.md)**



----------------------------------------------------------------------------------------------------------


 






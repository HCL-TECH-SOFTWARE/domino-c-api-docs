




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



**CDCOLOR** **-** Specifies
the Paper Color.


**----------------------------------------------------------------------------------------------------------**



**#include
<colorods.h>**



**Definition :**



typedef struct {  

   BSIG Header;           /\* Signature and length of this record \*/  

   COLOR\_VALUE Color;  

} CDCOLOR;


 


**Description :**



This CD
Record identifies the paper color for a given document.


 


Header                   Identifies
this as a CDCOLOR record.


COLOR\_VALUE      CD
Structure defining the components of paper color.


 


 **See Also :**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**


**[COLOR\_VALUE\_FLAGS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D8886C73BE9807FE85256676003F5054)**



----------------------------------------------------------------------------------------------------------


 






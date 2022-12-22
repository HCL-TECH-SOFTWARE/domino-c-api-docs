




<!--
 /\* Font Definitions \*/
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




**Initial Release 4.0**



**Function : Rich Text**



**MapExtColorToV3Color** **- Convert a
Notes Release 4 color index to a Notes Release 3 compatible color index.**


**----------------------------------------------------------------------------------------------------------**



**#include <colorid.h>**



WORD
LNPUBLIC **MapExtColorToV3Color(**  

      WORD  color**);**



**Description :**



In Notes
Release 4, the number of choices for a view's background color and for a form's
paper color have increased.  This function maps a Notes Release 4 color index
to the closest matching Notes Release 3  color index.  These color indexes are
used in the structures, CDDOCUMENT and VIEW\_TABLE\_FORMAT2.


 


**Parameters :**



Input :  

color  -  Notes Release 4 color index.  

  




Output :  

(routine)  -  Notes Release 3 color  index that maps to the given Release 4
form or view background color.  

  

  




 **See Also :**


**[CDDOCUMENT](CDDOCUMENT.md)**


**[VIEW\_TABLE\_FORMAT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004C005400E90078852564C3006285BD)**


**[NOTES\_COLOR\_xxx](NOTES_COLOR_xxx.md)**


**[MapV3ColorToExtColor](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/31FD05DD6A19A88A852562A700582632)**



----------------------------------------------------------------------------------------------------------


 






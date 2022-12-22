




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




**Initial Release 6**



**Symbolic Value : OLE**



**ASSOCITEM\_IFEXISTS\_xxx** **-** NSFNoteOLEAssociateFileToObject
- wIfExists


**----------------------------------------------------------------------------------------------------------**



**#include <nsfasc.h>**


 **Symbolic Values :**      ASSOCITEM\_IFEXISTS\_FAIL           -  If attachment ($FILE)
already exists as an associated item on any OLE object in the note, return an
error.  

  

      ASSOCITEM\_IFEXISTS\_OVERWRITE         -  If attachment ($FILE) already
exists as an associated item on any OLE object in the note, overwrite it with
the specified file.  

  

      ASSOCITEM\_IFEXISTS\_USEEXISTING       -  If attachment ($FILE) already
exists as an associated item on any OLE object in the note, use the existing
attachment and ignore the specified file.  

  




 **See Also :**


**[NSFNoteOLEAssociateFileToObject](NSFNoteOLEAssociateFileToObject.md)**



----------------------------------------------------------------------------------------------------------


 






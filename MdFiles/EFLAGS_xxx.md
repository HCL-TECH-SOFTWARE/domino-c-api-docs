




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Symbolic Value : File Attachment**



**EFLAGS\_xxx** **-** Additional
NSFNoteAttachFile encoding types.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      EFLAGS\_MASK        -  Bit mask specifiying the possible
EFLAGS\_xxx values.  

  

      EFLAGS\_INDOC      -  Set the FILEFLAG\_INDOC flag in the Flags member of
the FILEOBJECT structure.  

  

      EFLAGS\_KEEPPATH           -  Don't strip off path in the filename.  

  

      EFLAGS\_AUTOCOMPRESSED        -  Set the FILEFLAG\_AUTOCOMPRESSED flag in
the Flags member of the FILEOBJECT structure.  

  




**Description :**



These values
may optionally be bitwised OR'd in the encoding\_type parameter of
NSFNoteAttachFile.


 **See Also :**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**



----------------------------------------------------------------------------------------------------------


 






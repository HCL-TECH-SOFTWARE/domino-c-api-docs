




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



**Symbolic Value : File Attachment**



**NTATT\_xxx** **-** File
attachment - file types.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      NTATT\_FTYPE\_MASK         -  File type mask.  

  

      NTATT\_FTYPE\_FLAT          -  Normal, one fork file.  

  

      NTATT\_FTYPE\_MACBIN     -  MacBinaryII file.  

  

      NTATT\_FTYPE\_EBCDIC      -  EBCDIC flat file.  

  

      NTATT\_NODEALLOC           -  Don't deallocate object when item is
deleted.  

  




**Description :**



These values
are optional values for the encoding\_type parameter of NSFNoteAttachFile.  It
specifies the file type of a file attachment.  


 **See Also :**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**



----------------------------------------------------------------------------------------------------------


 






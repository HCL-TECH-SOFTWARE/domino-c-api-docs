




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




**Initial Release 8.5**



**Symbolic Value : archiving service**



**ARCHIVE\_ATTACH\_xxx** **-** Indicates
the type of attachment.


**----------------------------------------------------------------------------------------------------------**



**#include <archsvc.h>**


 **Symbolic Values :**      ARCHIVE\_ATTACH\_ENCRYPTED   -  Indicates attachment is being
passed encrypted.  

  

      ARCHIVE\_ATTACH\_MACBIN\_RAW             -  Indicates attachment data is mac
binary data as stored in NSF (compressed data and resource fork only).  

  

      ARCHIVE\_ATTACH\_RAW    -  Indicates that this is not a file attachment but
object data known only to notes.  

  




 **See Also :**


**[ARCHIVEATTACHINIT](ARCHIVEATTACHINIT.md)**



----------------------------------------------------------------------------------------------------------


 






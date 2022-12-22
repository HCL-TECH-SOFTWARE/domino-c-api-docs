




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




 


**Function : File Attachment**



**NSFNoteDetachFile** **- Deletes
an attached file from a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteDetachFile(**  

      NOTEHANDLE  note\_handle,  

      BLOCKID  item\_blockid**);**



**Description :**



Deletes an
attached file item (referenced by its BLOCKID) from a note and also deallocates
the disk space used to store the attached file in the database.  The BLOCKID of
the item can be easily obtained by item name from a call to NSFItemInfo.


 


**Parameters :**



Input :  

note\_handle  -  Handle of the Note which contains the attached file.  

  

item\_blockid  -  BLOCKID of the attachment item that is to be detached/deleted.  

  




Output :  

(routine)  -  Return status from this call.  Always returns NOERROR.  

  

  




 **See Also :**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**


**[NSFNoteExtractFile](NSFNoteExtractFile.md)**



----------------------------------------------------------------------------------------------------------


 






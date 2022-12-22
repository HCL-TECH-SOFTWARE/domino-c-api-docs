




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



**NSFNoteExtractFileExt** **- Extract a
file from an item in a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteExtractFileExt(**  

      NOTEHANDLE  note\_handle,  

      BLOCKID  item\_blockid,  

      const char far \*file\_name,  

      ENCRYPTION\_KEY far \*DecryptionKey,  

      WORD  wFlags**);**



**Description :**



Creates a
disk file from the contents of an attached item (referenced by its BLOCKID). 
The BLOCKID can be easily obtained by item name using NSFItemInfo.  The
file\_name parameter specifies the path, file name, and extension of the file to
be created.  If only a file name and extension are supplied, the file will be
created in the current working directory.


 


   **Note:
NSFNoteExtractFileExt should be deprecated from Notes/Domino 8.0.1. The
preferred function to use in their place is NSFNoteCipherDecrypt.**



**Parameters :**



Input :  

note\_handle  -  Handle of note from which disk file will be extracted.  

  

item\_blockid  -  BLOCKID of the attachment item from which file is to be
extracted.  

  

file\_name  -  A null-terminated file name of the file that will be created.  

  

DecryptionKey  -  Use NULL if the attachment is not encrypted.  Otherwise, use
a pointer to the ENCRYPTION\_KEY structure returned by NSFNoteDecrypt.  

  

wFlags  -  The possible values for the wFlags are defined by the NTEXT\_xxx
symbol.  

  




Output :  

(routine)  -  Return status from this call includes:  

  

NOERROR - Successfully extracted file.  

  

ERR\_ENCODING - Unknown type of compression technique.  

  

ERR\_NOEXTRACT\_ENCRYPTED - You must supply the decryption key in order to
extract this file.  

  

ERR\_NOTE\_BADATTSIGN - Attachment has been modified or corrupted since signed!  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**


**[NSFNoteDetachFile](NSFNoteDetachFile.md)**


**[NSFNoteExtractFile](NSFNoteExtractFile.md)**


**[NSFNoteDecrypt](NSFNoteDecrypt.md)**



----------------------------------------------------------------------------------------------------------


 






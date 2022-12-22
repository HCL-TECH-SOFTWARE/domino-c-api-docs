




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Data Type : Note**



**ENCRYPTION\_KEY** **-** Decryption
key for file attachment objects.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfnote.h>**



**Definition :**



typedef struct
{                          

   BYTE Byte1;               

   WORD Word1;               

   BYTE Text[16];  

} ENCRYPTION\_KEY;


 


**Description :**



This
structure is returned from NSFNoteDecrypt and can be used to decrypt file
attachment objects in NSFNoteExtractFile and NSFNoteExtractFileExt.  File
attachment objects are not decrypted until necessary.


 **See Also :**


**[NSFNoteDecrypt](NSFNoteDecrypt.md)**


**[NSFNoteExtractFile](NSFNoteExtractFile.md)**


**[NSFNoteExtractFileExt](NSFNoteExtractFileExt.md)**



----------------------------------------------------------------------------------------------------------


 






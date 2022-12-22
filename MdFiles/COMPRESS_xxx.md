




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




 


**Symbolic Value : Note**



**COMPRESS\_xxx** **-** Types of
compression used for file attachments.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      COMPRESS\_NONE              -  Indicates that no compression
algorithm is used.  

  

      COMPRESS\_HUFF   -  Indicates that the attached file is encoded using a
Huffman algorithm.  

  

      COMPRESS\_MASK              -  Used for NSFNoteAttachFile() - Encoding
argument.  

  

      COMPRESS\_LZ1      -  Indicates that the attached file is encoded using
LZ1 compression.  

  

      RECOMPRESS\_HUFF          -  Indicates that the attached file is
re-compressed with Huffman compression, even if LZ1 is supported.  

  




**Description :**



Specifies
compression algorithm used when attaching file to a note.


 **See Also :**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**



----------------------------------------------------------------------------------------------------------


 






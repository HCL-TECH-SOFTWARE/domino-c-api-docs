




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



**HOST\_xxx** **-** File
attachment definitions.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      HOST\_MSDOS         -  Attached file is in DOS format. Each
line in the file ends with <carriage return><newline>, with an
optional ^Z at the end of the file.  

  

      HOST\_OLE   -  The internal format of the file is unknown to Domino. The
format is defined by the application that attached the file.  

  

      HOST\_MAC             -  Attached file is in Macintosh format.  

  

      HOST\_UNKNOWN   -  The attached file came in through a gateway, and its
internal format is unknown.  

  

      HOST\_HPFS            -  The attached file is in High Performance File
System format. It may contain exended attributes and long filenames.  

  

      HOST\_OLELIB         -  Attached file is an encapsulated OLE object.  

  

      HOST\_BYTEARRAY\_EXT    -  OLE 2 ILockBytes byte array extent table. Used
to be HOST\_DOCFILE (Attached file is an OLE 2.0 compound file).  

  

      HOST\_BYTEARRAY\_PAGE              -  OLE 2 ILockBytes byte array page.  

  

      HOST\_MASK           -  Used for NSFNoteAttachFile() - Encoding argument.  

  

      HOST\_CDSTORAGE            -  Externally stored CD records. Multiple
blocks of CD records may be stored. The storage contains a WORD with the number
of blocks, a WORD for each block with the length of the block, a WORD
containing TYPE\_COMPOSITE, and the actual CD records.  

  

      HOST\_STREAM       -  Binary private stream.  

  

      HOST\_LINK             -  Contains a RESOURCELINK to a named element.  

  

      HOST\_LOCAL          -  Used only as an argument to NSFNoteAttachFile,
this specifies that the file should be attached using the host type of the
local operating system.  

  




**Description :**



Specifies
the file type used when attaching file to a note.


 **See Also :**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**



----------------------------------------------------------------------------------------------------------


 






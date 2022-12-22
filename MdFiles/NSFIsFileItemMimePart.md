




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




**Initial Release 7.0.2**



**Function : MIME**



**NSFIsFileItemMimePart** **- Searches
all TYPE\_MIME\_PART items on the note to see if the given $File item contains
MIME part data.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



BOOL
LNPUBLIC **NSFIsFileItemMimePart(**  

      NOTEHANDLE  hNote,  

      BLOCKID  bhFileItem**);**



**Description :**



Given a
BLOCKID to a $FILE item, the function NSFIsFileItemMimePart returns TRUE if the
file contains a MIME part item's data, FALSE otherwise.


 


**Parameters :**



Input :  

hNote  -  a handle to an open note.  

  

bhFileItem  -  BLOCKID to a $FILE item.  

  




Output :  

(routine)  -  TRUE if input file item contains MIME part data.  

  

  




 **See Also :**


**[BLOCKID](BLOCKID.md)**



----------------------------------------------------------------------------------------------------------


 






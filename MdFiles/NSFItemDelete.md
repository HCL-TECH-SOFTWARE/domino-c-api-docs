




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




 


**Function : Item (Field)**



**NSFItemDelete** **- Deletes
an item from a note by name.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemDelete(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name,  

      WORD  name\_len**);**



**Description :**



Deletes a
named item from the in-memory copy of a note.


 


**Parameters :**



Input :  

note\_handle  -  Handle of note from which item is to be deleted.  

  

item\_name  -  The name of the item in the note. This name is equivalent to the
field name when you design a form using the screen interface.   

  

name\_len  -  The length of item\_name.  

  




Output :  

(routine)  -  Return status from this call.  A successful call returns NOERROR.  

  

  




 **See Also :**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFItemAppendByBLOCKID](NSFItemAppendByBLOCKID.md)**


**[NSFItemDeleteByBLOCKID](NSFItemDeleteByBLOCKID.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**



----------------------------------------------------------------------------------------------------------


 






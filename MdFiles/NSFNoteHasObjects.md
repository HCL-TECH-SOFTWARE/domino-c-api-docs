




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




 


**Function : Note**



**NSFNoteHasObjects** **- Returns
TRUE if note contains any object items. FALSE otherwise.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFNoteHasObjects(**  

      NOTEHANDLE  hNote,  

      BLOCKID far \*bhFirstObjectItem**);**



**Description :**



This returns
TRUE if the specified note contains any object items, FALSE otherwise.   

  

Object items are items of type TYPE\_OBJECT. Domino and Notes use objects to
store data that is not rendered on the screen by the Notes editor. Examples
include file attachments ($FILE fields), help indexes, and macro left-to-do
lists ($LeftToDo fields).  

  

The BLOCKID value obtained using this function refers to memory within a note. 
This memory is managed by Domino and Notes, and should not be freed by the
application.


 


**Parameters :**



Input :  

hNote  -  Handle to the open note.  

  




Output :  

(routine)  -  TRUE if note contains any object items.  

  

  

bhFirstObjectItem  -  Receives the BLOCKID of the object item. Note: this
variable receives the item BLOCKID, not the value BLOCKID. The item block ID is
the same as what is received by item\_blockid in NSFItemInfo, not value\_blockid.  

  




 **See Also :**


**[NSFItemAppendObject](NSFItemAppendObject.md)**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**



----------------------------------------------------------------------------------------------------------


 






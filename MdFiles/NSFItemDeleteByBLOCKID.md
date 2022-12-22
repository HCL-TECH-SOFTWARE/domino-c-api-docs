




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




 


**Function : Item (Field)**



**NSFItemDeleteByBLOCKID** **- Deletes
an item from a note by BLOCKID.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemDeleteByBLOCKID(**  

      NOTEHANDLE  note\_handle,  

      BLOCKID  item\_blockid**);**



**Description :**



Deletes an
item specified by its BLOCKID from the in-memory copy of a note, and
deallocates the storage associated with the item.  

  

Use NSFItemDeleteByBLOCKID to delete and item from a Note if you do not have
the item name. You may obtain an item BLOCKID without the item name by
specifying NULL as the item\_name input argument to NSFItemInfo() or
NSFItemInfoNext().  NSFItemDeleteByBLOCKID() may also be useful if there are
multiple items that have the same name in the note, and you want to delete a
particular one.  

  

Normally, if you know the name of the item, use NSFItemDelete to delete the
item from the note.


 


**Parameters :**



Input :  

note\_handle  -  Handle of note from which item is to be deleted.  

  

item\_blockid  -  The BLOCKID of the item (NOT the BLOCKID of the item's value)
to be removed from the note and deallocated.  

  




Output :  

(routine)  -  Always returns NOERROR.  

  

  




 **Sample Usage :**


  

NOTEHANDLE   hRespNote;  

BLOCKID     bhThisBodyItem;  

WORD        wBodyType;  

BLOCKID     bhBodyValue;  

DWORD       dwBodyValueLength;  

  

/\* steps missing ... \*/  

  

if (status = NSFItemInfo(   hRespNote,  

                        szBodyFieldName,  

                        lstrlen(szBodyFieldName),  

                        &bhThisBodyItem,  

                        &wBodyType,  

                        &bhBodyValue,  

                        &dwBodyValueLength ))  

{  

    /\* Unable to get body of response document \*/  

    goto Exit1;  

}  

  

if (status = NSFItemDeleteByBLOCKID( hRespNote, bhThisBodyItem ))  

{  

    /\* Unable to delete old body from response document\*/  

    goto Exit3;  

}  

  




 **See Also :**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFItemAppendByBLOCKID](NSFItemAppendByBLOCKID.md)**


**[NSFItemDelete](NSFItemDelete.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemInfoNext](NSFItemInfoNext.md)**



----------------------------------------------------------------------------------------------------------


 






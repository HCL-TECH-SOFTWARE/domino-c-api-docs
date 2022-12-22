




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



**NSFItemCopy** **- Copies an
item from one note to another by BLOCKID.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemCopy(**  

      NOTEHANDLE  note\_handle,  

      BLOCKID  item\_blockid**);**



**Description :**



Copies an
item identified by its BLOCKID from one in-memory copy of a note to another.    

  

 Note:  If the item copied is of type TYPE\_COMPOSITE (a rich text field) and
contains a doclink, the doclink is not preserved in the new copy of the item. 
The doclink symbol will be displayed, but Notes will not be able to locate the
document when the user attempts to activate the doclink.   

  

Also Note:  If the item copied already exists in the destination note, the
item's value in the destination note will not be replaced by the value of the
item in the source note.  Rather, the item will retain its original value, and
the new copy of the item will be appended to the destination note.  Therefore,
the destination note will have two items with the same name, and only the
original one will be visible. If the intent is to replace the value of an item
in the destination note with the value of the item in the source note, be sure
that the item is first deleted in the destination note before calling this
function.


 


**Parameters :**



Input :  

note\_handle  -  Handle of note to which item is to be copied.  

  

item\_blockid  -  The BLOCKID for  the item you wish to copy.  

  Note:  This is the BLOCKID of the item's header information ( the
item\_block\_id returned by NSFItemInfo() ), not the BLOCKID of the actual item
itself ( the value\_block\_id returned by NSFItemInfo() ).  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - upon successfully copying the item.  

  

ERR\_xxx - STATUS returned from a lower level Notes function called in the
action routine and passed back.  This value can be passed to OSLoadString to
obtain a text string that can be presented in a dialog box or log entry.  

  

  




 **See Also :**


**[NSFItemScan](NSFItemScan.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFItemInfoNext](NSFItemInfoNext.md)**


**[NSFItemDelete](NSFItemDelete.md)**



----------------------------------------------------------------------------------------------------------


 






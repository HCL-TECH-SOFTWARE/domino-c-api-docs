




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




**Initial Release 5.0**



**Function : Database**



**NSFItemDefExtGetEntry** **- Get an
item entry from the extended version of the database's Item Definition Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFItemDefExtGetEntry(**  

      ITEM\_DEFINITION\_TABLE\_LOCK \*ItemDefTableLock,  

      DWORD  ItemNum,  

      WORD \*ItemType,  

      WORD \*ItemLength,  

      char \*\*ItemName**);**



**Description :**



This
function gets an item entry from the extended version of the database's Item
Definition Table.  After first getting the handle to the
ITEM\_DEFINITION\_TABLE\_EXT structure with function NSFDbItemDefTableExt, locking
the structure with NSFItemDefExtLock, and getting the number of items in the
table with NSFItemDefExtEntries, use this function to get the Item Type, Item
Length, and Item Name of the specifed item number that was passed in.


 


**Parameters :**



Input :  

ItemDefTableLock  -  A pointer to an ITEM\_DEFINITION\_TABLE\_LOCK structure.  

  

  

ItemNum  -  The item number of the item entry.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Operation succeeded.  

  

  

  

ItemType  -  A pointer to the Item Type.  

  

ItemLength  -  A pointer to the Item Length.  Use this length when accessing
the Item Name which is not null terminated.  

  

ItemName  -  The address of a pointer to the Item Name.  This parameter is not
null terminated.  Use the Item Length and null terminate the character stream.  

  




 **See Also :**


**[ITEM\_DEFINITION\_EXT](ITEM_DEFINITION_EXT.md)**


**[ITEM\_DEFINITION\_TABLE\_EXT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D230ED443AC3962085256711004ED105)**


**[ITEM\_DEFINITION\_TABLE\_LOCK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/901659ECD32C4D5185256711004FD3A8)**


**[NSFDbItemDefTableExt](NSFDbItemDefTableExt.md)**


**[NSFItemDefExtEntries](NSFItemDefExtEntries.md)**


**[NSFItemDefExtFree](NSFItemDefExtFree.md)**


**[NSFItemDefExtLock](NSFItemDefExtLock.md)**


**[NSFItemDefExtUnlock](NSFItemDefExtUnlock.md)**



----------------------------------------------------------------------------------------------------------


 






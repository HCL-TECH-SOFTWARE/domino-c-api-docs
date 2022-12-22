




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



**NSFItemDefExtFree** **- Free the
contents of the extended version of the Item Definition Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFItemDefExtFree(**  

      ITEM\_DEFINITION\_TABLE\_EXT \*ItemDeftable**);**



**Description :**



This
function frees the contents of the extended version of the Item Definition
Table contained in the ITEM\_DEFINITION\_TABLE\_EXT structure and is used after
the function NSFItemDefExtUnlock has been called. 


 


**Parameters :**



Input :  

ItemDeftable  -  A pointer to the ITEM\_DEFINITION\_TABLE\_EXT structure.  Call
NSFDbItemDefTableExt to get a handle to this structure.   

  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[ITEM\_DEFINITION\_EXT](ITEM_DEFINITION_EXT.md)**


**[ITEM\_DEFINITION\_TABLE\_EXT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D230ED443AC3962085256711004ED105)**


**[ITEM\_DEFINITION\_TABLE\_LOCK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/901659ECD32C4D5185256711004FD3A8)**


**[NSFDbItemDefTableExt](NSFDbItemDefTableExt.md)**


**[NSFItemDefExtEntries](NSFItemDefExtEntries.md)**


**[NSFItemDefExtGetEntry](NSFItemDefExtGetEntry.md)**


**[NSFItemDefExtLock](NSFItemDefExtLock.md)**


**[NSFItemDefExtUnlock](NSFItemDefExtUnlock.md)**



----------------------------------------------------------------------------------------------------------


 






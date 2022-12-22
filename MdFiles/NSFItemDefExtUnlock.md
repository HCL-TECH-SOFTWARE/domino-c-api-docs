




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



**NSFItemDefExtUnlock** **- Unlocks
the contents of the extended version of the Item Definition Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFItemDefExtUnlock(**  

      ITEM\_DEFINITION\_TABLE\_EXT \*ItemDefTable,  

      ITEM\_DEFINITION\_TABLE\_LOCK \*ItemDefTableLock**);**



**Description :**



This
function unlocks the contents of the ITEM\_DEFINITION\_TABLE\_EXT structure, and
is used with the following NSF functions: NSFItemDefExtEntries,
NSFItemExtGetEntry, NSFItemDefExtLock, NSFItemDefExtFree.


 


**Parameters :**



Input :  

ItemDefTable  -  A pointer to the ITEM\_DEFINITION\_TABLE\_EXT structure.  Use
NSFDbItemDefTableExt to receive a handle to this structure.  

  

  

  

ItemDefTableLock  -  A pointer to an ITEM\_DEFINITION\_TABLE\_LOCK structure.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Operation succeeded.  

  

  

  




 **See Also :**


**[ITEM\_DEFINITION\_EXT](ITEM_DEFINITION_EXT.md)**


**[ITEM\_DEFINITION\_TABLE\_EXT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D230ED443AC3962085256711004ED105)**


**[NSFDbItemDefTableExt](NSFDbItemDefTableExt.md)**


**[NSFItemDefExtEntries](NSFItemDefExtEntries.md)**


**[NSFItemDefExtFree](NSFItemDefExtFree.md)**


**[NSFItemDefExtGetEntry](NSFItemDefExtGetEntry.md)**


**[NSFItemDefExtLock](NSFItemDefExtLock.md)**



----------------------------------------------------------------------------------------------------------


 






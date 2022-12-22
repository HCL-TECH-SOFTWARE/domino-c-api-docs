




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




**Initial Release 8.5.2**



**Function : Dir**



**DirEntryItemDelete** **- Delete an
item and all its values from an entry.** 


**----------------------------------------------------------------------------------------------------------**



**#include <direntry.h>**



STATUS
LNPUBLIC **DirEntryItemDelete(**  

      DIRENTRY  hEntry,  

      const char \*itemName**);**



**Description :**



Delete an
item and all its values from an entry. No error is returned if the item does
not exist. 


        Note
that this routine only affects the in-memory hEntry object. The changes are
written to the directory entry only after a subsequent DirEntryUpdate()
operation on the hEntry.


 


**Parameters :**



Input :  

hEntry  -  Handle to person entry whose item is to be deleted.  

  

itemName  -  Name of the item to be deleted.  

  




Output :  

(routine)  -  NOERROR   

ERR\_DIR\_NULL\_ARGUMENT   

If itemName is NULL.   

An ERR status on failure indicating the problem.  

  

  




 **See Also :**


**[DirEntryItemAdd](DirEntryItemAdd.md)**


**[DirEntryUpdate](DirEntryUpdate.md)**



----------------------------------------------------------------------------------------------------------


 






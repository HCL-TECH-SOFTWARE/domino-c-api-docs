




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




 


**Function : Text List Manipulation**



**ListGetSize** **- Returns
the size of a text list.**


**----------------------------------------------------------------------------------------------------------**



**#include <textlist.h>**



WORD
LNPUBLIC **ListGetSize(**  

      void far \*pList,  

      BOOL  fPrefixDataType**);**



**Description :**



This
function returns the size of the entire text list, including the Domino data
type item prefix (if present) + the size of the LIST header + the size of the
array containing offsets to the beginning of each entry, and the text of all
entries.


 


**Parameters :**



Input :  

pList  -  void far \* containing the address of the LIST.  

  

fPrefixDataType  -  BOOL indicating whether or not the text list is prefixed
with a WORD containing the Domino data type.  TRUE if list was obtained from an
existing note using NSFItemInfo and FALSE if the text list has just been
created using ListAllocate.  

  




Output :  

(routine)  -  Return contains the size of the specified text list in BYTEs  

  

  




 **Sample Usage :**


  

   list\_size = ListGetSize (list\_ptr, prefix\_flag);  

  




 **See Also :**


**[ListAddEntry](ListAddEntry.md)**


**[ListAddText](ListAddText.md)**


**[ListAllocate](ListAllocate.md)**


**[ListGetNumEntries](ListGetNumEntries.md)**


**[ListGetText](ListGetText.md)**


**[ListRemoveEntry](ListRemoveEntry.md)**



----------------------------------------------------------------------------------------------------------


 






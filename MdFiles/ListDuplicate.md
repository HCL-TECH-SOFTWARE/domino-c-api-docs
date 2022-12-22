




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




 


**Function : Text List Manipulation**



**ListDuplicate** **- Duplicate
a text list.**


**----------------------------------------------------------------------------------------------------------**



**#include <textlist.h>**



STATUS
LNPUBLIC **ListDuplicate(**  

      LIST far \*pInList,  

      BOOL  fNoteItem,  

      DHANDLE far \*phOutList**);**



**Description :**



This
function creates a duplicate copy of a text list.


 


**Parameters :**



Input :  

pInList  -  Pointer to the source text list that is to be duplicated.  

  

fNoteItem  -  Indicates whether or not the text list is prefixed with a WORD
containing the Domino data type.  TRUE if the list contains this prefix.  A
list obtained from NSFItemInfo() contains this prefix.  A list created with
ListAllocate does not contain this prefix.  

  




Output :  

(routine)  -  Return status from this call - indicates either success
(NOERROR), or one of the following:  

  

ERR\_MEMORY - Not enough global memory available for allocation.  

ERR\_SEGMENT\_TOO\_BIG - Requested size is greater than the maximum supported.  

  

  

phOutList  -  Handle to the duplicate copy of the source text list.  

  




 **See Also :**


**[ListAddText](ListAddText.md)**


**[ListAllocate](ListAllocate.md)**


**[ListGetNumEntries](ListGetNumEntries.md)**


**[ListGetSize](ListGetSize.md)**


**[ListRemoveAllEntries](ListRemoveAllEntries.md)**


**[ListRemoveEntry](ListRemoveEntry.md)**


**[ListAddEntry](ListAddEntry.md)**



----------------------------------------------------------------------------------------------------------


 






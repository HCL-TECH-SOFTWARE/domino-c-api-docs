




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




**Initial Release 4.5**



**Function : Note**



**NSFNoteFindMatchingItem** **- Find item
in one note that matches the same item in another.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteFindMatchingItem(**  

      NOTEHANDLE  hNote1,  

      BLOCKID  bhItem1,  

      NOTEHANDLE  hNote2,  

      DWORD  dwFlags,  

      BLOCKID \*retbhItem2**);**



**Description :**



This routine
returns the BLOCKID of an item in one note that matches the same item in
another note.  Two items match if the item name one matches the item name of
the other.  This function is useful for replication conflict handlers.


 


**Parameters :**



Input :  

hNote1  -  Handle of the first note.  

  

bhItem1  -  BLOCKID of the source item.  

  

hNote2  -  Handle of the second note.  

  

dwFlags  -  Reserved for future use.  Must be set to 0L.  

  




Output :  

(routine)  -  NOERROR - Successfully found a matching item.  

ERR\_ITEM\_NOT\_FOUND - A matching item was not found in the second note.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

retbhItem2  -  BLOCKID of the matching item.  

  




 **See Also :**


**[NSFItemInfo](NSFItemInfo.md)**


**[NSFNoteFindDivergenceTime](NSFNoteFindDivergenceTime.md)**


**[NSFItemGetModifiedTime](NSFItemGetModifiedTime.md)**


**[NSFItemGetModifiedTimeByBLOCKID](NSFItemGetModifiedTimeByBLOCKID.md)**



----------------------------------------------------------------------------------------------------------


 






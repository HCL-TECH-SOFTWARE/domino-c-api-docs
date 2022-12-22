




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



**Function : OS Memory**



**OSMemoryUnlock** **- Unlock a
memory object**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



BOOL
LNPUBLIC **OSMemoryUnlock(**  

      MEMHANDLE  handle**);**



**Description :**



This
function is used to unlock a memory object when it is no longer being
referenced.  It decrements the lock count on the object, and, if no one else is
using the object, makes it possible for the object to be moved or swapped.


 


This
function returns TRUE if the object was previously locked, FALSE if not.


 


**Parameters :**



Input :  

handle  -  The object handle.  

  




Output :  

(routine)  -  TRUE if the object was previously locked, FALSE if not.  

  

  




 **See Also :**


**[MEMHANDLE](MEMHANDLE.md)**


**[OSMemoryAllocate](OSMemoryAllocate.md)**


**[OSMemoryFree](OSMemoryFree.md)**


**[OSMemoryGetSize](OSMemoryGetSize.md)**


**[OSMemoryLock](OSMemoryLock.md)**


**[OSMemoryReallocate](OSMemoryReallocate.md)**



----------------------------------------------------------------------------------------------------------


 






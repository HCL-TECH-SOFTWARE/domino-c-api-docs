




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



**OSMemoryLock** **- Lock an
object in memory and return its address**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



void
far \* LNPUBLIC **OSMemoryLock(**  

      MEMHANDLE  handle**);**



**Description :**



This
function must be called before any memory object is referenced.  It takes the
MEMHANDLE returned from the OSMemoryAllocate function, locks the object into
memory to prevent swapping, and returns an address of the actual memory.  If
the object has been disarded, this function returns NULL.  This function can be
called more than once for the same object because a lock count is maintained. 


 


**Parameters :**



Input :  

handle  -  The MEMHANDLE returns from the OSMemoryAllocate function.  

  




Output :  

(routine)  -  None.  

  

  




 **See Also :**


**[MEMHANDLE](MEMHANDLE.md)**


**[OSMemoryAllocate](OSMemoryAllocate.md)**


**[OSMemoryFree](OSMemoryFree.md)**


**[OSMemoryGetSize](OSMemoryGetSize.md)**


**[OSMemoryReallocate](OSMemoryReallocate.md)**


**[OSMemoryUnlock](OSMemoryUnlock.md)**



----------------------------------------------------------------------------------------------------------


 






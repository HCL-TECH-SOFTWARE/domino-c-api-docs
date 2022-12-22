




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



**OSMemoryFree** **-
Deallocate memory**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



void
LNPUBLIC **OSMemoryFree(**  

      MEMHANDLE  handle**);**



**Description :**



OSMemoryFree
is used to deallocate a block  or memory using the handle MEMHANDLE returned
from OSMemoryAllocate.


 


**Parameters :**



Input :  

handle  -  Object handle returned by the OSMemoryAllocate function.  If the
handle is NULLMEMHANDLE, no error will be reported.  

  




 


 **See Also :**


**[MEMHANDLE](MEMHANDLE.md)**


**[OSMemoryAllocate](OSMemoryAllocate.md)**


**[OSMemoryGetSize](OSMemoryGetSize.md)**


**[OSMemoryLock](OSMemoryLock.md)**


**[OSMemoryReallocate](OSMemoryReallocate.md)**


**[OSMemoryUnlock](OSMemoryUnlock.md)**


**[OSMemRealloc](OSMemRealloc.md)**



----------------------------------------------------------------------------------------------------------


 






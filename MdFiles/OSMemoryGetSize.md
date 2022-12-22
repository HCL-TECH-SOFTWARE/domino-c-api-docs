




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



**OSMemoryGetSize** **- Get size
of an MEMHANDLE object**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



DWORD
LNPUBLIC **OSMemoryGetSize(**  

      MEMHANDLE  handle**);**



**Description :**



This
function can be used to obtain the size of an object in bytes.  It returns the
amount of space actually available, not the size originally requested.


 


**Parameters :**



Input :  

handle  -  Object handle  

  




Output :  

(routine)  -  The address of a DWORD in which the MEMHANDLE object size in
bytes will be returned.  

  

  




 **See Also :**


**[MEMHANDLE](MEMHANDLE.md)**


**[OSMemoryAllocate](OSMemoryAllocate.md)**


**[OSMemoryFree](OSMemoryFree.md)**


**[OSMemoryLock](OSMemoryLock.md)**


**[OSMemoryReallocate](OSMemoryReallocate.md)**


**[OSMemoryUnlock](OSMemoryUnlock.md)**



----------------------------------------------------------------------------------------------------------


 






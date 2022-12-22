




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



**OSMemoryReallocate** **- Change
the allocated size of an object**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



STATUS
LNPUBLIC **OSMemoryReallocate(**  

      MEMHANDLE  handle,  

      DWORD  size**);**



**Description :**



Use this
function to increase or decrease the allocated size of a memory object.  If the
size is increased, a new block may be allocated, but the old contents will be
copied to the new block.  Reallocations are allowed while the block is locked,
but the caller MUST refresh all pointers to the block since it is extremely
likely that the block will have been moved after the reallocation.


 


Note - This
function can resize only those buffers originally allocated using the
MEM\_GROWABLE flag.  See MEM\_xxx for details.


 


**Parameters :**



Input :  

handle  -  Handle to the memory object  

  

size  -  New size in bytes  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[MEMHANDLE](MEMHANDLE.md)**


**[MEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5B03D1FBAAB6E7A085255F470053A741)**


**[OSMemAlloc](OSMemAlloc.md)**


**[OSMemoryAllocate](OSMemoryAllocate.md)**


**[OSMemoryFree](OSMemoryFree.md)**


**[OSMemoryGetSize](OSMemoryGetSize.md)**


**[OSMemoryLock](OSMemoryLock.md)**


**[OSMemoryUnlock](OSMemoryUnlock.md)**


**[OSMemRealloc](OSMemRealloc.md)**



----------------------------------------------------------------------------------------------------------


 






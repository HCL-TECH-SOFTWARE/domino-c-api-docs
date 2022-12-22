




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




 


**Function : OS Memory**



**OSMemRealloc** **- Change
the size of an existing Domino memory object.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



STATUS
LNPUBLIC **OSMemRealloc(**  

      DHANDLE  Handle,  

      DWORD  NewSize**);**



**Description :**



OSMemRealloc
is used to increase or decrease the allocated size of a Domino memory object. 
If the size is increased, then a new block may be allocated, but the block's
contents will be copied to the new block. Reallocations are allowed while the
block is locked, but the caller MUST refresh all pointers (using OSLockObject)
to the block, since it is extremely likely that the block will have moved after
the reallocation.  

  

If you call this routine with a HANDLE that is invalid or out of range, Domino
or Notes will panic and halt.


 


Note - This
function can resize only those buffers originally allocated using the
MEM\_GROWABLE flag.  See MEM\_xxx for details.


 


**Parameters :**



Input :  

Handle  -  Handle for the memory object to be reallocated.  

  

NewSize  -  The requested new size of the object, in bytes.  

  




Output :  

(routine)  -  Completion status of the operation, NOERROR if successful.  If
not successful, then status is one of:  

  

ERR\_MEMORY - Not enough global memory available for allocation.  

  

ERR\_SEGMENT\_TOO\_BIG - Requested size is greater than the maximum supported
(60K).  

  

  




 **See Also :**


**[MEM\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/5B03D1FBAAB6E7A085255F470053A741)**


**[OSLockObject](OSLockObject.md)**


**[OSMemAlloc](OSMemAlloc.md)**


**[OSMemFree](OSMemFree.md)**


**[OSMemGetSize](OSMemGetSize.md)**


**[OSMemoryAllocate](OSMemoryAllocate.md)**


**[OSMemoryReallocate](OSMemoryReallocate.md)**


**[OSUnlockObject](OSUnlockObject.md)**



----------------------------------------------------------------------------------------------------------


 






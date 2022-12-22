




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



**OSMemoryAllocate** **- Allocate
a block of memory - returns MEMHANDLE**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



STATUS
LNPUBLIC **OSMemoryAllocate(**  

      DWORD  dwtype,  

      DWORD  size,  

      MEMHANDLE \*rethandle**);**



**Description :**



 It is
advisable to use the OSMemoryAllocate function, instead of the OSMemAlloc
function, at the places where Domino or Notes takes a pointer to the data, and
you choose to use the Domino memory allocator to allocate storage for that
data. 


 


       This
function returns MEMHANDLE which has no relationship with the datatype HANDLE.  A HANDLE is
a WORD on all platforms except Win32.  On Win32, it is a DWORD, but the HANDLE
is still restricted to 16 bits of actual usage, which limits an application to
64K HANDLEs.  Due to a Domino algorithm change, OSMemoryAllocate returns DWORD
MEMHANDLEs which free the constraint posed by the size of the HANDLE datatype. 


 


       
OSMemoryAllocate allocates a block of memory and returns a MEMHANDLE handle to
the caller.  The memory should be locked with the function OSMemoryLock, and
unlocked and released using the function OSMemoryUnlock and OSMemoryFree
respectively.  

  




        This
function guarantees that if the memory allocation fails, the returned handle
will be NULLMEMHANDLE.  Unlike OSMemAlloc, this function allocates 0 byte if
that is requested, instead of returning a NULLHANDLE with success.


 


 


**Parameters :**



Input :  

dwtype  -  Type of memory block to be allocated.  Use 0 to allocate a block of
memory for the application's use.  To allocate memory that can be shared
between processes, use MEM\_SHARE.  For allocated memory that may be reallocated
to a different size, use MEM\_GROWABLE.  See Symbolic Value, MEM\_xxx for more
information.  

  

size  -  Size needed in bytes.  The maximum size is MAXONESEGSIZE.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

rethandle  -  MEMHANDLE to newly allocated object  

  




 **See Also :**


**[MEMHANDLE](MEMHANDLE.md)**


**[MEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5B03D1FBAAB6E7A085255F470053A741)**


**[OSMemAlloc](OSMemAlloc.md)**


**[OSMemoryFree](OSMemoryFree.md)**


**[OSMemoryGetSize](OSMemoryGetSize.md)**


**[OSMemoryLock](OSMemoryLock.md)**


**[OSMemoryReallocate](OSMemoryReallocate.md)**


**[OSMemoryUnlock](OSMemoryUnlock.md)**


**[OSMemRealloc](OSMemRealloc.md)**



----------------------------------------------------------------------------------------------------------


 






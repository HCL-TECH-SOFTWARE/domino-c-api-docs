




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




 


**Function : OS Memory**



**OSMemAlloc** **- Allocate
a block of memory from the Domino or Notes system.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



STATUS
LNPUBLIC **OSMemAlloc(**  

      WORD  BlkType,  

      DWORD  dwSize,  

      DHANDLE far \*retHandle**);**



**Description :**



OSMemAlloc
allocates a block of memory and returns a handle to the caller.  The handle can
be converted to a memory pointer by calling OSLockObject.  

  

Under normal circumstances, memory allocated using OSMemAlloc must be released
using the function OSMemFree.  (For the exceptions, please see the discussion
under OSMemFree.)  

  

This function is only necessary when allocating memory for which you need a
handle to pass to C API functions.  If you need to allocate memory that does
not require a handle, you can use the standard C function malloc() instead.


 


**Parameters :**



Input :  

BlkType  -  Type of memory block to be allocated.  Use 0 to allocate a block of
memory for the application's use.  To allocate memory that can be shared
between processes, use MEM\_SHARE.  For allocated memory that may be reallocated
to a different size, use MEM\_GROWABLE.  See Symbolic Value, MEM\_xxx for more
information.  

  

dwSize  -  Requested size of memory block in bytes.  The limit is MAXDWORD.  If
the requested size is 0 bytes, NULLHANDLE will be returned rather than a new
handle.  

  




Output :  

(routine)  -  Error status code for allocate operation.  NOERROR if successful,
or if not, one of the following:  

  

ERR\_MEMORY - Not enough global memory available for allocation.  

ERR\_SEGMENT\_TOO\_BIG - Requested size is greater than the maximum supported.  

  

  

retHandle  -  The address of a HANDLE in which the handle to the allocated
memory object is returned.  Guaranteed to be NULLHANDLE if allocate failed.  If
the requested size is 0 bytes, NULLHANDLE will be returned rather than a new
handle.  

  




 **Sample Usage :**


      /\* Allocate a
Domino or Notes memory object used in building an ITEM  \*/  

      /\* value                                                    \*/  

  

       if (usError = OSMemAlloc(0, dwTextLen, &ImpTextBID.pool))  

           goto Exit;  

       else  

           wCleanUp |= FREE\_IMPTEXTBID;  

  




 **See Also :**


**[MEM\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/5B03D1FBAAB6E7A085255F470053A741)**


**[OSLockObject](OSLockObject.md)**


**[OSMemFree](OSMemFree.md)**


**[OSMemoryAllocate](OSMemoryAllocate.md)**


**[OSMemoryReallocate](OSMemoryReallocate.md)**


**[OSMemRealloc](OSMemRealloc.md)**


**[OSUnlockObject](OSUnlockObject.md)**



----------------------------------------------------------------------------------------------------------


 






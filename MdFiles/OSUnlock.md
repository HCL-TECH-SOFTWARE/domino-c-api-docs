




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



**OSUnlock** **- Unlock a
Domino memory object.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



BOOL
LNPUBLIC **OSUnlock(**  

      HANDLE  handle**);**



**Description :**



OSUnlock is
called to indicate that an application no longer needs physical access to the
specified object.  The lock count on the object is then decremented, and the
calling application must then assume that the physical address for that object
is no longer valid.  An object must be fully unlocked (reference count = 0) before
it can be deallocated with OSMemFree.  

  

It is recommended that once an application is temporarily done using a memory
object, it unlock the handle associated with that object, allowing the object
to be moved by the memory manager.  This will prevent the creation of
"islands" that prevent efficient allocation/reallocation of memory. 
Islands lead to poor performance or insufficient memory errors.  When you
require a real address, just call OSLockObject and a new pointer value will be
returned.  

  

Most APIs that require a handle as an argument, require that the handle be
unlocked.  

  

An application can lock the same object more than once -- a lock reference
count is maintained.  It is not actually moveable until all locks are released
(reference count = 0).  

  

Calling this routine with a HANDLE that is invalid or out of range will result
in a Notes PANIC halt .  

  

Note - this routine is implemented as a macro that just calls OSUnlockObject
with the same argument.  It is provided merely to facilitate symmetry with OSLock:  

#define OSUnlock(handle) OSUnlockObject(handle)


 


**Parameters :**



Input :  

handle  -  Handle for the  object to be unlocked.  

  




Output :  

(routine)  -  Always returns TRUE.  There is no need to check the return value.  

  

  




 **Sample Usage :**


  

   /\* Cleanup memory \*/  

  

   if (wCleanUp & UNLOCK\_HCDBUF)  

       OSUnlock(hCDBuf);  

  




 **See Also :**


**[OSLock](OSLock.md)**


**[OSUnlockBlock](OSUnlockBlock.md)**


**[OSUnlockObject](OSUnlockObject.md)**



----------------------------------------------------------------------------------------------------------


 






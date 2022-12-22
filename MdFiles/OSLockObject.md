




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



**OSLockObject** **- Lock an
object in memory and return its address.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



void
far \* LNPUBLIC **OSLockObject(**  

      DHANDLE  Handle**);**



**Description :**



OSLockObject
locks a memory object (preventing its physical relocation) and returns a
pointer to its locked address in memory.  This routine must be called before
any memory object is referenced.  Once locked, the application can freely use
the pointer to access its contents.  

  

It is recommended that once an application is temporarily done using a memory
object, it unlock the object freeing up the memory for swapping to disk. 
OSLockObject can then be used for subsequent access, and the new pointer value
must then be used for access.  

  

An application can lock the same object more than once -- a lock reference
count is maintained.  It is not actually moveable until all locks are released
(reference count = 0).  

  

Calling this routine with a HANDLE that is invalid or out of range will result
in a Notes PANIC halt .  

  




 


**Parameters :**



Input :  

Handle  -  Handle for the object to be locked.   

  




Output :  

(routine)  -  Pointer to the locked object.  

  

  




 **Sample Usage :**


  /\* Get the physical
address associated with the handle \*/  

  

   pImpText = OSLockObject(ImpTextBID.pool);  

   wCleanUp |= UNLOCK\_IMPTEXTBID;  

  




 **See Also :**


**[OSUnlockObject](OSUnlockObject.md)**


**[OSMemAlloc](OSMemAlloc.md)**


**[OSMemFree](OSMemFree.md)**



----------------------------------------------------------------------------------------------------------


 






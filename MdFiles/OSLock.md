




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



**OSLock** **- Lock an
object and return a type-cast pointer to it.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmem.h>**



<blocktype>
far \* **OSLock(**  

      <typedef>  blocktype,  

      HANDLE  hObject**);**



**Description :**



OSLock locks
a memory object and returns a pointer to its locked address in memory.  The
pointer is type cast as given by the first argument.  This routine must be
called before any memory object is referenced.  Once locked, the application
can use the pointer to access its contents.  

  




If the block
of memory contains data that varies in size, such as a text list, the memory
may be relocated unexpectedly.  To avoid this, the block should only be locked
while accessing the contents, and should be unlocked immediately after.  It is
recommended that once an application is temporarily done using a memory object,
it unlock the object freeing up the memory for swapping to disk.  OSLock can
then be used for subsequent access, and the new pointer value must then be used
for access.  

  

An application can lock the same object more than once -- a lock reference
count is maintained.  

  

Calling this routine with a HANDLE that is invalid or out of range will result
in a Notes PANIC halt .  

  

Note: this routine is implemented as a macro around OSLockObject:  

  

  

#define OSLock(blocktype,handle) ((blocktype far \*) OSLockObject(handle))


 


**Parameters :**



Input :  

blocktype  -  This argument should be a C language data type, either a native
type or a TYPEDEFed one.  The returned pointer will be type-cast to point to
data of this type.  

  

hObject  -  Handle for the object to be locked.   

  




Output :  

(routine)  -  Pointer to a data item of the specified type.  

  

  




 **Sample Usage :**


  /\* Obtain physical
address of output ITEM value returned above. \*/  

  

   pCDBuf = OSLock(char, hCDBuf);  

   wCleanUp |= UNLOCK\_HCDBUF;  

  

  




 **See Also :**


**[OSLockBlock](OSLockBlock.md)**


**[OSLockObject](OSLockObject.md)**


**[OSUnlock](OSUnlock.md)**


**[OSUnlockBlock](OSUnlockBlock.md)**


**[OSUnlockObject](OSUnlockObject.md)**



----------------------------------------------------------------------------------------------------------


 






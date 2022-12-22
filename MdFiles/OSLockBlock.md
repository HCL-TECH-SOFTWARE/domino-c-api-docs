




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




 


**Function : OS Blocks**



**OSLockBlock** **- Locks
BLOCKID and returns typed pointer to the data.**


**----------------------------------------------------------------------------------------------------------**



**#include <pool.h>**



<type>
far \* **OSLockBlock(**  

      <typedef>  type,  

      BLOCKID  blockid**);**



**Description :**



OSLockBlock
locks the data associated with a BLOCKID in memory and returns a type cast
pointer to its locked address in memory.  This routine must be called before
any BLOCKID data can be referenced.  Once locked, the application can use the
pointer to access the data.  The BLOCKID must be unlocked by the application
using OSUnlockBlock before any corresponding Domino data entities (e.g. NSF,
note, etc) can be freed (e.g. closed).


 


If the block
of memory contains data that varies in size, such as a text list, the memory
may be relocated unexpectedly.  To avoid this, the block should only be locked
while accessing the contents, and should be unlocked immediately after.  

  

Calling this routine with a BLOCKID that is invalid or out of range will result
in a Notes PANIC halt!  

  

Note -- this function is actually implemented as a macro:  

   

  

#define OSLockBlock(type,blockid) \  

 ((type far \*)(OSLock(char,(blockid).pool) + (blockid).block))


 


**Parameters :**



Input :  

type  -  The data type of the data associated with the given BLOCKID.  

  

blockid  -  The BLOCKID to be locked.  

  




Output :  

(routine)  -  Pointer to a data item of the specified type.  

  

  




 **Sample Usage :**


  

       pTmpCD = OSLockBlock(char, bidTmpCD);  

       CleanUp\_State += UNLOCK\_EXPCDBID;  

  




 **See Also :**


**[ISNULLBLOCKID](ISNULLBLOCKID.md)**


**[OSUnlockBlock](OSUnlockBlock.md)**


**[OSLock](OSLock.md)**


**[OSUnlock](OSUnlock.md)**



----------------------------------------------------------------------------------------------------------


 






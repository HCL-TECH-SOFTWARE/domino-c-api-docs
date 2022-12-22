




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



**OSUnlockBlock** **- Unlock a
BLOCKID memory block.**


**----------------------------------------------------------------------------------------------------------**



**#include <pool.h>**



BOOL
LNPUBLIC **OSUnlockBlock(**  

      BLOCKID  blockid**);**



**Description :**



OSUnlockBlock
is called to indicate that an application no longer needs physical access to
the specified BLOCKID memory object. The lock count on the block is then
decremented, and the calling application must then assume that the physical
address for that object is no longer valid.  A BLOCKID must be fully unlocked (reference
count = 0) before it can be deallocated.  Note that in the case of BLOCKIDs,
operations such as closing Notes or databases require the corresponding
BLOCKIDs to be fully unlocked.  

  

Calling this routine with a BLOCKID that is invalid or out of range will result
in a Notes PANIC halt .  

  

Note -- this function is actually implemented as a macro:  

#define OSUnlockBlock(blockid) \  

 OSUnlockObject((blockid).pool)


 


**Parameters :**



Input :  

blockid  -  BLOCKID for the block to be unlocked.  

  




Output :  

(routine)  -  Always returns TRUE.  

  

  




 **Sample Usage :**


  

       /\* Unlock the CD Temp Buffer \*/  

       if (CleanUp\_State & UNLOCK\_EXPCDBID)  

           OSUnlockBlock(bidTmpCD);  

  




 **See Also :**


**[OSLock](OSLock.md)**


**[OSLockBlock](OSLockBlock.md)**


**[OSLockObject](OSLockObject.md)**


**[OSUnlock](OSUnlock.md)**


**[OSUnlockObject](OSUnlockObject.md)**



----------------------------------------------------------------------------------------------------------


 






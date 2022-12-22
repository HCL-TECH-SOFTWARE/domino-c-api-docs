




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




 


**Function : OS Blocks**



**OSSwitchBlock** **- Switch
pointer from one memory block to another.**


**----------------------------------------------------------------------------------------------------------**



**#include <pool.h>**



void **OSSwitchBlock(**  

      void far \*ptr,  

      BLOCKID  thisid,  

      BLOCKID  nextid**);**



**Description :**



OSSwitchBlock
operates on two BLOCKID structures.  The first one is UnLocked, and then the
second one is Locked.  Then the specified pointer is loaded with the memory
address associated with the second BLOCKID.  This function is actually
implemented as a macro.  It provides a transparent way for an application to
switch between two BLOCKIDs without requiring knowledge of BLOCKID
organization.


 


Note -- this
function is actually implemented as a macro:


#define
OSSwitchBlock(ptr,thisid,nextid) \


{ \


            if
((thisid).pool != (nextid).pool) \


            {
\


                        if
((thisid).pool != NULLHANDLE) \


                                    OSUnlockBlock((thisid));
\


                        ptr
= OSLockBlock(void,(nextid)); \


            }
\


            else
\


            {
\


                        register
char \*\*pptr = (char \*\*) &(ptr); \


                        \*pptr
= \*pptr + (LONG)((nextid).block - (thisid).block); \


            }
\


            (thisid)
= (nextid); \


}


 


**Parameters :**



Input :  

  

thisid  -  BLOCKID for the previous block (the one to be unlocked).  Note that
this BLOCKID is overwritten by the nextid argument;  if the user has allocated
the block identified by thisid, the BLOCKID must be preserved elsewhere.  

  

nextid  -  BLOCKID for the new block (the block that will be locked and whose
address is to be returned by the routine itself).  

  




Output :  

(routine)  -  None.  

  

  

ptr  -  Pointer to be loaded with a data pointer associated with the new
BLOCKID.  Because this function is actually a macro, this argument should be
passed in as the pointer itself, rather than a pointer to the pointer.  (ex:
char far \* pData;  use pData rather than &pData).  

  




 **See Also :**


**[OSLockBlock](OSLockBlock.md)**


**[OSUnlockBlock](OSUnlockBlock.md)**



----------------------------------------------------------------------------------------------------------


 






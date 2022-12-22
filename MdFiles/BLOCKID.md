




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




 


**Data Type : IDs**



**BLOCKID** **-** Domino
memory "block".


**----------------------------------------------------------------------------------------------------------**



**#include
<pool.h>**



**Definition :**



typedef struct {  

   DHANDLE pool;  /\* pool handle \*/  

   BLOCK  block; /\* block handle \*/  

 } BLOCKID;


 


**Description :**



A BLOCKID is
a structure used by Domino to manage memory.  Some API functions (e.g.
NSFItemInfo) return data in memory blocks. Others API functions (e.g.
NSFItemAppendByBLOCKID) take input data in memory blocks.   

  

A memory block consists of a "pool" subdivided in to
"blocks". The pool member of a BLOCKID stores the handle to an
allocated area of memory. The block member of a BLOCKID stores an offset to
some position in the pool.  

  

Take the following steps to store data in a memory block before passing the
BLOCKID as input to a C API function:  

  

1)  Declare a variable of type BLOCKID  

2)  Call OSMemAlloc to obtain a handle to an area of  memory.  

3)  Store the handle in the pool member of the BLOCKID  

4)  Set the block member of the BLOCKID to NULLBLOCK  

5)  Call OSLockBlock to obtain a pointer to the BLOCKID data  

6)  Write data to the memory using the pointer  

7)  Call OSUnlockBlock to release the BLOCKID before passing the BLOCKID as
input to a C API function.  

  

Take the following steps to read the data returned from a C API function in a
memory block:  

  

1)  Declare a data item of type BLOCKID  

2)  Call the appropriate C API function, passing a pointer to the BLOCKID  

3)  Call OSLockBlock to create a pointer to the BLOCKID data  

4)  Process the data using the created pointer  

5)  Call OSUnlockBlock to release the BLOCKID.


 **Sample Usage :**


  

    OBJECT\_DESCRIPTOR   objLeftToDo;  

    BLOCKID     bidLeftToDo;  

    DWORD       dwItemSize;  

    void       \*p;  

    WORD        w;  

  

    /\*... steps missing ...\*/  

  

    dwItemSize = (DWORD) (sizeof(WORD) + ODSLength(\_OBJECT\_DESCRIPTOR));  

  

    if (error = OSMemAlloc(0, dwItemSize, &(bidLeftToDo.pool)))  

    {  

        printf ("Error: unable to allocate %ld bytes for LeftToDo
item.\n",  

                                    dwItemSize);  

        goto Exit1;  

    }  

  

    bidLeftToDo.block = NULLBLOCK;  

  

    p = OSLockBlock(void, bidLeftToDo);  

    w = TYPE\_OBJECT;  

    memmove(p, &w, sizeof(WORD));  

    p += sizeof(WORD);  

    ODSWriteMemory(&p, \_OBJECT\_DESCRIPTOR, &objLeftToDo, 1);  

    OSUnlockBlock(bidLeftToDo);  

  

    if (error = NSFItemAppendObject(hMacro, ITEM\_SUMMARY,  

                            FILTER\_LEFTTODO\_ITEM,   

                            sizeof(FILTER\_LEFTTODO\_ITEM)-1,  

                            bidLeftToDo,   

                            dwItemSize,   

                            TRUE))  

    {  

        printf ("Error: unable to append %s item.\n",
FILTER\_LEFTTODO\_ITEM);  

        OSMemFree(bidLeftToDo.pool);  

        goto Exit1;  

    }


 **See Also :**


**[OSLockBlock](OSLockBlock.md)**


**[OSUnlockBlock](OSUnlockBlock.md)**


**[OSSwitchBlock](OSSwitchBlock.md)**


**[ISNULLBLOCKID](ISNULLBLOCKID.md)**



----------------------------------------------------------------------------------------------------------


 






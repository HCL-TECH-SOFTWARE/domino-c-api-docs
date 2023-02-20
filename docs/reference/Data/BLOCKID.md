##### Data Type : IDs
##### BLOCKID - Domino memory "block".
---
```
#include <pool.h>
```
**Description :**

A BLOCKID is a structure used by Domino to manage memory.  Some API functions 
(e.g. NSFItemInfo) return data in memory blocks. Others API functions (e.g. 
NSFItemAppendByBLOCKID) take input data in memory blocks. 

A memory block consists of a "pool" subdivided in to "blocks". The pool member 
of a BLOCKID stores the handle to an allocated area of memory. The block member 
of a BLOCKID stores an offset to some position in the pool.

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
```

    OBJECT_DESCRIPTOR   objLeftToDo;
    BLOCKID     bidLeftToDo;
    DWORD       dwItemSize;
    void       *p;
    WORD        w;

    /*... steps missing ...*/

    dwItemSize = (DWORD) (sizeof(WORD) + ODSLength(_OBJECT_DESCRIPTOR));

    if (error = OSMemAlloc(0, dwItemSize, &(bidLeftToDo.pool)))
    {
        printf ("Error: unable to allocate %ld bytes for LeftToDo item.\n",
                                    dwItemSize);
        goto Exit1;
    }

    bidLeftToDo.block = NULLBLOCK;

    p = OSLockBlock(void, bidLeftToDo);
    w = TYPE_OBJECT;
    memmove(p, &w, sizeof(WORD));
    p += sizeof(WORD);
    ODSWriteMemory(&p, _OBJECT_DESCRIPTOR, &objLeftToDo, 1);
    OSUnlockBlock(bidLeftToDo);

    if (error = NSFItemAppendObject(hMacro, ITEM_SUMMARY,
                            FILTER_LEFTTODO_ITEM, 
                            sizeof(FILTER_LEFTTODO_ITEM)-1,
                            bidLeftToDo, 
                            dwItemSize, 
                            TRUE))
    {
        printf ("Error: unable to append %s item.\n", FILTER_LEFTTODO_ITEM);
        OSMemFree(bidLeftToDo.pool);
        goto Exit1;
    }
```
**See Also :**
[OSLockBlock](/reference/Func/OSLockBlock)
[OSUnlockBlock](/reference/Func/OSUnlockBlock)
[OSSwitchBlock](/reference/Func/OSSwitchBlock)
[ISNULLBLOCKID](/reference/Func/ISNULLBLOCKID)
---

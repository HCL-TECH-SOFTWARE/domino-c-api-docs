##### Data Type : Item (Field) Information
##### OBJECT_DESCRIPTOR - Object item strucure
---
```
#include <nsfdata.h>
```
**Description :**

All items (fields) of type TYPE_OBJECT contain this data structure.

Domino and Notes use objects to store data that is not rendered on the screen 
by the Notes editor. Examples include file attachments ($FILE fields), help 
indexes, and macro left-to-do lists ($LeftToDo fields). 

The ObjectType member stores the type of the object. The RRV member stores the 
ID that identifies the object in the database.

An object consists of two parts: the object itself in the database, and the 
object item in the note. The object itself is stored separately from the note 
and is identified by it's Object ID (the RRV). The object item is a structure 
of type OBJECT_DESCRIPTOR that resides in the note. The RRV member of the 
OBJECT_DESCRIPTOR identifies the object itself in the Domino database file. 

Possible object types include OBJECT_FILE and OBJECT_FILTER_LEFTTODO. See 
OBJECT_xxx for a list of all object types. For file attachments ($FILE fields) 
the ObjectType member is OBJECT_FILE. In this case, the OBJECT_DESCRIPTOR 
serves as the header for the larger FILEOBJECT structure.

To attach a file to a note, use NSFNoteAttachFile. To add a different type of 
object to a note, use NSFDbAllocObject() and NSFItemAppendObject().

**Sample Usage :**
```
    OBJECT_DESCRIPTOR   objLeftToDo;
    OBJECT_DESCRIPTOR  *pobj;
    BLOCKID     bidLeftToDo;  

    /* Assume Windows platform. Code below must
       be modified to convert the OBJECT_DESCRIPTOR to
       Domino Canonical Format in order to be portable.
     */

    objLeftToDo.ObjectType = OBJECT_FILTER_LEFTTODO ;
    objLeftToDo.RRV = dwObjectID;

    dwItemSize = (DWORD) (sizeof(WORD) + sizeof(OBJECT_DESCRIPTOR));

    if (error = OSMemAlloc(0, dwItemSize, &(bidLeftToDo.pool)))
    {
        printf ("Error: unable to allocate %ld bytes for LeftToDo item.\n",
                                    dwItemSize);
        NSFDbFreeObject(hDb, dwObjectID);
        goto Exit1;
    }

    bidLeftToDo.block = NULLHANDLE;

    pw = OSLockBlock(WORD, bidLeftToDo);
    *pw = TYPE_OBJECT;
    pw++;
    pobj = (OBJECT_DESCRIPTOR*)pw;
    *pobj = objLeftToDo;
    OSUnlockBlock(bidLeftToDo);

    if (error = NSFItemAppendObject(hMacro, ITEM_SUMMARY,
                            FILTER_LEFTTODO_ITEM, 
                            sizeof(FILTER_LEFTTODO_ITEM)-1,
                            bidLeftToDo, 
                            dwItemSize, 
                            TRUE))      /* Notes will deallocate memory */
    {
        printf ("Error: unable to append %s item.\n", FILTER_LEFTTODO_ITEM);
        OSMemFree(bidLeftToDo.pool);
        goto Exit1;
    }

```
**See Also :**
[FILEOBJECT](/domino-c-api-docs/reference/Data/FILEOBJECT)
[NSFItemAppendObject](/domino-c-api-docs/reference/Func/NSFItemAppendObject)
[NSFNoteAttachFile](/domino-c-api-docs/reference/Func/NSFNoteAttachFile)
[OBJECT_xxx](/domino-c-api-docs/reference/Symb/OBJECT_xxx)
---

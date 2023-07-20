##### Symbolic Value : Field
##### OBJECT_xxx - Object types used in OBJECT_DESCRIPTOR structure
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	OBJECT_NO_COPY	  -  A flag that may be bitwise OR-ed with the object type value. Prevents object from being copied when note is copied.

	OBJECT_PRESERVE	  -  A flag that may be bitwise OR-ed with the object type to prevent Domino or Notes from deleting the object when a note that refers to the object is deleted.

	OBJECT_PUBLIC	  -  Public access object being allocated.

	OBJECT_FILE	  -  File Attachment.

	OBJECT_FILTER_LEFTTODO	  -  The $LeftToDo object associated with a macro: has an ID table of docs not yet processed by the macro.

	OBJECT_ASSIST_RUNDATA	  -  Assistant run data object.

	OBJECT_UNKNOWN	  -  Unknown object type. Specify in NSFDbGetObjectSize() if you do not know the object type.


**Description :**

These values reside in the ObjectType member of the OBJECT_DESCRIPTOR structure. They are also specified in the ObjectType argument to the function NSFDbGetObjectSize(). The object type characterizes what sort of information resides in an object.<br>
<br>
All items of type TYPE_OBJECT have an OBJECT_DESCRIPTOR structure. The ObjectType member of the OBJECT_DESCRIPTOR structure differentiates between different types of objects. <br>
<br>
File attachments are items of type TYPE_OBJECT with field name $FILE and object type OBJECT_FILE. <br>
<br>
Macro left-to-do lists are items of type TYPE_OBJECT with field name $LeftToDo and object type OBJECT_FILTER_LEFTTODO. <br>
<br>
For either of the above object types, you may specify OBJECT_UNKNOWN as the ObjectType argument to NSFDbGetObjectSize() and obtain the correct result.<br>
<br>
OBJECT_NO_COPY and OBJECT_PRESERVE flags may be bitwise OR-ed with certain object types. These flags affect  how Domino or Notes handles objects when copying or updating a note containing the object. Normally these flags are not used with either of the above object types.


**Sample Usage :**
```

    DWORD       dwObjectID;
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
[OBJECT_DESCRIPTOR](/domino-c-api-docs/reference/Data/OBJECT_DESCRIPTOR)
[FILEOBJECT](/domino-c-api-docs/reference/Data/FILEOBJECT)
[NSFNoteAttachFile](/domino-c-api-docs/reference/Func/NSFNoteAttachFile)
[NSFItemAppendObject](/domino-c-api-docs/reference/Func/NSFItemAppendObject)
[NSFDbGetObjectSize](/domino-c-api-docs/reference/Func/NSFDbGetObjectSize)
---

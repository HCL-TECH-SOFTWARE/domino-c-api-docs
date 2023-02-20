##### Function : Database
##### NSFDbReallocObject - Re-allocate an object to change its size.
---
```
#include <nsfobjec.h>
STATUS LNPUBLIC NSFDbReallocObject(

	DBHANDLE  hDB,
	DWORD  ObjectID,
	DWORD  NewSize);
```
**Description :**

This function reallocates an object in the database file to accommodate a 
different size. The object ID (the RRV) remains the same even after the object 
is reallocated.

Use this function when updating an object in a database if the updated size of 
the object is greater than the original object. Use NSFDbGetObjectSize to 
obtain the size of an object initially.

Domino and Notes use objects and object items to store data that is not 
rendered on the screen by the Notes editor. Examples include file attachments 
($FILE fields), help indexes, and macro left-to-do lists ($LeftToDo). Note that 
for file attachments, NSFNoteAttachFile and NSFNoteDetatchFile are simpler to 
use than NSFDbReadObject and NSFDbWriteObject.

**Parameters :**
Input :
hDB  -  handle to the open database in which the object resides

ObjectID  -  The object ID (the RRV) that identifies the location of the object in the database file. Obtain this ID originally from NSFDbAllocateObject. This ID is stored in the RRV member of the OBJECT_DESCRIPTOR structure, which is stored in note fields of type TYPE_OBJECT.

NewSize  -  The new size, in bytes, of the object. On successfull return, the object specified by ObjectID has at least this much space.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully re-allocated object to requested size.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**Sample Usage :**
```

    DBHANDLE    hDb;
    OBJECT_DESCRIPTOR   objLeftToDo;
    DWORD       dwNeededSize, dwExistingSize;
    WORD        wClass, wPrivs;

    /* Get the size of the existing $LeftToDo object. */

    if (error = NSFDbGetObjectSize(hDb, 
                        objLeftToDo.RRV, 
                        objLeftToDo.ObjectType,
                        &dwExistingSize, &wClass, &wPrivs))
    {
        printf ("Error: unable to get size of object '%s' in macro.\n",
                        FILTER_LEFTTODO_ITEM);
        goto Exit2;
    }

    /* Reallocate the existing object if necessary. */

    if (dwExistingSize < dwNeededSize)
    {
        /* realloc 1K more than needed so won't have to realloc as often */
        if (error = NSFDbReallocObject(hMacro,
                                    objLeftToDo.RRV, dwNeededSize+1024))
        {
            printf ("Error: unable to re-allocate '%s' to %ld bytes.\n",
                        FILTER_LEFTTODO_ITEM, dwNeededSize);
            goto Exit2;
        }
    }

    /*  Write the object */
    if (error = NSFDbWriteObject(hDb, objLeftToDo.RRV, 
                        hLeftToDo, 0,
                        dwNeededSize))
    {
        printf ("Error: unable to write '%s' object to macro note.\n",
                                FILTER_LEFTTODO_ITEM);
    }

```
**See Also :**
[NSFDbAllocObject](/reference/Func/NSFDbAllocObject)
[NSFDbFreeObject](/reference/Func/NSFDbFreeObject)
[NSFDbGetObjectSize](/reference/Func/NSFDbGetObjectSize)
[NSFDbReadObject](/reference/Func/NSFDbReadObject)
[NSFDbWriteObject](/reference/Func/NSFDbWriteObject)
[NSFItemAppendObject](/reference/Func/NSFItemAppendObject)
[OBJECT_DESCRIPTOR](/reference/Data/OBJECT_DESCRIPTOR)
---

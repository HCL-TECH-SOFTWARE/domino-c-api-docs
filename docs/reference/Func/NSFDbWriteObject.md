##### Function : Database
##### NSFDbWriteObject - Write an object from memory to a database file.
---
```
#include <nsfobjec.h>
STATUS LNPUBLIC NSFDbWriteObject(

	DBHANDLE  hDB,
	DWORD  ObjectID,
	DHANDLE  hBuffer,
	DWORD  Offset,
	DWORD  Length);
```
**Description :**

Write an object from a memory block to the database file.

Use the object ID (the RRV) to identify the object to write. If the object 
previously existed, get the object ID from the RRV member of an 
OBJECT_DESCRIPTOR structure of an object item in a note. If you just created 
the object, get the object ID from the call to NSFDbAllocObject. 

The object in the database must have sufficient space reserved by 
NSFDbAllocObject or NSFDbReallocObject to accommodate the specified offset plus 
length. If not, this function will return a nonzero status code. Use 
NSFDbGetObjectSize before writing an object to check that the object in the 
database has sufficient space.

Domino and Notes uses objects to store data that is not rendered on the screen 
by the Notes editor. Examples include file attachments ($FILE fields), help 
indexes, and macro left-to-do lists ($LeftToDo). Note that for file 
attachments, NSFNoteAttachFile is simpler to use than NSFDbWriteObject.

**Parameters :**
Input :
hDB  -   Handle to the open database where the object resides

ObjectID  -  Object ID (the RRV) identifying the object in the database. Get this ID from the RRV member of the OBJECT_DESCRIPTOR structure stored in items of type TYPE_OBJECT. If you just created the object, get the object ID from the call to NSFDbAllocObject.

hBuffer  -  Handle to memory area containing the data to write. This memory must be unlocked.

Offset  -  Offset within the object in the database specifying where NSFDbWriteObject should begin writing.

Length  -  Length, in bytes, of data to write to the object in the database.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully wrote object into database file from memory buffer.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**Sample Usage :**
```

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
[NSFItemAppendObject](/reference/Func/NSFItemAppendObject)
[OBJECT_DESCRIPTOR](/reference/Data/OBJECT_DESCRIPTOR)
[NSFDbAllocObject](/reference/Func/NSFDbAllocObject)
[NSFDbReallocObject](/reference/Func/NSFDbReallocObject)
[NSFDbFreeObject](/reference/Func/NSFDbFreeObject)
[NSFDbGetObjectSize](/reference/Func/NSFDbGetObjectSize)
[NSFDbReadObject](/reference/Func/NSFDbReadObject)
---

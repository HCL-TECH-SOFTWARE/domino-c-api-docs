##### Function : Database
##### NSFDbGetObjectSize - Get the size and class of an object in a database file.
---
```
#include <nsfobjec.h>
STATUS LNPUBLIC NSFDbGetObjectSize(

	DBHANDLE  hDB,
	DWORD  ObjectID,
	WORD  ObjectType,
	DWORD far *retSize,
	WORD far *retClass,
	WORD far *retPrivileges);
```
**Description :**

This function returns the size (in bytes), the class, and the privileges mask 
of an object in a Domino database file.  

Specify the object by its object ID. The object ID (the RRV) identifies the 
location of the object in the database file. Get this object ID from the RRV 
member of the OBJECT_DESCRIPTOR structure. The OBJECT_DESCRIPTOR structure 
resides in an item of type TYPE_OBJECT in a note.

Use NSFDbGetObjectSize when updating an object to check that the size of the 
object is large enough to store the updated object data. If the size of the 
updated data exceeds the size of the object, call NSFDbReallocObject to 
increase the amount of space reserved for the object in the database file.

**Parameters :**
Input :
hDB  -  Handle to the open database containing the object.

ObjectID  -  The object ID (the RRV) of the object. Get this from the RRV member of an OBJECT_DESCRIPTOR structure.

ObjectType  -  The object type. OBJECT_FILE for file attachments.  OBJECT_FILTER_LEFTTODO for macro left-to-do Id table.  See Symbolic Value : Field OBJECT_xxx for a list of all possible values. 

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully obtained object size and class.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


retSize  -  Optional;  if not NULL, receives the size, in bytes, of the database object specified by the object ID.

retClass  -  Optional;  if not NULL, receives the object class. Object classes are the same as note classes (e.g. NOTE_CLASS_DOCUMENT). See Symbolic Value, NOTE_CLASS_xxx for a list of all possible values.

retPrivileges  -  Optional;  if not NULL, receives the privilege mask for this object.


**Sample Usage :**
```
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
[NSFDbAllocObject](/domino-c-api-docs/reference/Func/NSFDbAllocObject)
[NSFDbFreeObject](/domino-c-api-docs/reference/Func/NSFDbFreeObject)
[NSFDbReadObject](/domino-c-api-docs/reference/Func/NSFDbReadObject)
[NSFDbReallocObject](/domino-c-api-docs/reference/Func/NSFDbReallocObject)
[NSFDbWriteObject](/domino-c-api-docs/reference/Func/NSFDbWriteObject)
[NSFItemAppendObject](/domino-c-api-docs/reference/Func/NSFItemAppendObject)
[OBJECT_DESCRIPTOR](/domino-c-api-docs/reference/Data/OBJECT_DESCRIPTOR)
---

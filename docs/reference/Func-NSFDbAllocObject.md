##### Function : Database
##### NSFDbAllocObject - Allocates an object in a Domino database file.
---
##### #include <nsfobjec.h>
STATUS LNPUBLIC **NSFDbAllocObject(**

	DBHANDLE  hDB,
	DWORD  dwSize,
	WORD  Class,
	WORD  Privileges,
	DWORD far *retObjectID);
**Description :**
Allocate space for an object in an open database file. This reserves space in 
the database file for the object data itself and returns the object ID.

The object ID (the RRV) identifies the location of the object in the database 
file. You need this object ID in subsequent calls to NSFDbWriteObject, etc. 
Store this object ID in the RRV member of the OBJECT_DESCRIPTOR structure. 
Store the OBJECT_DESCRIPTOR structure in an item of type TYPE_OBJECT that you 
append to a note. 

Domino and Notes uses objects and object items to store data that is not 
rendered on the screen by the Notes editor. Examples include file attachments 
($FILE fields), help indexes, and macro left-to-do lists ($LeftToDo). Note that 
for file attachments, NSFNoteAttachFile is simpler to use than 
NSFItemAppendObject.

An object item consists of two parts: the object itself in the database, and 
the object item in the note. The object itself resides in the Domino database 
file at a location identified by it's RRV (the Object ID). Use NSFDbAllocObject 
to allocate space for the object itself.  The object item is a structure of 
type OBJECT_DESCRIPTOR that resides in a note. Use NSFItemAppendObject to 
append the object item to a note.

Create an object by first creating the object itself in the database, then 
appending an object item to the note. Read an object by reading the object item 
in the note, obtaining the RRV of the object, then calling NSFDbReadObject 
specifying the RRV you obtained from the item.
**Parameters :**
Input :
hDB  -  Handle to the open database in which to allocate the object

dwSize  -  Size in bytes of the object data

Class  -  Object class. Normally, set this to NOTE_CLASS_DOCUMENT.  Domino and Notes uses the same classes for objects as for notes. See NOTE_CLASS_xxx.

Privileges  -  Privilege mask controlling access to this object. Specify zero if not used.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully appended Item to the note.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


retObjectID  -  The specified variable receives the Object ID of the object in the database. Use this object ID to refer to this object in subsequent calls to NSFDbWriteObject, etc. Store this object ID in the RRV member of the OBJECT_DESCRIPTOR structure.

**Sample Usage :**
```

    if (error = NSFDbAllocObject(hDb, dwObjectSize, NOTE_CLASS_DOCUMENT, 0, 
                                &dwObjectID))
    {
        printf ("Error: unable to allocate LeftToDo Object.\n");
        goto Exit1;
    }
    
    objLeftToDo.ObjectType = OBJECT_FILTER_LEFTTODO ;
    objLeftToDo.RRV = dwObjectID;

```
**See Also :**
[NOTE_CLASS_xxx](D:/md_files/NOTE_CLASS_xxx.md)
[NSFDbFreeObject](D:/md_files/NSFDbFreeObject.md)
[NSFDbGetObjectSize](D:/md_files/NSFDbGetObjectSize.md)
[NSFDbReadObject](D:/md_files/NSFDbReadObject.md)
[NSFDbReallocObject](D:/md_files/NSFDbReallocObject.md)
[NSFDbWriteObject](D:/md_files/NSFDbWriteObject.md)
[NSFItemAppendObject](D:/md_files/NSFItemAppendObject.md)
[OBJECT_DESCRIPTOR](D:/md_files/OBJECT_DESCRIPTOR.md)
---

##### Function : Database
##### NSFDbFreeObject - Free the space used by an object in a database file.
---
```
#include <nsfobjec.h>
STATUS LNPUBLIC NSFDbFreeObject(

	DBHANDLE  hDB,
	DWORD  ObjectID);
```
**Description :**

This function frees the space from a database file associated with an object. 

Use the Object ID to identify the object to free. The object ID (the RRV) 
identifies the location of the object in the database file. Normally, you get 
this object ID from the RRV member of the OBJECT_DESCRIPTOR structure. The 
OBJECT_DESCRIPTOR structure is the value stored in an item of type TYPE_OBJECT 
in a note. 

Thus a Domino object consists of two parts: the object itself in the database, 
and the object item in the note. This function frees the space reserved for the 
object itself.

Normally, you do not need to call NSFDbFreeObject explicitly when deleting an 
item of type TYPE_OBJECT. If the fDelete flag parameter to NSFItemAppendObject 
was TRUE when the object item was appended to the note, then NSFItemDelete will 
free the object automatically when the object item is deleted.

**Parameters :**
Input :
hDB  -  handle to the open database where the object resides

ObjectID  -  The object ID (the RRV) of the object to free. Get this ID from the OBJECT_DESCRIPTOR structure stored in an item of type TYPE_OBJECT in a note.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully freed object in database file.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**See Also :**
[NSFDbAllocObject](/domino-c-api-docs/reference/Func/NSFDbAllocObject)
[NSFDbGetObjectSize](/domino-c-api-docs/reference/Func/NSFDbGetObjectSize)
[NSFDbReadObject](/domino-c-api-docs/reference/Func/NSFDbReadObject)
[NSFDbReallocObject](/domino-c-api-docs/reference/Func/NSFDbReallocObject)
[NSFDbWriteObject](/domino-c-api-docs/reference/Func/NSFDbWriteObject)
[NSFItemAppendObject](/domino-c-api-docs/reference/Func/NSFItemAppendObject)
[OBJECT_DESCRIPTOR](/domino-c-api-docs/reference/Data/OBJECT_DESCRIPTOR)
---

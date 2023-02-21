##### Function : Database
##### NSFDbReadObject - Read an object into memory.
---
```
#include <nsfobjec.h>
STATUS LNPUBLIC NSFDbReadObject(

	DBHANDLE  hDB,
	DWORD  ObjectID,
	DWORD  Offset,
	DWORD  Length,
	DHANDLE far *rethBuffer);
```
**Description :**

Read an object from a database file into memory. This returns a handle 
specifying a memory area where the object has been read. Free this memory after 
processing it.

Use the object ID (the RRV) to identify the object to read. Get this object ID 
from the RRV member of an OBJECT_DESCRIPTOR structure. The OBJECT_DESCRIPTOR 
structure resides in items of type TYPE_OBJECT appended to notes. 

Domino and Notes use objects to store data that is not rendered on the screen 
by the Notes editor. Examples include file attachments ($FILE fields), help 
indexes, and macro left-to-do lists ($LeftToDo). Note that for file 
attachments, NSFNoteExtractFile is simpler to use than NSFDbReadObject.

**Parameters :**
Input :
hDB  -  Handle to the open database where the object resides

ObjectID  -  Object ID (the RRV) identifying the object in the database. Get this ID from the RRV member of the OBJECT_DESCRIPTOR structure stored in items of type TYPE_OBJECT.

Offset  -  Begin reading at this offset (in bytes) from the start of the object. Specify 0 to start at the beginning of the object.

Length  -  Number of bytes to read. Must not be zero.  Use MAXDWORD to read in the number of bytes equal to the size of the object. 

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully read object from database file to memory buffer.

ERR_OBJECT_CANNOT_BE_ZERO - Length input parameter specified zero.

ERR_OBJECT_TRUNCATED - Specified offset exceeds size of object, or length input parameter exceeds object size minus offset.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


rethBuffer  -  Receives a handle to a memory area containing the object data read from the file.


**Sample Usage :**
```
STATUS LNPUBLIC ReadLeftToDoObject(
	DBHANDLE            hDb,
	NOTEHANDLE          hMacro,
	OBJECT_DESCRIPTOR  *pObject,
	DHANDLE             *phLeftToDo,
	TIMEDATE           *ptdLeftToDoTime,
	WORD               *pwLeftToDoFlags )
{
	STATUS      error;
	WORD        wDataType;
	BLOCKID     bidValue;
	DWORD       dwValueLength;
	void       *ptable;
	OBJECT_DESCRIPTOR  tempObject;
	OBJECT_DESCRIPTOR *tempPtr;
	
	error = NSFItemInfo(hMacro, FILTER_LEFTTODO_ITEM, 
                       sizeof(FILTER_LEFTTODO_ITEM)-1,
                       NULL, &wDataType, &bidValue, &dwValueLength);

	if ( ERR(error) == ERR_ITEM_NOT_FOUND )
	{
	 return (error);
	}
	else if (error)
	{
	 printf("Error: unable get '%s' from Macro.\n",
	  FILTER_LEFTTODO_ITEM);
	 return(error);
	}
	if (wDataType != TYPE_OBJECT)
	{
	 printf ("Error: item '%s' not TYPE_OBJECT.\n", FILTER_LEFTTODO_ITEM);
	 return(error);
	}
        
	*pObject = 
*((OBJECT_DESCRIPTOR*)(OSLockBlock(char,bidValue)+sizeof(WORD)));

	tempPtr = pObject;

	ODSReadMemory( &tempPtr, _OBJECT_DESCRIPTOR, &tempObject, 1 );

	if (tempObject.ObjectType != OBJECT_FILTER_LEFTTODO)
	{                                                 
	 printf ("Error: object '%s' unknown type.\n",
	  FILTER_LEFTTODO_ITEM);
	 OSUnlockBlock(bidValue);
	 return (ERR_RUNMACRO_BADOBJECTTYPE);
	}

	error = NSFDbReadObject(hDb, tempObject.RRV, 0, MAXDWORD, phLeftToDo);
	OSUnlockBlock(bidValue);
	if (error)
	{
	 printf ("Error: unable to read object '%s'.\n", FILTER_LEFTTODO_ITEM);
	 return (error);
	}

	ptable = OSLock(void, *phLeftToDo);
	*ptdLeftToDoTime = IDTableTime(ptable);
	*pwLeftToDoFlags = IDTableFlags(ptable);
	OSUnlock(*phLeftToDo);  /* unlock handle we are done with */

	return NOERROR;
}
```
**See Also :**
[NSFItemAppendObject](/domino-c-api-docs/reference/Func/NSFItemAppendObject)
[OBJECT_DESCRIPTOR](/domino-c-api-docs/reference/Data/OBJECT_DESCRIPTOR)
[NSFDbAllocObject](/domino-c-api-docs/reference/Func/NSFDbAllocObject)
[NSFDbReallocObject](/domino-c-api-docs/reference/Func/NSFDbReallocObject)
[NSFDbFreeObject](/domino-c-api-docs/reference/Func/NSFDbFreeObject)
[NSFDbGetObjectSize](/domino-c-api-docs/reference/Func/NSFDbGetObjectSize)
[NSFDbWriteObject](/domino-c-api-docs/reference/Func/NSFDbWriteObject)
---

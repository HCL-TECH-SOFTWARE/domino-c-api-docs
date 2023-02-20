##### Function : Item (Field)
##### NSFItemAppendObject - Add an object item (field of type TYPE_OBJECT) to a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemAppendObject(

	NOTEHANDLE  hNote,
	WORD  ItemFlags,
	const char far *Name,
	WORD  NameLength,
	BLOCKID  bhValue,
	DWORD  ValueLength,
	BOOL  fDealloc);
```
**Description :**

Add an item of TYPE_OBJECT to an existing note. You must use 
NSFItemAppendObject to append an item of TYPE_OBJECT to a note rather than 
NSFItemAppend, because NSFItemAppendObject copies certain information from the 
item value to the Domino internal item descriptor.

An object item consists of two parts: the object itself in the database, and 
the object item in the note. The object itself resides in the Domino database 
file at a location identified by it's RRV (a.k.a. Object ID). Use the 
NSFDbAllocObject family of functions to manipulate the object itself.  The 
object item is a structure of type OBJECT_DESCRIPTOR that resides in a note. 
The RRV member of the OBJECT_DESCRIPTOR identifies the location of the object 
data in the Domino database file.

Domino and Notes uses objects to store data that is not rendered on the screen 
by the Notes editor. Examples include file attachments ($FILE fields), help 
indexes, and macro left-to-do lists ($LeftToDo fields). For file attachments, 
NSFNoteAttachFile is simpler to use than NSFItemAppendObject.

Add an object item to a note by allocating space for the object itself in the 
database, then appending the object item to the note. Call NSFDbAllocObject to 
allocate space for the object and to obtain the RRV (Object ID) of the object. 
Initialize the RRV member of an OBJECT_DESCRIPTOR structure with this object 
ID. Next, initialize an item value buffer to append to the note. The item value 
buffer must start with the data type word (TYPE_OBJECT) followed by the 
OBJECT_DESCRIPTOR structure.   Call NSFItemAppendObject() to add the item 
buffer to the note.  You must unlock the block containing the item buffer 
before you call NSFItemAppendObject. 

NSFItemAppendObject transfers ownership of the item buffer to the note. After 
successful return from NSFItemAppendObject, do not free the item buffer.

**Parameters :**
Input :
hNote  -  The handle to the note that will receive the object item.

ItemFlags  -  The flags that define the characteristics of this item. These flags are defined in ITEM_xxx and may be bit-wise - OR'ed together for combined functionality. Normally, use ITEM_SUMMARY for items of type TYPE_OBJECT.

Name  -  Field name of the item in the note. Normally, use one of the symbolic values defined in STDNAMES.H such as VIEW_COLLECTION_ITEM or FILTER_LEFTTODO_ITEM.

NameLength  -  Length, in bytes, of the specified Name string. Do not count the zero terminator, if present.

bhValue  -  Specifies a Domino memory block containing the item value. This value must begin with the data type word (which must be TYPE_OBJECT for an object item) followed by a structure of type OBJECT_DESCRIPTOR. For portability to non-Intel platforms, the data type word must be in Host format, but the OBJECT_DESCRIPTOR structure must be converted to Domino Canonical Format. The memory block must be unlocked. NSFItemAppendObject transfers ownership of the memory block to the note. Do not free this memory block after successful return.

ValueLength  -  The length, in bytes, of the item value. This length must include the length of the data type word.

fDealloc  -  TRUE if object (specified by the RRV member of the OBJECT_DESCRIPTOR) should be de-allocated by Domino or Notes when the note is de-allocated or the object item is deleted. FALSE gives the object persistence beyond that of the object item. Normally, you should specify TRUE.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully appended object item to the note.

ERR_xxx - Errors returned by lower level Notes functions.  Call to OSLoadString to interpret the error code for display.



**Sample Usage :**
```
BYTE       *pb;
WORD       *pw;
DWORD       dwObjectID;
OBJECT_DESCRIPTOR   objLeftToDo;
OBJECT_DESCRIPTOR  *pobj;
BLOCKID     bidLeftToDo;
DWORD       dwItemSize;

if (error = NSFDbAllocObject(hDb, dwObjectSize, NOTE_CLASS_DOCUMENT, 0, 
                            &dwObjectID))
{
   printf ("Error: unable to allocate LeftToDo Object.\n");
   goto Exit1;
}
    
objLeftToDo.ObjectType =  OBJECT_FILTER_LEFTTODO ;
objLeftToDo.RRV = dwObjectID;

dwItemSize = (DWORD) (sizeof(WORD) + sizeof(OBJECT_DESCRIPTOR));

if (error = OSMemAlloc(0, dwItemSize, &(bidLeftToDo.pool)))
{
   printf("Error: unable to allocate %ld bytes for LeftToDo item.\n",
                            dwItemSize);
   NSFDbFreeObject(hDb, dwObjectID);
   goto Exit1;
}

bidLeftToDo.block = NULLHANDLE;

pw = OSLockBlock(WORD, bidLeftToDo);
*pw = TYPE_OBJECT;
pw++;

ODSWriteMemory (&pw, _OBJECT_DESCRIPTOR, &objLeftToDo, 1);
    
OSUnlockBlock(bidLeftToDo);

if (error = NSFItemAppendObject(hMacro, ITEM_SUMMARY,
                            FILTER_LEFTTODO_ITEM, 
                            sizeof(FILTER_LEFTTODO_ITEM)-1,
                            bidLeftToDo, 
                            dwItemSize, 
                            TRUE)) /* Notes will deallocate memory */
{
   printf ("Error: unable to append %s item.\n",
                            FILTER_LEFTTODO_ITEM);
   OSMemFree(bidLeftToDo.pool);
   goto Exit1;
}
```
**See Also :**
[ITEM_xxx](/reference/Symb/ITEM_xxx)
[NSFDbAllocObject](/reference/Func/NSFDbAllocObject)
[NSFDbWriteObject](/reference/Func/NSFDbWriteObject)
[OBJECT_DESCRIPTOR](/reference/Data/OBJECT_DESCRIPTOR)
---

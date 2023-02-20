##### Function : OS Memory
##### OSMemFree - Deallocate (free) a block of Domino memory.
---
```
#include <osmem.h>
STATUS LNPUBLIC OSMemFree(

	DHANDLE  Handle);
```
**Description :**

OSMemFree is used to deallocate a block of Domino memory that was created via 
OSMemAlloc.  In order for the deallocation to take place, the lock reference 
count for the memory block must be zero. In other words, all OSLockObject 
operations made to the memory block must be matched with an OSUnlockObject 
operation before memory can be freed.

Calling this routine with a HANDLE that is invalid or out of range, or with a 
HANDLE for a memory object that is still locked, will result in a Notes PANIC 
halt .

Note: this routine must be called to free the memory objects specifically 
created by you with OSMemAlloc or returned by one of several functions.  Each 
function description will mention any specific objects you must 'free'.   The 
following discussion will organize C API functions into several categories, 
based on the way they handle the memory they create, manage, and destroy.

Generally, functions that create database objects come in pairs, which could be 
regarded as symmetrical functions.  A pair such as NSFNoteOpen and NSFNoteClose 
are a case in point; any memory objects created by NSFNoteOpen will be freed by 
NSFNoteClose.  Also, since notes are composed of a header structure and a 
variable number of memory objects called 'items' (fields), NSFNoteClose will 
take care of freeing the memory associated with any items in a note.  You must 
NOT free memory that is still associated with a note's "items" with OSMemFree, 
as a subsequent NSFNoteClose will try to free the memory objects that no longer 
exist and a Notes PANIC halt will be the result.

Another category of functions transfers responsibility for existing memory 
objects to symmetrical functions.  A function such as NSFItemAppendByBLOCKID 
actually creates an association between an object in memory and a note.   You 
must NOT free the memory associated with note "items" by NSFItemAppendByBLOCKID 
with OSMemFree, as NSFNoteClose will try to do the same when it is called and a 
Notes PANIC halt will be the result.

Another category of functions absolves symmetrical functions of their 
responsibility for existing memory objects.  Functions such as 
NSFItemDeleteByBLOCKID or NSFItemDelete remove the association between an 
object in memory (item) and a note, and  then perform an OSMemFree themselves.

Another category of functions create memory objects for you, in order to return 
information to the caller.  Generally, the size of these memory objects cannot 
be forseen or efficiently limited.  These include, but are not limited to: 
NIFReadEntries, NSFConvertItemToComposite, and NSFConvertItemToText.  Again, 
the function descriptions will flag any arguments that create memory your 
program is ultimately responsible for cleaning up.

The final category of functions copy existing memory objects, transferring 
responsibility for management of the object to a symmetrical function.  
NSFItemAppend actually copies a memory object and appends it as a note item 
(field).  NSFNoteClose takes care of the copied data, and you are left with the 
original object, which your program may either re-use or free.

**Parameters :**
Input :
Handle  -  Handle for the memory object to be freed.

Output :
(routine)  -  Always returns NOERROR.  There is no need to check the return value.



**Sample Usage :**
```

   if (wCleanUp & FREE_HCDBUF)
       OSMemFree(hCDBuf);

```
**See Also :**
[OSMemAlloc](/reference/Func/OSMemAlloc)
[OSMemRealloc](/reference/Func/OSMemRealloc)
[OSMemGetSize](/reference/Func/OSMemGetSize)
[OSLockObject](/reference/Func/OSLockObject)
[OSUnlockObject](/reference/Func/OSUnlockObject)
---

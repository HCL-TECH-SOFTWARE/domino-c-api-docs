##### Function : Database
##### NSFDbGetNotes - Get database note information with several callback routines.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFDbGetNotes(

	DBHANDLE  hDB,
	DWORD  NumNotes,
	NOTEID *NoteID,
	DWORD *NoteOpenFlags,
	DWORD *SinceSeqNum,
	DWORD  ControlFlags,
	DBHANDLE  hObjectDB,
	void *CallbackParam,
	NSFGETNOTESCALLBACK  GetNotesCallback,
	NSFNOTEOPENCALLBACK  NoteOpenCallback,
	NSFOBJECTALLOCCALLBACK  ObjectAllocCallback,
	NSFOBJECTWRITECALLBACK  ObjectWriteCallback,
	TIMEDATE *FolderSinceTime,
	NSFFOLDERADDCALLBACK  FolderAddCallback);
```
**Description :**

This function will return a stream of notes to the caller through several 
callback functions.

**Parameters :**
Input :
hDB  -  Handle to an open database to retrieve notes from.

NumNotes  -  Number of notes to retrieve.

NoteID  -  Pointer to note ID(s) of retrieved note(s).

NoteOpenFlags  -  Pointer to flags that control the manner in which the note is opened. This, in turn, controls what information about the note is available to you and how it is structured. The flags are defined in OPEN_xxx (note) and may be or'ed together to combine functionality.

SinceSeqNum  -  Pointer to the since sequence number.

ControlFlags  -  Flags that control the actions of the function during note retrieval. The flags are defined in GETNOTES_xxx.

hObjectDB  -  Database handle.  If objects are being retrieved (GETNOTES_SEND_OBJECTS) and the value of hObjectDB is not NULLHANDLE, objects will be stored in this database and attached to the incoming notes prior to NoteOpenCallback being called.  

CallbackParam  -  Callback parameter for each of the callback functions.

GetNotesCallback  -  The get notes callback function pointer.  Called once before any others but only if going to a server that is R6 or greater.   If GETNOTES_ORDER_BY_SIZE is specified in options the two DWORD parameters, TotalSizeLow and TotalSizeHigh, provide the approximate total size of the bytes to be returned in the notes and objects.  These values are intended to be used for progress indication.  See NSFGETNOTESCALLBACK

NoteOpenCallback  -  The note open callback function pointer.  This function is called for each note retrieved.  If non-NULL, this is called for each note after all objects have been retrieved (if GETNOTES_SEND_OBJECTS is specified).  See NSFNOTEOPENCALLBACK.

ObjectAllocCallback  -  The object allocate callback function pointer.  If GETNOTES_SEND_OBJECTS is specified and hObjectDB is not NULLHANDLE, this function is called exactly once for each object to provide the caller with information about the object's size and ObjectID.  The intent is to allow for the physical allocation for the object if need be.  It is called before the NoteOpenCallback for the corresponding note.  See NSFOBJECTALLOCCALLBACK.

ObjectWriteCallback  -  The object write callback function pointer.  This function is called for each "chunk" of each object if GETNOTES_SEND_OBJECTS is specified and hObjectDB is not NULLHANDLE.  For each object this will be called one or more times.  See NSFOBJECTWRITECALLBACK.

FolderSinceTime  -  A pointer to a TIMEDATE structure containing a time/date value specifying the earliest time to retrieve notes from the folder.  If GETNOTES_GET_FOLDER_ADDS is specified this is the time folder operations should be retrieved from.

FolderAddCallback  -  The folder add callback function pointer.  If GETNOTES_GET_FOLDER_ADDS is specified but GETNOTES_APPLY_FOLDER_ADDS is not, this function is called for each note after the NoteOpenCallback function is called.  See NSFFOLDERADDCALLBACK.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.



**See Also :**
[GETNOTES_xxx](/domino-c-api-docs/reference/Symb/GETNOTES_xxx)
[NSFFOLDERADDCALLBACK](/domino-c-api-docs/reference/Data/NSFFOLDERADDCALLBACK)
[NSFGETNOTESCALLBACK](/domino-c-api-docs/reference/Data/NSFGETNOTESCALLBACK)
[NSFNOTEOPENCALLBACK](/domino-c-api-docs/reference/Data/NSFNOTEOPENCALLBACK)
[NSFOBJECTALLOCCALLBACK](/domino-c-api-docs/reference/Data/NSFOBJECTALLOCCALLBACK)
[NSFOBJECTWRITECALLBACK](/domino-c-api-docs/reference/Data/NSFOBJECTWRITECALLBACK)
---

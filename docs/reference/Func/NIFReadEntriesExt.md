##### Function : Database 
##### NIFReadEntriesExt - Read view entries and their data.
---
```
#include <nif.h>
STATUS NIFReadEntriesExt(

	HCOLLECTION  hCollection,
	COLLECTIONPOSITION *CollectionPos,
	WORD  SkipNavigator,
	DWORD  SkipCount,
	WORD  ReturnNavigator,
	DWORD  ReturnCount,
	DWORD  ReturnMask,
	TIMEDATE *DiffTime,
	DHANDLE  DiffIDTable,
	DWORD  ColumnNumber,
	DWORD  Flags,
	DHANDLE *rethBuffer,
	WORD *retBufferLength,
	DWORD *retNumEntriesSkipped,
	DWORD *retNumEntriesReturned,
	WORD *retSignalflags,
	TIMEDATE *retDiffTime,
	TIMEDATE *retLastModifiedTime,
	DWORD *retSequence);
```
**Description :**

Read view entries and their data. Provides capabilities that NIFReadEntries 
does not but shares many of its parameters and functionality. This extended 
version of the call allows users to return:

 View entry information based upon changes received after a set time.
 View entry information for a set of documents specified in an IDTable of 
NOTEIDs. 
 Data from a specific single column in the view. 
 A sequence number usable as a virtual version number to detect view updating.

**Parameters :**
Input :
hCollection  -  The handle of the collection that you want to read.

CollectionPos  -  A pointer to a COLLECTIONPOSITION that holds the starting point within the collection. The starting point controls which note in the collection is the first note read. To start at the beginning of the collection, set CollPosition.Level to 0 and CollPosition.Tumbler[0] to 1.  An alternative way to start at the beginning of the collection is to set the CollPosition.Level to 0, set the CollPosition.Tumbler[0] to 0, set the skip navigate flag (third parameter) to NAVIGATE_NEXT and set the skip count (fourth parameter) to 1L.

SkipNavigator  -  Flags that controls how the collection is navigated during the "skip" operation. Skipping occurs before the collection is read and may be used to pass over some of the collection's entries. The skip flags are defined in NAVIGATE_xxx.

SkipCount  -  How many entries to skip before reading the collection. The skip pattern is determined by SkipNavigator parameter. To skip no entries, set this argument to 0.

ReturnNavigator  -  Flags that control how the collection is navigated when the entries are read (after skipping is complete). The read flags are defined in NAVIGATE_xxx. See the example below for how to read all the entries in a collection.

ReturnCount  -  The maximum number of entries that should be returned. To read all the entries in the collection, set this argument to 0xFFFFFFFF. To stop reading before the end of the collection, set this argument to the number of entries you want.

ReturnMask  -  Flags that control what information about the collection's entries will be returned. The information flags are defined in READ_MASK_xxx, and may be OR'ed together to combine functionailty.  If more than one flag is requested, the order of the item's information in the buffer is the same order as the flag's bit numbers (i.e. flag bit 0 precedes bit 1, then bit 2, etc).

DiffTime  -  If non-null, this is a "differential view read" - optimize results to only return full information for notes which have changed (or are new) in the view, return just NoteIDs for notes which haven't changed since this time and return a deleted ID table for notes which may be known by the caller and have been deleted since DiffTime.

DiffIDTable  -  If DiffTime is non-null and DiffIDTable is not NULLHANDLE it provides a list of notes which the caller has current information on. We use this to know which notes can be returned based on input DiffTime.

ColumnNumber  -  If not MAXDWORD, number of single column to return values for.

Flags  -  Unused.

Output :
(routine)  -  Returns status from the call, either success or an error.

The return codes include: 
NOERROR - On success. 
ERR_HDL_NULL - On NULL collection. 
ERR_COLLECTION_HANDLE - On closed/invalid collection handle. 
ERR_NIF_VIEW_DELETED - If view has been deleted. 
ERR_BAD_COLLATION_NUM - If collation number is negative or greater than number of collations in view.


CollectionPos  -  A pointer to a COLLECTIONPOSITION indicating the last note in the collection that was read by NIFReadEntriesExt.  If the entire collection is not read by a call to NIFReadEntriesExt, this COLLECTIONPOSITION can be used as input into the next call to NIFReadEntriesExt.  In this case, be sure to set the skip navigate flag and skip count so that the last note read in the previous call to NIFReadEntriesExt is skipped.

rethBuffer  -  The address of a HANDLE variable in which the handle to a buffer of information about this collection is returned.  This may be returned as NULLHANDLE if there were no entries returned, so be sure to check for NULLHANDLE before attempting to lock the returned handle. The caller is responsible for freeing this buffer using OSMemFree.

retBufferLength  -  The address of a WORD in which the length of the information buffer is returned. If you are not interested in this length, set this argument to NULL.

retNumEntriesSkipped  -  The address of a WORD in which the number of entries that were skipped is returned. If you are not interested in this information, set this argument to NULL.

retNumEntriesReturned  -  The address of a DWORD in which the number of entries is returned. If you are not interested in this information, set this argument to NULL.  However, you should use this returned value to determine whether this function found any entries.

retSignalflags  -  The address of a WORD in which various result flags are returned.  If one of the the flags represented by SIGNAL_ANY_CONFLICT is set, the collection has changed since it was last read. If the SIGNAL_MORE_TO_DO flag is set, then the end of the collection has not been reached and there exists more information than could fit in the return buffer.  In this case, NIFReadEntries should be called again to retrieve an additional buffer of information.  The signal flags are defined in SIGNAL_xxx, and are returned OR'ed together.

retDiffTime  -  If non-NULL, returned time to use in subsequent differential view read.

retLastModifiedTime  -  If non-NULL, returns last modified time of the view.

retSequence  -  Last updated sequence number of the view.


**Sample Usage :**
```
/* Usage of NIFReadEntriesExt. */

COLLECTIONPOSITION IndexPos;
DHANDLE hBuffer = NULLHANDLE;
DWORD dwFillCount = 24;
DWORD dwEntriesReturned = 0, dwEntriesSkipped = 0;
WORD wSignalFlags = 0;
WORD wSummarySize = 0;
TIMEDATE NewTime;
TIMEDATE tdLastModified;
TIMEDATE OldTime;

TimeDateClear(&OldTime);
OSCurrentTIMEDATE(&NewTime);
TimeDateClear(&tdLastModified);

Czeromem(&IndexPos, sizeof(COLLECTIONPOSITION));
IndexPos.Tumbler[0] = 1L;
if (hOldIDTable != NULLHANDLE)
{
	error = NIFReadEntriesExt(hViewCollection, /* Handle to this 
collection. */
	  &IndexPos, /* Where to start in collection. */
	  NAVIGATE_NEXT, /* Order to skip entries. */
	  0L, /* Number to skip. */
	  NAVIGATE_NEXT, /* Order to use after skipping. */
	  dwFillCount, /* Max return number. */
	  READ_MASK_SUMMARYVALUES |  READ_MASK_NOTEUNID | READ_MASK_NOTEID, /* 
Info we want. */
	  &OldTime,
	  hOldIDTable, /* ID table of note documets in a view. */
	  MAXWORD, /* Column number. */
	  0,
	  &hBuffer,  /* Handle to info (return). */
	  &wSummarySize,  /* Length of buffer (return). */
	  &dwEntriesSkipped, /* Entries skipped (return). */
	  &dwEntriesReturned,  /* Number of notes (return). */
	  &wSignalFlags, /* Share warning (return). */
	  &NewTime,
	  &tdLastModified, /* Last modified time of the view. */
	  NULL); /* Last updated sequence number of the view. */
	Cmovmem(&OldTime, &NewTime, sizeof(TIMEDATE));
	if(hBuffer != NULLHANDLE)
	 OSMemFree(hBuffer);
}
```
**See Also :**
---

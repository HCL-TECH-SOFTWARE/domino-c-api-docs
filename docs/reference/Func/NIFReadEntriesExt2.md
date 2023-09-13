##### Function : Database 
##### NIFReadEntriesExt2 - Read collection index information .
---
```
#include <nif.h>
STATUS NIFReadEntriesExt2(

	HCOLLECTION  hCollection,
	COLLECTIONPOSITION *CollectionPos,
	WORD  SkipNavigator,
	DWORD  SkipCount,
	WORD  ReturnNavigator,
	DWORD  ReturnCount,
	DWORD  ReturnMask,
	DWORD  ReturnMask2,
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

<br>
<font face="Times New Roman">A new feature is introduced to view NIFReadEntries output in JSON format. This feature is introduced with the new API call NIFReadEntriesExt2. With existing implementation, the output from NIFReadEntriesExt is in the form of structure (ITEM_TABLE) whereas with the new call the output would be in JSON format so that it facilitates the end user easily to parse JSON and represents output the way they want. This is achieved by enabling a new flag READ_MASK_TO_JSON as a Input parameter (ReturnMask2) in NIFReadEntriesExt2 API call. The return type for this call is STATUS. This new flag needs to be used along with other flags to return that value in JSON object. JSON object can be created with NOTEID, UNID, NOTE_CLASS and fields (length should be greater than '0') of the document based on input flags(ReturnMask).</font>
<p><font face="Times New Roman">This new call supports categorized, non-categorized and response type JSON output purely based on view type</font>. <font face="Times New Roman">In case of buffer overflow this call returns the Json object and then continues with new Json object from next document onwards.The size of Json object is limited to 32KB.</font>


**Parameters :**
Input :
hCollection  -  Per-user collection context handle.

CollectionPos  -  Starting index position of entry to skip/return.

SkipNavigator  -  Navigator used to skip "SkipCount" entries.

SkipCount  -  (max) # entries to skip before starting to return information.

ReturnNavigator  -  Navigator used to return entries (NOTE: only used when returning 2nd thru last entries).

ReturnCount  -  (max) # entries to return information.

ReturnMask  -  Mask specifying what information is to be returned on each entry(READ_MASK_xxx).  Information is always returned in the order of the bits which are 1.

ReturnMask2  -  Mask specifying what information is to be returned on each entry(READ_MASK2_xxx). READ_MASK2_TO_JSON need to be parsed if customer wants the output from the call for requested flags (ReturnMask) in JSON format.

DiffTime  -  If non-null, this is a "differential view read" - optimize results to only return full information for notes which have changed (or are new) in the view, return just NoteIDs for notes which haven't changed since this time and return a deleted ID table for notes which may be known by the caller and have been deleted since DiffTime.

DiffIDTable  -  If DiffTime is non-null and DiffIDTable is not NULLHANDLE it provides a list of notes which the caller has current information on. We use this to know which notes can be returned based on input DiffTime.

ColumnNumber  -  If not MAXDWORD, number of single column to return values for.

Flags  -  READENT_xxx flags.

rethBuffer  -  Place to receive return buffer handle (optional).

retBufferLength  -  Place to receive return buffer handle (optional).

retNumEntriesSkipped  -  Place to receive return buffer handle (optional).

retNumEntriesReturned  -  Place to receive return buffer handle (optional).

retDiffTime  -  If differential view read was done, TIMEDATE to be passed in on next read .

Output :
(routine)  -  Returns status from the call, either success or an error.

The return codes include: 
NOERROR - On success. 
ERR_HDL_NULL - On NULL collection. 
ERR_COLLECTION_HANDLE - On closed/invalid collection handle. 
ERR_NIF_VIEW_DELETED - If view has been deleted. 
ERR_BAD_COLLATION_NUM - If collation number is negative or greater than number of collations in view.
ERR_INVALID_ARG_TYPE	- In case of issue in object creation will exit here.
The return warning for JSON:
JSON_NULL_POINTER_ERROR  - If input size is NULL but continues by reporting error.
JSON_PARSE_ERROR - In case of error in Json parsing  but continues by reporting error.
JSON_OBJECT_INVALID - If return JSON is not a valid JSON but continues by reporting the error.


CollectionPos  -  Index position updated to point at LAST returned entry.

rethBuffer  -  The address of a HANDLE variable in which the handle to a buffer of information about this collection is returned.  This may be returned as NULLHANDLE if there were no entries returned, so be sure to check for NULLHANDLE before attempting to lock the returned handle. The caller is responsible for freeing this buffer using OSMemFree.

retBufferLength  -  The address of a WORD in which the length of the information buffer is returned. If you are not interested in this length, set this argument to NULL.

retNumEntriesSkipped  -  The address of a WORD in which the number of entries that were skipped is returned. If you are not interested in this information, set this argument to NULL.

retNumEntriesReturned  -  The address of a DWORD in which the number of entries is returned. If you are not interested in this information, set this argument to NULL.  However, you should use this returned value to determine whether this function found any entries.

retSignalflags  -  The following special file sharing warning flags:
		
SIGNAL_VIEW_DEFN_MODIFIED (warning) - At least one of the special view items($FORMULA, $COLLATION, $FORMULACLASS) have been modified by another user of the shared collection since the last ReadEntries call.When this error is received the caller may wish to re-open the view note and re-read the rebuilt collection. This is a warning; the buffer is returned anyway, in case the caller wishes to ignore the condition.This warning is only returned ONCE after each modification.
		
SIGNAL_VIEW_ITEM_MODIFIED (warning) - The contents of a non-critical view item($TITLE, $COLUMNFORMAT, etc) has been modified by another user of the shared collection since the last ReadEntries call.  When this warning is received,the caller may wish to re-read the view note and reload any of the changed items.  This is a warning; the buffer is returned anyway, in case the caller wishes to ignore the condition.This warning is only returned ONCE after each modification.
		
SIGNAL_INDEX_MODIFIED (warning) - The contents of the collection index has been modified by another user of the shared collection since the last ReadEntries call.  When this warning is received, the caller should re-locate the position in the index where the "caret" is located, and re-issue the call.  This is a warning; the buffer is returned anyway, in case the caller wishes to ignore the condition.  This warning is only returned ONCE after each modification.
		
SIGNAL_MORE_TO_DO (noerror) - The desired number of entries could not be returned because the buffer couldn't be expanded.The caller should retry the call at the returned index position to continue the read operation.SIGNAL_DIFF_READ_NOT_DONE (noerror) - If a differential view read was requested (i.e., DiffTime was provided) but it could not be for some reason, a "regular" ReadEntries is done and this flag is set.

retDiffTime  -  If non-NULL, returned time to use in subsequent differential view read.

retLastModifiedTime  -  If non-NULL, returns NIFLastModifiedTime value.

retSequence  -  Last modified sequence number.



**See Also :**
[NIFReadEntriesExt](./NIFReadEntriesExt.md)
---

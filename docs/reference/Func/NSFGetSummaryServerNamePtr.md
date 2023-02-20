##### Function : Replica Info
##### NSFGetSummaryServerNamePtr - Returns the server name for a specific entry in the replication history summary.
---
```
#include <nsfdb.h>
char FAR * NSFGetSummaryServerNamePtr(

	REPLHIST_SUMMARY *Summary,
	DWORD  Index);
```
**Description :**

This function returns the server name for a specific entry in the replication 
history summary data.  Use NSFDbGetReplHistorySummary() to obtain a handle to 
the replication history summary data.  Use OSLock() to lock this handle to 
obtain a pointer to the data.  Pass this pointer in as the Summary argument of 
this routine.  The returned Server Name pointer is not null-terminated.  
NSFDbGetReplHistorySummary()  returns the length of the server name.


This routine is implemented as a macro:

#define NSFGetSummaryServerNamePtr(Summary, Index) \
   (((char FAR *) Summary) + Summary[Index].ServerNameOffset)

**Parameters :**
Input :
Summary  -  Pointer to the first structure in the replication history summary data.

Index  -  Index into the replication history summary array.  This index is zero-based and indicates which entry in the replication history summary you wish to access.

Output :
(routine)  -  A pointer to the server name component of a replication history summary entry.  This pointer is NOT null terminated.



**See Also :**
[NSFDbGetReplHistorySummary](/reference/Func/NSFDbGetReplHistorySummary)
[NSFGetSummaryFileNamePtr](/reference/Func/NSFGetSummaryFileNamePtr)
[REPLHIST_SUMMARY](/reference/Data/REPLHIST_SUMMARY)
---

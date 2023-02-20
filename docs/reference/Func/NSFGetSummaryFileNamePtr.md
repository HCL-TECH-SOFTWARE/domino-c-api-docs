##### Function : Replica Info
##### NSFGetSummaryFileNamePtr - Returns the database filename for a specific entry in the replication history summary.
---
```
#include <nsfdb.h>
char FAR * NSFGetSummaryFileNamePtr(

	REPLHIST_SUMMARY *Summary,
	DWORD  Index);
```
**Description :**

This routine returns the database filename for a specific entry in the 
replication history summary data.  Use NSFDbGetReplHistorySummary() to obtain a 
handle to the replication history summary data.  Use OSLock() to lock this 
handle to obtain a pointer to the data.  Pass this pointer in as the Summary 
argument of this routine.

This routine is implemented as a macro:

#define NSFGetSummaryFileNamePtr(Summary, Index) \
   (((char FAR *) Summary) + Summary[Index].ServerNameOffset + \
                             Summary[Index].ServerNameLength + 2)

**Parameters :**
Input :
Summary  -  Pointer to the first structure in the replication history summary data.

Index  -  Index into the replication history summary array.  This index is zero-based and indicates which entry in the replication history summary you wish to access.

Output :
(routine)  -  A null-terminated pointer to the database filename component of a replication history summary entry.



**See Also :**
[NSFDbGetReplHistorySummary](/reference/Func/NSFDbGetReplHistorySummary)
[NSFGetSummaryServerNamePtr](/reference/Func/NSFGetSummaryServerNamePtr)
[REPLHIST_SUMMARY](/reference/Data/REPLHIST_SUMMARY)
---

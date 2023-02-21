##### Data Type : Replica Info
##### REPLHIST_SUMMARY - Replication history summary structure in the array returned from NSFDbGetReplHistorySummary
---
```
#include <nsfdb.h>
```
**Description :**

This structure is returned by NSFDbGetReplHistorySummary().  
NSFDbGetReplHistorySummary() returns an array of REPLHIST_SUMMARY structures 
followed by the packed server and database filename data.  This data is in the 
format, <server name>!!<database filename>, with a NULL terminator at the end 
of the database filename.  Use the NSFGetSummaryServerNamePtr() and 
NSFGetSummaryFileNamePtr() macros for accessing the packed data following the 
REPLHISTORY_SUMMARY array.  

**See Also :**
[NSFGetSummaryFileNamePtr](/domino-c-api-docs/reference/Func/NSFGetSummaryFileNamePtr)
[NSFGetSummaryServerNamePtr](/domino-c-api-docs/reference/Func/NSFGetSummaryServerNamePtr)
[NSFDbGetReplHistorySummary](/domino-c-api-docs/reference/Func/NSFDbGetReplHistorySummary)
---

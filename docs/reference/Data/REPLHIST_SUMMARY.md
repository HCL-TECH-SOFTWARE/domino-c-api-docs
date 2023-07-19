##### Data Type : Replica Info
##### REPLHIST_SUMMARY - Replication history summary structure in the array returned from NSFDbGetReplHistorySummary
---
```
#include <nsfdb.h>
```

**Definition :**

typedef struct {
	TIMEDATE ReplicationTime; /* Time returned from last replciation */
	WORD  AccessLevel;  /* Access level at time of replication */
	WORD  AccessFlags;  /* Access flags at time of replication */
	WORD  Direction;  /* NEVER, SEND, RECEIVE */
	DWORD  ServerNameOffset; /* Server name offset in packed data */
	WORD  ServerNameLength; /* Server name length in packed data */
	WORD  FileNameLength; /* File name length in packed data */
	     /* Total server!!file length is */ 
	     /* ServerNameLength + FileNameLength + 2 */
	     /* to compensate for the !! separator */
	WORD  MoreInfo;  /* contains MoreInfo from cache - includes complete 
replication flag */
	WORD  wSpare;  /* Room for growth */
	DWORD  dwSpare;  /* Room for growth */
	     /* Server/file name pairs follow as */
	     /* "<server name>!!<file name>" with */
	     /* NULL after each pairing */
} REPLHIST_SUMMARY;

**Description :**

This structure is returned by NSFDbGetReplHistorySummary().  NSFDbGetReplHistorySummary() returns an array of REPLHIST_SUMMARY structures followed by the packed server and database filename data.  This data is in the format, &lt;server name&gt;!!&lt;database filename&gt;, with a NULL terminator at the end of the database filename.  Use the NSFGetSummaryServerNamePtr() and NSFGetSummaryFileNamePtr() macros for accessing the packed data following the REPLHISTORY_SUMMARY array.  


**See Also :**
[NSFGetSummaryFileNamePtr](/domino-c-api-docs/reference/Func/NSFGetSummaryFileNamePtr)
[NSFGetSummaryServerNamePtr](/domino-c-api-docs/reference/Func/NSFGetSummaryServerNamePtr)
[NSFDbGetReplHistorySummary](/domino-c-api-docs/reference/Func/NSFDbGetReplHistorySummary)
---

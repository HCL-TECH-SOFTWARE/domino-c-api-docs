##### Symbolic Value : Database
##### fINFO_XXX - Definitions for NSFDbGetMultNoteInfo and NSFDbGetMultNoteInfoByUNID. Specify the infomation to return.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	fINFO_NOTEID	  -  Return NoteID

	fINFO_SEQTIME	  -  Return SequenceTime from OID

	fINFO_SEQNUM	  -  Return Sequence number from OID

	fINFO_OID	  -  Return OID (disables SeqTime & number & UNID)

	fINFO_COMPRESS	  -  Compress non-existent UNIDs

	fINFO_UNID	  -  Return UNID

	fINFO_ALLOW_HUGE	  -  Allow the returned buffer to exceed 64k.
Only applicable to NSFDbGetMultNoteInfo.


**Description :**

Definitions for NSFDbGetMultNoteInfo and NSFDbGetMultNoteInfoByUNID. Specify the infomation to return.


**See Also :**
[NSFDbGetMultNoteInfo](/domino-c-api-docs/reference/Func/NSFDbGetMultNoteInfo)
[NSFDbGetMultNoteInfoByUNID](/domino-c-api-docs/reference/Func/NSFDbGetMultNoteInfoByUNID)
[OID](/domino-c-api-docs/reference/Data/OID)
[ORIGINATORID](/domino-c-api-docs/reference/Data/ORIGINATORID)
[UNID](/domino-c-api-docs/reference/Data/UNID)
[UNIVERSALNOTEID](/domino-c-api-docs/reference/Data/UNIVERSALNOTEID)
---

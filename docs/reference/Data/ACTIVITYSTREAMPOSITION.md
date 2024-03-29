##### Data Type : Log
##### ACTIVITYSTREAMPOSITION - Structure for storing activity logging stream position
---
```
#include <log.h>
```

**Definition :**
```
typedef struct{
	NOTEID  NoteID; 
	DWORD  RecordPos;
}ACTIVITYSTREAMPOSITION;
```

**Description :**

This structure is updated by LogEnumActivityStream and used as input by LogSetActivityStreamPosition. Users of the API can save this structure to a note item or file, and restore it to resume processing at the previous stopping position.


**See Also :**
[LogEnumActivityStream](/domino-c-api-docs/reference/Func/LogEnumActivityStream)
[LogSetActivityStreamPosition](/domino-c-api-docs/reference/Func/LogSetActivityStreamPosition)
---

##### Data Type : Log
##### ACTIVITYSTREAMACTION - Callback function for activity logging
---
```
#include <log.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR ACTIVITYSTREAMACTION)(
	const char *DescName, 
	DWORD DescIdx,
	DWORD Flags,
	WORD  PrimaryKey,
    const TIMEDATE* TimeStamp,
	void *pActivityRecord,
	void *pUserData);

**Description :**

This is the datatype of the action routine passed to LogEnumActivityStream.<br>
<br>

<ul>
<ul>DescName - 	The name of the activity type.<br>
<br>
DescIdx - 	The index associated with an activity type. Although there is no permanent association between the value of this field and DescName, it does remain consistent during the lifetime of an activity stream. i.e between calls to LogOpenActivityStream and LogCloseActivityStream <br>
<br>
Flags -  		Flags associated with the record description. See ACTFLAGS_<br>
<br>
PrimaryKey -	If the ACTFLAGS_CHECKPOINTED_RECORD flag is set, this param indicates the 0 based index of the field that is the primary key of the record.<br>
<br>
TimeStamp -	The time that the record was created.<br>
<br>
pActivityRecord  -	Pointer to a buffer containing the record.  This buffer is in the format of an ITEM_TABLE.<br>
<br>
pUserData -	User context information</ul>
</ul>



**See Also :**
[LogEnumActivityStream](/domino-c-api-docs/reference/Func/LogEnumActivityStream)
---

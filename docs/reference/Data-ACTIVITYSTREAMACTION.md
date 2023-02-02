##### Data Type : Log
##### ACTIVITYSTREAMACTION - Callback function for activity logging
---
##### #include <log.h>
**Description :**
This is the datatype of the action routine passed to LogEnumActivityStream.


DescName -  The name of the activity type.

DescIdx -  The index associated with an activity type. Although there is no 
permanent association between the value of this field and DescName, it does 
remain consistent during the lifetime of an activity stream. i.e between calls 
to LogOpenActivityStream and LogCloseActivityStream 

Flags -    Flags associated with the record description. See ACTFLAGS_

PrimaryKey - If the ACTFLAGS_CHECKPOINTED_RECORD flag is set, this param 
indicates the 0 based index of the field that is the primary key of the record.

TimeStamp - The time that the record was created.

pActivityRecord  - Pointer to a buffer containing the record.  This buffer is 
in the format of an ITEM_TABLE.

pUserData - User context information

**See Also :**
[LogEnumActivityStream](D:/md_files/LogEnumActivityStream.md)
---

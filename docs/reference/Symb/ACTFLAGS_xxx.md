##### Symbolic Value : Log
##### ACTFLAGS_xxx - Public activity logging API flags.
---
```
#include <log.h>
```

**Symbolic Values :**

	ACTFLAGS_CHECKPOINTED_RECORD	  -  Used with the ACTIVITYSTREAMACTION callback routine. Indicates that a record is a checkpointed record. Passed via the ActionRoutine

	ACTFLAGS_CHECKPOINT_FINAL	  -  Used with the ACTIVITYSTREAMACTION callback routine. Indicates that a record is the final record in a series of checkpointed records.

	ACTFLAGS_COLLAPSE_CHECKPOINTS	  -  Used with LogOpenActivityStream. Causes the LogEnumActivityStream function to pass only the last known instance of a checkpointed record to the ActionRoutine. Note that this does not imply that all checkpoint records passed will be the final record in the series.

	ACTFLAGS_RECORD_TRUNCATED	  -  Passed via the stream callback function flags argument. Indicates that the record was truncated. Current record size limit is 20K.


**Description :**




**See Also :**
[ACTIVITYSTREAMACTION](/domino-c-api-docs/reference/Data/ACTIVITYSTREAMACTION)
[LogEnumActivityStream](/domino-c-api-docs/reference/Func/LogEnumActivityStream)
[LogOpenActivityStream](/domino-c-api-docs/reference/Func/LogOpenActivityStream)
---

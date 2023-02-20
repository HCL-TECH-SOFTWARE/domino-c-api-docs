##### Function : Log
##### LogOpenActivityStream - Open a stream for activity logging
---
```
#include <log.h>
STATUS LNPUBLIC LogOpenActivityStream(

	void **pStreamCtx,
	const char *ServerName,
	const char *LogPath,
	const char *ActivityName,
	DWORD  Flags,
	const TIMEDATE_PAIR *DateRange);
```
**Description :**

This function opens a stream which is used to read activity logging data

**Parameters :**
Input :

ServerName  -  A pointer to the null-terminated name of the Lotus Domino Server you want to access.  Information on servers is available from the Domino Directory (Server's Address book) using standard NIF and NSF APIs.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass NULL or a pointer to "" (the null string).

LogPath  -  A pointer to the null-terminated log path.

ActivityName  -  A pointer to the null-terminated names of the activity types you wish to extract. Multiple activity names can be concatenated with the "|" character. The "*" character works as a wildcard.  You may also extract all activity types by passing NULL

Flags  -  ACTFLAGS_COLLAPSE_CHECKPOINTS causes only the latest instance of a checkpointed record to be output. Note that this means that records may not be output in sequential order.

DateRange  -  The lower and upper time bounds of the activity you which to process. To process all available records set Lower to TIMEDATE_MINIMUM and Upper to TIMEDATE_MAXIMUM or pass NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully opened activity stream.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


pStreamCtx  -  A pointer to the stream context needed by the other API functions.


**See Also :**
[ACTFLAGS_xxx](/reference/Symb/ACTFLAGS_xxx)
[ACTIVITYSTREAMACTION](/reference/Data/ACTIVITYSTREAMACTION)
[ACTIVITYSTREAMPOSITION](/reference/Data/ACTIVITYSTREAMPOSITION)
[LogCloseActivityStream](/reference/Func/LogCloseActivityStream)
[LogEnumActivityStream](/reference/Func/LogEnumActivityStream)
[LogSetActivityStreamPosition](/reference/Func/LogSetActivityStreamPosition)
---

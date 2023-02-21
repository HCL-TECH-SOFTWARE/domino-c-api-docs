##### Function : Log
##### LogSetActivityStreamPosition - Sets the current position in an open activity logging stream
---
```
#include <log.h>
STATUS LNPUBLIC LogSetActivityStreamPosition(

	void *pStreamCtx,
	const ACTIVITYSTREAMPOSITION *Position,
	DWORD  PositionSize);
```
**Description :**

Sets the stream position so that processing will start at "Position". Position 
should contain values generated from a previous call to LogEnumActivityStream 
in order to ensure validity

**Parameters :**
Input :
pStreamCtx  -  The stream context created by LogOpenActivityStream

Position  -  An ACTIVITYSTREAMPOSITION struct as returned by LogEnumActivityStream

PositionSize  -  The size of the ACTIVITYSTREAMPOSITION as returned by sizeof(ACTIVITYSTREAMPOSITION)

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully set activity stream position.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[ACTIVITYSTREAMPOSITION](/domino-c-api-docs/reference/Data/ACTIVITYSTREAMPOSITION)
[LogEnumActivityStream](/domino-c-api-docs/reference/Func/LogEnumActivityStream)
[LogOpenActivityStream](/domino-c-api-docs/reference/Func/LogOpenActivityStream)
---

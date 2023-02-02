##### Function : Log
##### LogEnumActivityStream - Enumerates the set of server activity records in an activity logging stream
---
##### #include <log.h>
STATUS LNPUBLIC **LogEnumActivityStream(**

	void *pStreamCtx,
	ACTIVITYSTREAMACTION  ActionRoutine,
	void *pUserData,
	ACTIVITYSTREAMPOSITION *Position,
	DWORD  PositionSize);
**Description :**
This function enumerates the set of server activity records that are referenced 
in an activity logging stream.  For every record that is processed in the 
stream, a caller-supplied callback function is called.
**Parameters :**
Input :
pStreamCtx  -  A pointer to the stream context of the open activity logging stream, as returned by LogOpenActivityStream()

ActionRoutine  -  A caller provided function that is called to for every record in the stream

pUserData  -  User provided context information

PositionSize  -  If a position parameter is passed, then this field is required. It should be sizeof(ACTIVITYSTREAMPOSITION). If no position is passed, the value should be set to zero (0).

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully enumerated activity stream.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


Position  -  If desired, a caller provided ACTIVITYSTREAMPOSITION structure will be updated with the position where processing stopped. This structure can be used by LogSetActivityStreamPosition to resume processing at the record indicated by this structure.  Set to NULL if you don't need to save the stream position

**See Also :**
[ACTIVITYSTREAMACTION](D:/md_files/ACTIVITYSTREAMACTION.md)
[ACTIVITYSTREAMPOSITION](D:/md_files/ACTIVITYSTREAMPOSITION.md)
[LogOpenActivityStream](D:/md_files/LogOpenActivityStream.md)
---

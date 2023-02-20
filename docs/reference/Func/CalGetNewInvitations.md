##### Function : iCalendar
##### CalGetNewInvitations - Retrieve invitations in a mailfile that have not yet been responded to.  This returns the number of new invitations as well as optional NOTEID and/or UNID lists.
---
```
#include <calapi.h>
STATUS CalGetNewInvitations(

	DBHANDLE  hDB,
	TIMEDATE*ptdStart,
	char*pszUID,
	TIMEDATE*ptdSince,
	TIMEDATE*ptdretUntil,
	WORD*pwNumInvites,
	MEMHANDLE *phRetNOTEIDs,
	MEMHANDLE *phRetUNIDs,
	void*pReserved,
	DWORD  dwFlags,
	void*pCtx);
```
**Description :**

Retrieve invitations in a mailfile that have not yet been responded to.  This 
returns the number of new invitations as well as optional NOTEID and/or UNID 
lists. This returns only invitations (and delegated invitations), and not 
reschedules, information updates, cancels, etc.  This method does not filter 
out any invitations that have since been canceled/rescheduled, or are otherwise 
out of date.  Once the invitation is accepted, other notices that apply to that 
meeting can be discovered with a call to CalGetUnappliedNotices must be used 
(on a per-UID level).Only invitations for meetings that are current (at least 
one instance starts within the last day or in the future) are returned, 
although the starting time can be specified by the caller to override the 
default.A caller can retrieve only invitations that have arrived since a prior 
call to CalGetNewInvitations by using tdSince and ptdretUntil.If pszUID is 
provided, invitations only for a particular meeting will be returned.  This is 
useful if you are looking for an invitation or invitations that correspond to 
an updated notice that has arrived.  Note: Mutliple invitations might exist for 
a particular UID if that meeting is recurring and you were added to an instance 
or instances after the initial creation.The returned notices are not guaranteed 
to be in any particular order.

**Parameters :**
Input :
hDB  -  The database from which entries are returned.

ptdStart  -  Optional: If provided, only invitations for meetings that occur on or after this time will be returned.Passing in NULL will use the default value (one day before current time).

pszUID  -  Optional: If present only invitations with a matching UID will be returned.  Note: For some repeating meetings there could be multiple invites for the same UID (for separate instances).

ptdSince  -  Optional: Only return invitations that have been received/modified since the provided time.Passing in NULL will return invitations regardless of when they arrived.

ptdretUntil  -  Optional: If provided, this is populated with the time of this method call, which can then be used as the ptdSince argument of a subsequent call.

pReserved  -  RESERVED - MUST be NULL

dwFlags  -  Flags - currently unused

pCtx  -  RESERVED - MUST be NULL

Output :
(routine)  -  Status of the function


pwNumInvites  -  The number of invitaitons returned (and thus also the length of phRetNOTEIDs and/or phRetUNIDs).Ignored if NULL.

phRetNOTEIDs  -  Handle to the returned NOTEID data.  It is the caller's responsibility to free this memory via OSMemoryFree (if non-NULL).  Access the data via casting the result of OSMemoryLock to a (NOTEID*).Ignored if NULL.

phRetUNIDs  -  Handle to the returned UNID data.  It is the caller's responsibility to free this memory via OSMemoryFree (if non-NULL).  Access the data via casting the result of OSMemoryLock to a (UNID*).Ignored if NULL.


**See Also :**
---

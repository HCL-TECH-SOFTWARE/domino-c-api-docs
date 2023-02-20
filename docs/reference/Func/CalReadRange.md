##### Function : iCalendar
##### CalReadRange - Return data for all entries that begin within a specified date range.
---
```
#include <calapi.h>
STATUS CalReadRange(

	DBHANDLE  hDB,
	TIMEDATE  tdStart,
	TIMEDATE  tdEnd,
	DWORD  dwViewSkipCount,
	DWORD  dwMaxReturnCount,
	DWORD  dwReturnMask,
	DWORD  dwReturnMaskExt,
	void *pFilterInfo,
	MEMHANDLE far *hRetCalData,
	WORD far *retCalBufferLength,
	MEMHANDLE far *hRetUIDData,
	DWORD far *retNumEntriesProcessed,
	WORD far *retSignalFlags,
	DWORD  dwFlags,
	void*pCtx);
```
**Description :**

This will return data for all entries that begin within a specified date range, 
with paging capabilities (similar to NIFReadEntries) in cases where there is 
more data than can be returned in a single call. Specifically, this can return 
one or both of:
1) iCalendar generated from view level data about the calendar entries in the 
date range.
2) A list of UIDs for each calendar entry in the date range.

The iCalendar (returned in hRetCalData) contains only view level data. Full 
iCalendar data for entries must be retrieved via calls to CalReadEntry.  For 
recurring entries, this returns a separate VEVENT with a RECURRENCE-ID for each 
instance in the recurring entry that lies within the specified date range.  
Inclusion within a date range is determined by using start time only. If any 
invitations, reschedule notices, countered meetings, or cancelation notices 
appear on your calendar, they will be included in the output. Meetings not on 
your calendar (including delegated, declined, and some canceled/countered 
meetings) will NOT be returned in the output.

The returned VEVENTs will include the UID, as well as output corresponding to 
each of the READ_RANGE_MASK_xxx values defined in this file. Specific 
READ_RANGE_MASK_xxx values can be defined in dwReturnMask and dwReturnMaskExt 
to further control what properties are output. Examples of properties that are 
not included are ATTENDEE, DESCRIPTION, and ATTACH.

UID information (returned in hRetUIDData) is in the form of a handle to a 
textlist (see textlist.h).  This list can be iterated through to get the UID 
for each entry in a date range.

**Parameters :**
Input :
hDB  -  The database from which entries are returned.

tdStart  -  The starting point of the time range.Only events that START on or after this time will be returned and entries that start before this date but span into the range are NOT returned. Start a day early to capture these entries.

tdEnd  -  The ending point of the time range.

dwViewSkipCount  -  How many view entries to skip before reading the collection. To skip no entries, set this argument to 0.
Note: The data returned from this method is returned from a view and there is no guarantee to be a 1-1 match between view entries and VEVENTs in the returned iCalendar data.  As such, ViewSkipCount and retNumViewEntriesReturned are not intended to represent a number of VEVENTs at all, but instead intended only to allow the caller to make a subsequent call to retrieve remaining data continuing from where a previous call.

dwMaxReturnCount  -  The maximum number of entries (VEVENTs) that should be returned. To attempt to read all the entries within the date range, set this argument to 0xFFFFFFFF (MAXDWORD).

dwReturnMask  -  Bits that control what properties about the calendar entries will be returned. The information flags are defined in READ_RANGE_MASK_xxx, and may be OR'ed together to combine functionailty.  Use MAXDWORD to get information about the returned calendar entries.

dwReturnMaskExt  -  Bits that control what properties about the calendar entries will be returned in addition to those defined in dwReturnMask. The information flags are defined in READ_RANGE_MASK2_xxx, and may be OR'ed together to combine functionailty. Use 0 to generate only the commonly used properties from dwReturnMask, use MAXDWORD to generate all available data, or specify only the bits corresponding to desired READ_RANGE_MASK2_xxx data.

pFilterInfo  -  RESERVED - MUST be NULL.

dwFlags  -  Flags to control non-default behavior. Supported: None currently.

pCtx  -  RESERVED - MUST be NULL.

Output :
hRetCalData  -  Handle to the returned iCalendar data.  It is the caller's responsibility to free this memory.  If you are not interested in this information (but only interested in hRetUIDData), set this argument to NULL.

retCalBufferLength  -  The address of a WORD in which the length of the hRetCalData information buffer is returned. If you are not interested in this length, set this argument to NULL. Ignored if hRetCalData is NULL.

hRetUIDData  -  Handle to a textlist (see textlist.h) data representing UIDs found within the range.  If you are not interested in this information, set this argument to NULL.  Once returned, size and/or number of values can be determined by calls to ListGetSize and/or ListGetNumEntries.

retNumEntriesProcessed  -  The address of a DWORD in which the number of processed view entries is returned. If you are not interested in this information, set this argument to NULL. Ignored if hRetCalData is NULL.  Useful as the value of dwViewSkipCount in a subsequent call in case you cannot retrieve all data. This value is NOT guaranteed to match the number of UIDs or VEVENTs in hRetCalData/hRetUIDData.

retSignalFlags  -  The address of a WORD in which various result flags are returned. If one of the the flags represented by SIGNAL_ANY_CONFLICT is set, the collection has changed since it was last read. If the SIGNAL_MORE_TO_DO flag is set, then the end of the collection has not been reached and there exists more information than could fit in the return buffer. In this case, CalReadRange should be called again to retrieve an additional buffer of information. The signal flags are defined in SIGNAL_xxx, and are returned OR'ed together.


**See Also :**
---

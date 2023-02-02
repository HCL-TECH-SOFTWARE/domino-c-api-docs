##### Function : 
##### SchFreeTimeSearch - Searches the schedule database (locally or on a specified server) for free time periods common to a specified list of people.
---
##### #include <schedule.h>
STATUS **SchFreeTimeSearch(**

	const UNID FAR *pApptUnid,
	TIMEDATE FAR *pApptOrigDate,
	WORD  fFindFirstFit,
	DWORD  dwReserved,
	TIMEDATE_PAIR FAR *Interval,
	WORD  Duration,
	LIST FAR *pNames,
	DHANDLE FAR *rethRange);
**Description :**

**Parameters :**
Input :
pApptUnid  -  This is the UNID of an appointment to ignore for the purposes of calculating free time. This is useful when you need to move an appointment to a time which overlaps it.

pApptOrigDate  -  This is the date of the original date of the appointment to ignore for free time calculations. Note that the only reason that this is here is for compatibility with Organizer 2.x gateway. 

fFindFirstFit  -   If this value is equal to TRUE then this routine will return just the first free time interval that fits the duration. The size of this interval will equal to duration.

dwReserved  -  Reserved for future use.  Must be set to 0L.

Interval  -  Pointer to a TIMEDATE_PAIR structure that specifies the range over which the free time search should be performed. In typical scheduling applications, this might be a range of 1 day or 5 days.

Duration  -  How much free time you are looking for, in minutes.

|	pNames  -  Pointer to a list of distinguished names whose schedule should be searched. This list is in TEXT_LIST format without the datatype word. This list can be conveniently built with the textlist package (e.g. List Allocate)

Output :
(routine)  -  (routine)  -  NOERROR - Successfully searched for free time.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethRange  -  Handle for the RANGE of timedate pairs indicating runs of free time.

**See Also :**
[CalCreateEntry](D:/md_files/CalCreateEntry.md)
[CalReadEntry](D:/md_files/CalReadEntry.md)
---

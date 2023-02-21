##### Function : Calendaring and Scheduling
##### SchSrvRetrieveExt - Retrieve a schedule - extended
---
```
#include <schedule.h>
STATUS LNPUBLIC SchSrvRetrieveExt(

	LIST FAR *pClientNames,
	const UNID FAR *pApptUnid,
	TIMEDATE FAR *pApptOrigDate,
	DWORD  dwOptions,
	TIMEDATE_PAIR FAR *pInterval,
	LIST FAR *pNames,
	LIST FAR *pDetails,
	LIST FAR *piCalList,
	char FAR *pszProxyUserName,
	char FAR *pszProxyPassword,
	HCNTNR FAR *rethCntnr);
```
**Description :**

When this call is made on a server, it synchronously retrieves local or remote 
schedules from the proper fanout servers. When this call is made on a client, 
it retrieves only locally available information in busytime.nsf

This container must be deallocated by the caller using SchContainer_Free.

**Parameters :**
Input :
pClientNames  -  List of users making query.

pApptUnid  -  Ignore this UNID in computations.

pApptOrigDate  -  This is the original start date of the appointment to ignore. This is only here for Organizer 2.x compatibility.

dwOptions  -  Option flags:
SCHRQST_COMPOSITE          default if dwOptions is 0
SCHRQST_EACHPERSON       return each person's schedule
SCHRQST_LOCAL                  only look up schedules locally
SCHRQST_FORCEREMOTE force remote even if you are using workstation based email
SCHRQST_EXTFORMAT get busytime in the SCHED_ENTRY_EXT format instead of the normal SCHED_ENTRY format from pre 6 Note: Use does not guarantee that data will be in SCHED_ENTRY_EXT format since we do not convert data from pre 6 servers.

pInterval  -  Pointer to a TIMEDATE_PAIR structure that specifies the range over which the free time search should be performed. In typical scheduling applications this might be a range of 1 day or 5 days.

pNames  -  Pointer to a list of distinguished names whose schedule should be searched. This list is in TEXT_LIST format without the datatype word. This list can be build with the textlist package (e.g. ListAllocate)

pDetails  -  Details

piCalList  -  Call list

pszProxyUserName  -  Proxy user name

pszProxyPassword  -  Proxy password

Output :
(routine)  -  NOERROR - Successfully retrieved a schedule.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethCntnr  -  Handle of the container that results are returned in.


**See Also :**
[SchContainer_Free](/domino-c-api-docs/reference/Func/SchContainer_Free)
[SCHRQST_xxx](/domino-c-api-docs/reference/Symb/SCHRQST_xxx)
[SchRetrieve](/domino-c-api-docs/reference/Func/SchRetrieve)
---

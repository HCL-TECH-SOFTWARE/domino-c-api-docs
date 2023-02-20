##### Function : Calendaring and Scheduling
##### SchContainer_GetRequestExt - Get the first request in a container - extended.
---
```
#include <schgtw.h>
STATUS LNPUBLIC SchContainer_GetRequestExt(

	DHANDLE  hCntnr,
	WORD  wVersion,
	HCNTNROBJ FAR *rethRqst,
	void FAR * FAR *retpRqst,
	LIST FAR * FAR *retpNameList,
	LIST FAR * FAR *repClientNames,
	char FAR * FAR *retpNS,
	LIST FAR * FAR *retpDetails,
	LIST FAR * FAR *retpiCal,
	char FAR * FAR *retpAuthUsername,
	char FAR * FAR *retpAuthPassword);
```
**Description :**

This function is used to get the first request in a container.  It is the 
extended version of SchContainer_GetRequest created to properly query for 
additional info/data.  Requests are used to obtain free time information from a 
foreign system calendaring and scheduling gateway.

**Parameters :**
Input :
hCntnr  -  The container Handle.

wVersion  -  Version of SCHOBJID_RQST_SCHED request to use: 0 = RQST_SCHED_OBJ; 1 = RQST_SCHED_OBJ2.

Output :
(routine)  -  NOERROR - Successfully got the request.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethRqst  -  Points to where we return the handle to the request.

retpRqst  -  Points to where we return the pointer to the request.

retpNameList  -  Points to where we return the list of names to query.

repClientNames  -  Points to list of clients names doing the query.

retpNS  -  Points to name of Lotus Domino Server to chain to.

retpDetails  -  Points to where we return the list of details to query.  May be NULL.

retpiCal  -  Points to where we return the paired list of iCal URLs/Names to query.  May be NULL.

retpAuthUsername  -  Points to the name to use to authenticate with firewall.  May be NULL.

retpAuthPassword  -  Points to password to use to authenticate with firewall.  May be NULL.


**See Also :**
[SchContainer_FreeRequest](/reference/Func/SchContainer_FreeRequest)
---

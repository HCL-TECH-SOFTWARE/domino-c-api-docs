##### Function : OOO
##### OOOStartOperation - It initializes values for each specific user.
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOStartOperation(

	const char *pMailOwnerName,
	const char *pHomeMailServer,
	BOOL  bHomeMailServer,
	DHANDLE  hMailFile,
	OOOCTXHANDLE *hOOOContext,
	OOOCTXPTR **pOOOOContext);
```
**Description :**

This function should be called prior to performing any OOO operation. It 
initializes values for each specific user.  When you are finished with the 
logic of a specific operation you are required to call OOOEndOperation 
routine.For example,to check the state of OOO functionality for a specific user 
you would call OOOStartOperation, OOOGetState, OOOEndOperation. All strings are 
LMBCS strings.The user is required to have a minimum of Editor level access in 
the ACL of their mail file.If OOOStartOperation returns an error any memory 
allocated in the OOOStartOperation call is freed (i.e. calling OOOEndOperation 
on error is not necessary). 

Effeciency Considerations:
For most efficient operation specify all optional parameters (home mail server 
and handle to the users mail file).  
If home mail server is not specified or if the mail file handle is not 
provided, this function will look up this information on the server specified 
in pMailServer parameter.  If that lookup fails it will attempt a look up 
locally on the server where the application is running.  If the second lookup 
fails and handle to the mail file was provided, then a lookup on the server 
where the database is located will be performed. If you would like to suppress 
the extra look ups and limit the look up only to the server which was specified 
in pMailServer parameter use the following ini variable on the server where 
this api/application is running.
SUPRESS_OOO_DIRECTORY_FAILOVER_LOOKUP = 1
When multiple lookups are performed it is typically a sign that there is a 
configuration problem in the domain and an event indicating this will be logged 
to the server console (and DDM).  This event will be generated 5 or more 
minutes apart to avoid flooding the server.

**Parameters :**
Input :
pMailOwnerName  -  Canonical name of the owner of the mail where we are turning on OOO,Mandatory parameter. 
This is a canonical name of the person whose out of office functionality is being turned on. This parameter is a zero terminated string.

pHomeMailServer  -  Canonical name of the server where the lookup for user information should be made (optional).
This parameter contains the canonical name of the server where the users information should be looked up.  If the server name is not specified, the lookup will be performed locally and the directory topology should return information about the user.  If the server name is not a home mail server, an attempt will be made to figure out the home mail server by looking first locally and, if configured, in the extended directory. The lookups can be suppressed by providing the server name in pMailServer parameter and setting the bHomeMailServer parameter to TRUE.  Suppressing lookups is a more efficient option.

bHomeMailServer  -  TRUE if the pMailServer is users home mail(optional). Set it only if you are sure that users home mail server was specified.  If FALSE the look up for users home mail will be performed.

hMailFile  -  Handle to the open mail file (optional).
If the application already has the mail file opened they can pass in a handle for better better efficiency.  If hMailFile was passed in, the caller is responsible for closing the mail file.

Output :
(routine)  -  Return status from this call indicates either success or what the error is. 
NOERROR 			- Successfully perform this function.
This function can return Domino errors.
OOO specific errors:
ERR_OOO_MISSING_PARAM	-  One or more mandatory parameters were not specified


hOOOContext  -  Pointer to the handle of the OOO context.  This handle is used as an argument to OOOEndOperation function.

pOOOOContext  -  Address of a pointer to the OOO context.  This pointer is used as an argument to other functions.  Both OOOCTXHANDLE and OOOCTXPTR are returned from OOOStartOperation, and OOOCTXPTR is used as input to other routines for efficiency to avoid an extra lock on each set/get operation.


**See Also :**
[OOOEndOperation](/domino-c-api-docs/reference/Func/OOOEndOperation)
---

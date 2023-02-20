##### Function : Database
##### NSFGetNSFDB2GroupProperty -  Retrieve DB2-related information about a Domino server
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFGetNSFDB2GroupProperty(

	const char *group,
	DWORD  infotype,
	void far *buffer,
	DWORD *size);
```
**Description :**

This function retrieves DB2-related information about a Domino server.  This 
function is passed the name of a nsfdb2 group,  an identifier for the 
information you wish to obtain, the address of a buffer into which the 
requested data will be returned, and the address of a size variable.


**Parameters :**
Input :
group  -  name of the nsfdb2 group.

infotype  -  specifies a #define from the following: DB2NSF_GROUP_PROPERTY_CLASS


size  -  specifies the size of buffer

Output :
(routine)  -  Return status from this call: 

NOERROR - Successful.

ERR_DB2NSF_BUFFER_TOO_SMALL

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


buffer  -  points to a caller supplied variable / buffer.

size  -  returns the size in bytes of the data returned. 
 if STATUS==ERR_DB2NSF_BUFFER_TOO_SMALL, returns the required size of the buffer


**See Also :**
[NSFDB2GetInfo](/reference/Func/NSFDB2GetInfo)
---

##### Function : Statistics Reporting
##### NSFGetServerStats - Get named statistics from the server.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFGetServerStats(

	char far *ServerName,
	char far *Facility,
	char far *StatName,
	DHANDLE far *rethTable,
	DWORD far *retTableSize);
```
**Description :**

Request the specified information from the named server.  Statistics are 
identified by a Facility name (see STATPKG_xxx for Domino facilities) and a 
Statistic Name.

The value of the statistic is returned in a memory buffer;  the caller is 
responsible for freeing this buffer with OSMemFree().  The format of this 
buffer is the same as the format of the buffer in the STAT_RETURN_BLOCK.  See 
ParseStats routine in the Message Queues chapter of the User Guide for an 
example that parses this buffer.

**Parameters :**
Input :
ServerName  -  Null-terminated string containing the name of the server.

Facility  -  Optional - Null-terminated string containing the name of the facility.  If no facility name is supplied, pass NULL for this argument.

StatName  -  Optional -  Null-terminated string containing the name of the desired statistic.  If no statistic name is supplied, pass NULL for this argument.

Output :
(routine)  -  Return status from this call:

NOERROR - Success

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethTable  -  Handle to the allocated memory block containing the server statistic.  This memory must be freed by the caller.

retTableSize  -  Size of the returned statistic table, in bytes.


**See Also :**
[NSFGetServerLatency](/reference/Func/NSFGetServerLatency)
[STATPKG_xxx](/reference/Symb/STATPKG_xxx)
[StatTraverse](/reference/Func/StatTraverse)
---

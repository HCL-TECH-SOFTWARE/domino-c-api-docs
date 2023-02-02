##### Function : Access Control List
##### ACLGetHistory - Return handle to buffer containing change history strings
---
##### #include <acl.h>
STATUS LNPUBLIC **ACLGetHistory(**

	DHANDLE  hACL,
	DHANDLE far *hHistory,
	WORD far *HistoryCount);
**Description :**
Allocate a buffer and read the change history for this access control list into 
the buffer.  The buffer will contain LMBCS strings, one entry for each change 
history event.  Each LMBCS string is terminated by two NULL characters, for 
example LastString\0\0PreviousString\0\0.  The strings appear in LIFO (last in, 
first out) order.  The number of strings in the buffer is returned at 
*retHistoryCount.  If there is no change history for this ACL, the 
retHistoryCount will be 0 and the buffer handle will be NULLHANDLE.  If there 
are any history strings, the handle to the buffer is returned;  the caller is 
responsible for freeing this memory by calling OSMemFree().
**Parameters :**
Input :
hACL  -  Handle of the ACL.

Output :
(routine)  -  NOERROR - Successfully retrieved history.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


hHistory  -  Handle of memory containing the change history (or NULLHANDLE if there are no change history strings).

HistoryCount  -  Number of strings in the change history (0 if there are no change history strings).

**See Also :**
[NSFDbReadACL](D:/md_files/NSFDbReadACL.md)
---

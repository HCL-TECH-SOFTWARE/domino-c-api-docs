##### Function : Database
##### NSFDbUserNameGet - Get the user name of the user who is accessing the specified database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbUserNameGet(**

	DBHANDLE  hDB,
	char far *retUserName,
	WORD  BufferLength);
**Description :**
This function returns the name of the user who is accessing the specified 
database.  This function is useful in client and server extension manager 
applications in order to obtain the user name of the user performing the 
database operation.  This allows extension manager applications to obtain the 
same user name that is available to database hook drivers.

      Note:  If calling NSFDbOpenExtended with option set to 
DBOPEN_NO_USERINFO, and the client or server extension manager is trapping this 
call, calling NSFDbUserNameGet will return an empty string for the user name. 
**Parameters :**
Input :
hDB  -  Handle to the open database.

BufferLength  -  Length of the retUserName buffer.

Output :
(routine)  -   Return status from this call:

NOERROR - Success

ERR_xxx - Function was not successful.  Use OSLoadString() to interpret the error status as a string that you may display/log for the user.


retUserName  -  Pointer to the buffer in which a null-terminated user name string is returned.  The buffer should have a minimum length of MAXUSERNAME + 1 (see names.h).

**See Also :**
[EM_xxx](D:/md_files/EM_xxx.md)
---

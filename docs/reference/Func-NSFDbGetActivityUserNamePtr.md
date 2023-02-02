##### Function : Database
##### NSFDbGetActivityUserNamePtr - Returns the user name for a specific entry in the database's user session activity array.
---
##### #include <nsfdb.h>
char FAR * **NSFDbGetActivityUserNamePtr(**

	DBACTIVITY_ENTRY *DbActivity,
	int  Index);
**Description :**
This routine returns the user name for a specific entry in the database user 
session activity array.  Use NSFDbGetUserActivity() to obtain a handle to the 
user session activity information.  Use OSLock() to lock this handle to obtain 
a pointer to the data.  Pass this pointer in as the DbActivity argument of this 
routine.

Implemented as a macro:

#define NSFDbGetActivityUserNamePtr(DbActivity, Index) \
   (((char FAR *) DbActivity) + DbActivity[Index].UserNameOffset)
**Parameters :**
Input :
DbActivity  -  Pointer to the first structure in database's user session activity array.

Index  -  Index into the database's user session activity array.  This index is zero-based and indicates which entry in the database's user session activity array you wish to access.

Output :
(routine)  -  A null-terminated pointer to the user name component of a database's user session activity information entry.


**See Also :**
[NSFDbGetUserActivity](D:/md_files/NSFDbGetUserActivity.md)
[DBACTIVITY](D:/md_files/DBACTIVITY.md)
[DBACTIVITY_ENTRY](D:/md_files/DBACTIVITY_ENTRY.md)
---

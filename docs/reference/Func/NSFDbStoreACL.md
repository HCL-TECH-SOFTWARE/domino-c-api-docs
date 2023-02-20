##### Function : Database
##### NSFDbStoreACL - Stores an access control list in a database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbStoreACL(

	DBHANDLE  hDB,
	DHANDLE  hACL,
	DWORD  ObjectID,
	WORD  Method);
```
**Description :**

This function stores an access control list in a database.  As of Notes Release 
4, NSFDbStoreACL displays a password prompt.  This allows you to put your name 
(signature) as confirmation of changes to the ACL.  If you enter your password, 
your name will appear at the bottom of the Access Control List dialog box when 
you open the ACL in Notes.  If you cancel or abort from the password prompt, 
the ACL will be stored, but your name will not appear at the bottom of the 
Access Control List dialog box and the ACL will not be signed.

**Parameters :**
Input :
hDB  -  Handle to the database.

hACL  -  Handle to the access control list.

ObjectID  -  Reserved for future use.  Use 0L.

Method  -  0 to update the exisiting access control list - ie:  the handle to the access control list was obtained by NSFDbReadACL.

1 to store a new access control list - ie:  the handle to the access control list was obtained by ACLCreate.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - success

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[NSFDbReadACL](/reference/Func/NSFDbReadACL)
[ACLCreate](/reference/Func/ACLCreate)
---

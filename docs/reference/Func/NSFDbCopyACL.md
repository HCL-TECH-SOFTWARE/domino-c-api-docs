##### Function : Database
##### NSFDbCopyACL - Copy a database's ACL to another database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCopyACL(

	DBHANDLE  hSrcDB,
	DBHANDLE  hDstDB);
```
**Description :**

This function copies a database's Access Control List (ACL) to another 
database.  The other database need not be a replica or even a copy of the 
original database.  If the source or destination database is remotely located, 
the username associated with the workstation or server executing this function 
must have MANAGER access in the destination database's ACL in order to complete 
this operation.  As of Notes/Domino 6, Extended Access information is copied if 
Extended Access is enabled on the database.

**Parameters :**
Input :
hSrcDB  -  A DBHANDLE to the database to copy from.

hDstDB  -  A DBHANDLE to the database to copy to.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully copied the ACL.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**Sample Usage :**
```

   else
   {
       /* Copy/replica, use src CutoffInterval to calc dst Cutoff */
       OSCurrentTIMEDATE(&replica_info_dst.Cutoff);
       if (TimeDateAdjust(&replica_info_dst.Cutoff, 0, 0, 0,
                    -((int) replica_info_src.CutoffInterval), 0, 0))
           goto Exit;

       if (error_status = NSFDbCopy(db_handle_src, db_handle_dst,
                                    copy_cutoff_td, NOTE_CLASS_ALL))
           goto Exit;
       if (error_status = NSFDbCopyACL(db_handle_src,
                                        db_handle_dst))
           goto Exit;
   }

```
**See Also :**
[NSFDbCopy](/domino-c-api-docs/reference/Func/NSFDbCopy)
[NSFDbCopyTemplateACL](/domino-c-api-docs/reference/Func/NSFDbCopyTemplateACL)
---

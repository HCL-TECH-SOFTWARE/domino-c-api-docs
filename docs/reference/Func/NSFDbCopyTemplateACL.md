##### Function : Database
##### NSFDbCopyTemplateACL - Copy database template's ACL to a new database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCopyTemplateACL(

	DBHANDLE  hSrcDB,
	DBHANDLE  hDstDB,
	char far *Manager,
	WORD  DefaultAccessLevel);
```
**Description :**

This function copies a database template's Access Control List (ACL) to a newly 
created database.  This function copies only the ACL entries of the form [User 
Name] and converts them to the form User Name during the copy.  It also allows 
you to add one username to the new database's ACL with manager access.  

The [-Default-] entry from the template is copied to the -Default- entry in the 
destination ACL.  If the original template does not have a [-Default-] entry,  
you can specify the default access level for the new database.

 NSFDbCopyTemplateACL does not copy the LocalDomainServers and 
OtherDomainServers entries when copying to a remote database.  This is 
consistent with what occurs in the Notes user interface when you copy a 
template ACL to a remote server.

**Parameters :**
Input :
hSrcDB  -  A DBHANDLE to the database template (NTF) to copy from.

hDstDB  -  A DBHANDLE to the new database to copy to.

Manager  -  A pointer to a null-terminated user name you wish to add to the new database's ACL with ACL_LEVEL_MANAGER.  If NULL is used, the user name from the workstation or server configuration where this function is executed, will be added to the ACL. See MAXUSERNAME for the maximum length of a user name.  The user name must be either in canonical fully-qualified form (ie:  CN=John Doe/OU=Documentation/O=WorkSavers) or as a common name (ie:  John Doe).  Do not use abbreviated format.

DefaultAccessLevel  -  If the source template has a [-Default-] entry, then this entry is copied to the -Default- entry in the destination ACL and this parameter is ignored.  If the source template does not have a [-Default-] entry, then this parameter specifies a WORD value containing the ACL_LEVEL_xxx you wish to assign as the new database's -Default- access control level.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully copied Template ACL.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**Sample Usage :**
```

   /* if New DB from a template */

   if (argc == 4 && (copy_type == 'N'
       || copy_type == 'G' || copy_type == 'H'))
   {
       /* If from template, use replicainfo defaults */

       replica_info_dst.Flags |= REPLFLG_IGNORE_DELETES;
       replica_info_dst.CutoffInterval = 90;
       OSCurrentTIMEDATE(&replica_info_dst.Cutoff);
       if (TimeDateAdjust(&replica_info_dst.Cutoff, 0, 0, 0,
                    -((int) replica_info_dst.CutoffInterval), 0, 0))
           goto Exit;

       if (error_status = NSFDbCopy(db_handle_src, db_handle_dst,
                              copy_cutoff_td, NOTE_CLASS_ALLNONDATA))
           goto Exit;
       if (error_status = NSFDbCopyTemplateACL(db_handle_src,
                              db_handle_dst, user_name,
                              ACL_LEVEL_MANAGER))
           goto Exit;
    }

```
**See Also :**
[ACL_LEVEL_xxx](/domino-c-api-docs/reference/Symb/ACL_LEVEL_xxx)
[NSFDbCopyACL](/domino-c-api-docs/reference/Func/NSFDbCopyACL)
---

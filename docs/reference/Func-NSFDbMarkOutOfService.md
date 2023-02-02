##### Function : Clusters
##### NSFDbMarkOutOfService - Marks a database out of service.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbMarkOutOfService(**

	const char far *dbPathPtr);
**Description :**
The NFSDbMarkOutOfService function marks a cluster database out of service for 
remote user sessions by modifying the database option flags to include 
DBOPTION_OUT_OF_SERVICE.   When a call to NFSDbMarkOutOfService is successful,  
the Cluster Manager denies any new user sessions for this database.  This 
restriction is in addition to any restrictions set forth in the database access 
control list (ACL).  The purpose of this function is allow the system 
administrator to perform maintenance on a database without requiring a server 
shutdown or having to use the database ACL to restrict access.

In order to use NFSDbMarkOutOfService with a database on a clustered server, 
the remote Notes user must have at least designer access privileges.  If a 
user's privilege level is insufficient, a database access error is returned.  

Additionally, when called from a remote session, the dbPathPtr argument must 
specify a qualified database network pathname that can be constructed using the 
DNCanonicalize and OSPathNetConstruct C API functions.

The NFSDbMarkOutOfService function affects only databases that reside on Domino 
clusters.  You can mark a database back in service by calling the 
NFSDbMarkInService function.

For more information, see the Domino Administration Help database.
**Parameters :**
Input :
dbPathPtr  -  Address of string containing fully qualified database pathname.

Output :
(routine)  -  If successful,  returns NOERROR; otherwise, returns database access errors.


**Sample Usage :**
```
    ...

    #include <nsfdb.h>
    #include <dname.h>
    #include <osfile.h>
    
    ...

     /* Canonicalize the Servername */
    nError = DNCanonicalize( 0L, NULL, szServerName, 
                                szCanonServerName, MAXUSERNAME, NULL);
             
    /* Construct NetPath */
    nError = OSPathNetConstruct (NULL, (char FAR *)szServerName, 
                                (char FAR *)szDBName, (char FAR 
*)szNetPathName);
    
    /* Mark in service */
    nError = NSFDbMarkOutOfService ( (char FAR *)szNetPathName );

    ...

```
**See Also :**
[DBOPTION_xxx](D:/md_files/DBOPTION_xxx.md)
[DNCanonicalize](D:/md_files/DNCanonicalize.md)
[NSFDbMarkForDelete](D:/md_files/NSFDbMarkForDelete.md)
[NSFDbMarkInService](D:/md_files/NSFDbMarkInService.md)
[OSPathNetConstruct](D:/md_files/OSPathNetConstruct.md)
---

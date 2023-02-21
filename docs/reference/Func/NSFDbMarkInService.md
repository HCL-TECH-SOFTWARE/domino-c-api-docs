##### Function : Clusters
##### NSFDbMarkInService - Marks a database in service for remote user sessions.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbMarkInService(

	const char far *dbPathPtr);
```
**Description :**

The NFSDbMarkInService function marks a cluster database in service by clearing 
the database option flag  DBOPTION_OUT_OF_SERVICE, if set.   When a call to 
NFSDbMarkInService is successful, the Cluster Manager enables users to access 
the database again by removing the "out of service" access restriction.  

Traditional Domino database access control list (ACL) privileges apply under 
all circumstances. In order to use NFSDbMarkInService on a database in a 
cluster, the remote Notes user must have at least designer access privileges 
for the specified database. If a user does not have the proper privileges, a 
database access error is returned.  

Additionally, when called from a remote session, the dbPathPtr argument must 
specify a qualified database network pathname that can be constructed using the 
DNCanonicalize and OSPathNetConstruct C API functions.

The NFSDbMarkInService function only affects databases within a Lotus Domino 
Server cluster.

For more information, see the Domino  Administration Help database.

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
    nError = NSFDbMarkInService ( (char FAR *)szNetPathName );

    ...

```
**See Also :**
[DBOPTION_xxx](/domino-c-api-docs/reference/Symb/DBOPTION_xxx)
[DNCanonicalize](/domino-c-api-docs/reference/Func/DNCanonicalize)
[NSFDbMarkForDelete](/domino-c-api-docs/reference/Func/NSFDbMarkForDelete)
[NSFDbMarkOutOfService](/domino-c-api-docs/reference/Func/NSFDbMarkOutOfService)
[OSPathNetConstruct](/domino-c-api-docs/reference/Func/OSPathNetConstruct)
---

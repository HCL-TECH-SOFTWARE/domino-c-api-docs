##### Function : Clusters
##### NSFDbMarkForDelete - Marks a database for deletion when there are no more user sessions attached to the database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbMarkForDelete(

	const char far *dbPathPtr);
```
**Description :**

The NFSDbMarkForDelete function marks a cluster database for pending deletion. 
The function modifies the database option flags to include 
DBOPTION_MARKED_FOR_DELETE and DBOPTION_OUT_OF_SERVICE.   As a result, when a 
call to NFSDbMarkForDelete is successful,  the Cluster Manager denies any new 
access requests to the database.  After all active users complete their tasks 
and close the database, the Cluster Manager pushes changes to a replica and 
then deletes the database.   

Use this function with extreme caution. It is impossible to programatically 
unmark a database that is marked for deletion by NFSDbMarkForDelete. A marked 
database will be permanently deleted from the server.

Traditional Domino database access privileges apply when using this function.  
In order to use NFSDbMarkForDelete on a database within a cluster, the remote 
Notes user must have at least manager access privileges for the specified 
database; otherwise, a database access error is returned.  Additionally, when 
called from a remote session, the dbPathPtr argument must specify a qualified 
database network pathname that can be constructed using the DNCanonicalize and 
OSPathNetConstruct C API functions.

Only use the NFSDbMarkForDelete function against databases that reside on a 
Lotus Domino Server configured for a cluster.  If the server is not a member of 
a cluster, the "pending deletion" option will be set, but the database will not 
be deleted.  It is the Cluster Manager's responsibility to delete the database 
after it is marked, and the Cluster Manager is only installed on clustered 
Lotus Domino Servers.

For more information, see the Domino 5 Administration Help database.

**Parameters :**
Input :
dbPathPtr  -  Address of string containing the fully qualified database pathname. 

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
    
    /* Warn the user, and mark for delete */
    strcpy (szErrorString,
           "Marking a database for deletion can not be undone.\nDo you wish to 
continue?");
     
    if ( MessageBox (GetFocus(), szErrorString, "Warning!", MB_YESNO) == IDYES)
            nError = NSFDbMarkForDelete ( (char FAR *)szNetPathName );

    ...

```
**See Also :**
[DBOPTION_xxx](/domino-c-api-docs/reference/Symb/DBOPTION_xxx)
[DNCanonicalize](/domino-c-api-docs/reference/Func/DNCanonicalize)
[NSFDbMarkInService](/domino-c-api-docs/reference/Func/NSFDbMarkInService)
[NSFDbMarkOutOfService](/domino-c-api-docs/reference/Func/NSFDbMarkOutOfService)
[OSPathNetConstruct](/domino-c-api-docs/reference/Func/OSPathNetConstruct)
---

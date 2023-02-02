##### Function : Database
##### NSFDbLocateByReplicaID - Locate a database by replica ID.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbLocateByReplicaID(**

	DBHANDLE  hDB,
	DBID far *ReplicaID,
	char far *retPathName,
	WORD  PathMaxLen);
**Description :**
This function takes a database handle (DBHANDLE) to the data directory, or to 
one of its subdirectories, and the replica ID of a database.  It returns an 
expanded path specification for the replica.  The function searches all 
subdirectories of the data directory for the database.

Note: If you are trying to locate a replica on a remote Lotus Domino Server, 
obtain the replica ID of the local database replica with NSFDbReplicaInfoGet, 
build a fully qualified network pathname to the remote server's data directory 
with OSPathNetConstruct, use that path with NSFDbOpen to obtain a handle to the 
data directory, and then pass that handle to NSFDbLocateByReplicaID to get the 
server's pathname for the replica you want.  The network path to that database 
may then be constructed using OSPathNetConstruct.
**Parameters :**
Input :
hDB  -  A handle to a directory.

ReplicaID  -  A pointer to the Replica ID of the database you wish to find in the directory.

PathMaxLen  -  A WORD containing the length of the buffer minus one (1) for the NULL terminator.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully got path specifications for database.

ERR_NOT_DIRECTORY - Handle provided was not a directory.


retPathName  -  The address of a text buffer into which the expanded pathname for the Domino database Replica is returned.  The pathname is returned as a null-terminated string.  The buffer should be declared with a length of MAXPATH.

**Sample Usage :**
```
 
        if (error_status = NSFDbOpen(src_datadir, &db_handle_dir))
            goto Exit;

        cleanup_state += CLOSE_DIR_DB;

        if (error_status = NSFDbLocateByReplicaID(db_handle_dir,
                             &replica_info_dst.ID, path_by_replid,
                             sizeof(path_by_replid)-1))
        {
            if(ERR(error_status) != ERR_NOEXIST)
                goto Exit;
        }
        else
        {
            printf("\nGiven: %s Matched with: %s by Replica ID\n",
                   dst_expandedpath, path_by_replid);
            printf("Note- Match path is relative to Notes Data\n");
            printf("Directory, NOT to the directory supplied.\n");
        }
        cleanup_state -= CLOSE_DIR_DB;
        if (error_status = NSFDbClose(db_handle_dir))
            goto Exit;

    }
```
**See Also :**
[NSFDbPathGet](D:/md_files/NSFDbPathGet.md)
[NSFDbOpen](D:/md_files/NSFDbOpen.md)
[OSGetDataDirectory](D:/md_files/OSGetDataDirectory.md)
[OSPathNetConstruct](D:/md_files/OSPathNetConstruct.md)
---

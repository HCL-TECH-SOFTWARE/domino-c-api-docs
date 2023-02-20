##### Function : Replication
##### ReplicateWithServer - Replicate with a server from a local system.
---
```
#include <repl.h>
STATUS LNPUBLIC ReplicateWithServer(

	char far *PortName,
	char far *ServerName,
	WORD  Options,
	WORD  NumFiles,
	const char far *FileList,
	REPLSERVSTATS far *retStats);
```
**Description :**

This routine replicates Domino database files on the local system with a 
specified server.  Either all common files can be replicated or a specified 
list of files can be replicated.  The number of file names is specified in the 
parameter NumFiles.  The file names must be concatenated into a single list, 
with each name terminated by a NUL ('\0') character.

Replication can be performed in either direction or both directions (push, 
pull, or both).

Note:
    The REPLSERVSTATS data structure must be initialized to zeros to get the 
correct results; see example below.

**Parameters :**
Input :
PortName  -   Name of the port on which to access the server.  Specify NULL to allow Domino or Notes to use the "most available" port to the given server.

ServerName  -  Name of server to replicate with.    A hierarchical server name needs to be specified in the abbreviated hierarchical name format (such as ServerC/Operations/Acme).

Options  -  Replication options.  These options are defined in REPL_OPTION_xxx and may be bitwise or'ed together for combined functionality.  If the option REPL_OPTION_ALL_DBS is specified, all local Domino database files are added to the list of names (if used).  If the option REPL_OPTION_ALL_NTFS is specified, all local Domino template files are added to the list of names.  If the option REPL_OPTION_ALL_FILES is specified, both database and template files are added.  The priority flags, REPL_OPTION_PRI_LOW, REPL_OPTION_PRI_MED, and REPL_OPTION_PRI_HI, are only meaningful if one of the flags REPL_OPTION_ALL_DBS, REPL_OPTION_ALL_NTFS, or REPL_OPTION_ALL_FILES is specified.

NumFiles  -  Number of files in the file list.  If no file names are specified, this parameter should be set to 0.

FileList  -  (Optional)  A pointer to the concatenated null-terminated database filenames to replicate;  may be NULL.

Output :
(routine)  -  Return status from this call: 

NOERROR - Data replication succeeded.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


retStats  -   Pointer to the returned replication statistics structure.


**Sample Usage :**
```
memset( &retStats, '\0', sizeof(REPLSERVSTATS) );
error = ReplicateWithServer(
   PORTNAME,
   ServerName, 
   REPL_OPTION_RCV_NOTES | REPL_OPTION_SEND_NOTES,  /* pull, push */
   1,
   DBName,
   &retStats))
```
**See Also :**
[ReplicateWithServerExt](/reference/Func/ReplicateWithServerExt)
[REPLSERVSTATS](/reference/Data/REPLSERVSTATS)
[REPL_OPTION_xxx](/reference/Symb/REPL_OPTION_xxx)
---

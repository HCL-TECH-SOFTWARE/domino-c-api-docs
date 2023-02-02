##### Function : Database
##### NSFDbQuotaGet - Return the database quotas.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbQuotaGet(**

	const char far *Filename,
	DBQUOTAINFO far *retQuotaInfo);
**Description :**
This function returns the specified database quota information.  This 
information is also available from the Notes user interface by choosing menu 
items File - Tools - Server Administration to bring up Domino Administrator.  
Next, click on the File tab and select a database, then choose Files - Quotas 
from the menu to see the quota settings dialog.
**Parameters :**
Input :
Filename  -  A pointer to the pathname of a Notes database. The string must be null-terminated.

For a database: The directory part of the path may be omitted if the database is in the Notes data directory.  If the database is on a remote server, a full network pathname must be built with OSPathNetConstruct.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully obtained quota information.

ERR_NO_SERVER_ACCESS - You are not authorized to use the server.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


retQuotaInfo  -  Pointer to the returned DBQUOTAINFO structure.  This structure contains the warning threshold, database size limit, current database size, and maximum database size.  If no warning threshold is set, zero is returned for the WarningThreshold member of this structure.  If no database size limit is set, zero is returned for the SizeLimit member of this structure.  This structure is allocated by the caller.

**Sample Usage :**
```
char        *path_name;          /* pathname of database */
  STATUS      error = NOERROR;
  DBQUOTAINFO  dbQuotaStruct;
  char szErrorString[256];
   
/*  Program initialization */
/*  ...                    */            

  /* Get the DB Quota information */
  error = NSFDbQuotaGet(path_name, &dbQuotaStruct);
  if (error)
  {
    OSLoadString(0, ERR(error), szErrorString, 255);
    printf ("Error from NSFDbQuotaGet:  %s\n\n", szErrorString);
  }
  else
  {
    printf("WarningThreshold:  %lu      SizeLimit:  %lu\n",
           dbQuotaStruct.WarningThreshold, dbQuotaStruct.SizeLimit);
    printf("CurrentSize  %lu      MaxDbSize:  %lu\n",
           dbQuotaStruct.CurrentDbSize, dbQuotaStruct.MaxDbSize);
  }
/*  Program termination */
/*  ...                    */ 

```
**See Also :**
[DBQUOTAINFO](D:/md_files/DBQUOTAINFO.md)
[NSFDbQuotaSetExt](D:/md_files/NSFDbQuotaSetExt.md)
---

##### Function : Database
##### NSFDbQuotaSetExt - Set Database Quotas
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbQuotaSetExt(

	const char far *Filename,
	DWORD  Flags,
	DBQUOTAINFO far *QuotaInfo);
```
**Description :**

This function sets the specified database quota information.  This information 
can also be set using the Notes user interface by choosing menu items File - 
Tools - Server Administration to bring up Domino Administrator.  Next, click on 
the File tab and select a database, then choose Files - Quotas from the menu to 
see the quota settings dialog.

**Parameters :**
Input :
Filename  -  A pointer to the pathname of a Domino database. The string must be null-terminated.

For a database: The directory part of the path may be omitted if the database is in the data directory.  If the database is on a remote server, a full network pathname must be built with OSPathNetConstruct.

Flags  -  Must be zero.

QuotaInfo  -  Pointer to a DBQUOTAINFO structure.  You may only change the database warning threshold and size limit.  Specify DBQUOTA_NOT_SPECIFIED for a field you do not wish to change, and for any unused fields.  This structure is allocated by the caller.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully obtained quota information.

ERR_NO_SERVER_ACCESS - You are not authorized to use the server.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**Sample Usage :**
```
char        *path_name;          /* pathname of database */
	STATUS      error = NOERROR;
DBQUOTAINFO  dbQuotaStruct;
char szErrorString[256];

/* Set the DB Quota information */
dbQuotaStruct.WarningThreshold = 580;
dbQuotaStruct.SizeLimit = 600;
dbQuotaStruct.CurrentDbSize = DBQUOTA_NOT_SPECIFIED;
dbQuotaStruct.MaxDbSize = DBQUOTA_NOT_SPECIFIED;

error = NSFDbQuotaSetExt(path_name, 0, &dbQuotaStruct);
if (error)
{
 OSLoadString(0, ERR(error), szErrorString, 255);
 printf ("Error from NSFDbQuotaSetExt:  %s\n\n", szErrorString);
}
```
**See Also :**
[DBQUOTAINFO](/reference/Data/DBQUOTAINFO)
[NSFDbQuotaGet](/reference/Func/NSFDbQuotaGet)
---

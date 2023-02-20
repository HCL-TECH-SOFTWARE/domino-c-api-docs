##### Function : Database
##### NSFGetChangedDBs - Get the changed databases that have occurred on the server since SinceTime
---
```
#include <nsfdb.h>
STATUS far PASCAL NSFGetChangedDBs(

	char *ServerName,
	TIMEDATE *SinceTime,
	DWORD *ChangesSize,
	DHANDLE *hChanges,
	TIMEDATE *NextSinceTime);
```
**Description :**

Get the changed databases that have occurred on the server since SinceTime

**Parameters :**
Input :
ServerName  -  name of server to check for changed dbs on (failover will not happen with this API)

SinceTime  -  list of dbs located in rethChanges will only be populated with dbs that have been modified since this time 

Output :
(routine)  -  NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


ChangesSize  -  Size in bytes of the value represented by hChanges

hChanges  -  Returned list of dbs that have changed since SinceTime.

NextSinceTime  -  New Since Time


**Sample Usage :**
```
char	 *server_name;                /* server name where database lives*/
TIMEDATE SinceTime,NextSinceTime;
STATUS      error = NOERROR;             /* error code from API calls */
DWORD   ChangesSize;
DHANDLE  hChanges=NULLHANDLE;
char	 *pChanges;
char	 DbPath[MAXPATH] = {0};
int	 i=0;
DWORD  PathLen = 0;


if ( error = NSFGetChangedDBs(server_name, &SinceTime, 
      &ChangesSize, &hChanges, &NextSinceTime))
{
    goto exit;
    
}
if (  (error == NOERROR) && (ChangesSize > 0) && (hChanges != NULLHANDLE))
{
	pChanges = OSLock(char,hChanges);     
	strcpy(DbPath, pChanges);
	printf(" Get modifed dbs list that have occurred on the server since 
SinceTime:\n");
	while(ChangesSize>0)
	{
	 i=i++;
	 strcpy(DbPath, pChanges);
	 PathLen = strlen(DbPath) + 1;
	 pChanges += PathLen;
	 ChangesSize -= PathLen;
	 printf ("%d, %s\n",i,DbPath);
	}
	  
	OSUnlock(hChanges);

}
else 
{
	printf ("------ No Modified dbs found\n");
}

```
**See Also :**
[ConvertTextToTIMEDATE](/reference/Func/ConvertTextToTIMEDATE)
[NSFDbOpenExtended](/reference/Func/NSFDbOpenExtended)
---

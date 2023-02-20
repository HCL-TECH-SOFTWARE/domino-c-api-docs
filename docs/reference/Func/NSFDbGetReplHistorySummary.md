##### Function : Replica Info
##### NSFDbGetReplHistorySummary - Return the replication history summary information.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetReplHistorySummary(

	DBHANDLE  hDb,
	DWORD  Flags,
	DHANDLE *rethSummary,
	DWORD *retNumEntries);
```
**Description :**

This function returns the replication history summary information in an array 
of REPLHIST_SUMMARY structures.  The array of  REPLHIST_SUMMARY structures is 
followed by the packed server and database filename data.  This data is in the 
format, <server name>!!<database filename>, with a NULL terminator at the end 
of the database filename.

If there is no summary information, this function returns ERR_SPECIAL_ID.

This function returns information that is also available from the Notes user 
interface via the File/Replication/History menu item selection.  

**Parameters :**
Input :
hDb  -  A handle to the open Domino database.

Flags  -  Optional history summary flags enabling you to specify that wildcard entries are not to be returned and/or that sorting is to be done by date rather than by the default, server name.  The flags may be OR'ed together to achieve the desired affect.  See REPLHIST_xxx for the available flags.  Specify, 0L, if no flags are desired.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully obtained replication history summary information.

ERR_SPECIAL_ID - No Replication History Summary was found in this database.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


rethSummary  -  Handle to the returned summary information.  The rethSummary is an array of REPLHIST_SUMMARY structures followed by the packed server and database filename data.  The number of returned REPLHIST_SUMMARY structures is returned in *retNumEntries.  Use OSLock() to obtain a pointer to the first structure in the array.  Use the NSFGetSummaryServerNamePtr() and NSFGetSummaryFileNamePtr() macros for accessing the packed data following the REPLHISTORY_SUMMARY array.  Be sure to free this memory by calling OSMemFree() when done.

retNumEntries  -  Pointer to the returned number of replication history summary entries.


**Sample Usage :**
```
STATUS     error = NOERROR;          /* error code from API calls */
DHANDLE      hReplHist;
REPLHIST_SUMMARY ReplHist;
REPLHIST_SUMMARY *pReplHist;
char        szTimedate[MAXALPHATIMEDATE+1];
WORD        wLen;
DWORD       dwNumEntries, i;
char *pServerName;                    /* terminating NULL not included */
char szServerName[MAXUSERNAME + 1];
char *pFileName;                      /* includes terminating NULL */
char szDirection[10];                 /* NEVER, SEND, RECEIVE */

/* Open the database */
...

/* Get the Replication History Summary */
error = NSFDbGetReplHistorySummary (db_handle, 0, &hReplHist, &dwNumEntries);
if (error)
{
  NSFDbClose (db_handle);
  LAPI_RETURN (ERR(error));
}
/* Obtain a pointer to the first member of the Replication History Summary
   array */
pReplHist = OSLock (REPLHIST_SUMMARY, hReplHist);
for (i = 0; i < dwNumEntries; i++)
{
  ReplHist = pReplHist[i];
  error = ConvertTIMEDATEToText (NULL, NULL, &(ReplHist.ReplicationTime),
                               szTimedate, MAXALPHATIMEDATE, &wLen);
  if (error)
  {
    OSUnlock (hReplHist);
    OSMemFree (hReplHist);
    NSFDbClose (db_handle);
    LAPI_RETURN (ERR(error));
  }
  szTimedate[wLen] = '\0';
  if (ReplHist.Direction == DIRECTION_NEVER)
    strcpy (szDirection, "NEVER");
  else if (ReplHist.Direction == DIRECTION_SEND)
    strcpy (szDirection, "SEND");
  else if (ReplHist.Direction == DIRECTION_RECEIVE)
    strcpy (szDirection, "RECEIVE");
  else
    strcpy (szDirection, "");

  pServerName = NSFGetSummaryServerNamePtr (pReplHist, i);
  strncpy (szServerName, pServerName, ReplHist.ServerNameLength);
  szServerName[ReplHist.ServerNameLength] = '\0';
  /* FileName will be NULL terminated */
  pFileName = NSFGetSummaryFileNamePtr (pReplHist, i);
  printf ("%s  %s %s (%s)\n", szTimedate, szServerName, pFileName, szDirection);
}
OSUnlock (hReplHist);
OSMemFree (hReplHist);
```
**See Also :**
[NSFGetSummaryFileNamePtr](/reference/Func/NSFGetSummaryFileNamePtr)
[NSFGetSummaryServerNamePtr](/reference/Func/NSFGetSummaryServerNamePtr)
[REPLHIST_SUMMARY](/reference/Data/REPLHIST_SUMMARY)
---

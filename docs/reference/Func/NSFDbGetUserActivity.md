##### Function : Database
##### NSFDbGetUserActivity - Return the database user activity summary information.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetUserActivity(

	DBHANDLE  hDB,
	DWORD  Flags,
	DBACTIVITY far *retDbActivity,
	DHANDLE far *rethUserInfo,
	WORD far *retUserCount);
```
**Description :**

This function returns the database user activity summary information.  The 
total of the usage statistics for the prior day, week, and month, and since 
user activity recording began is returned in the retDbActivity structure.  The 
number of documents a user or server read or wrote during each session, with 
the most recent activity first is returned in an array of DBACTIVITY_ENTRY 
structures.  The array of  DBACTIVITY_ENTRY structures is followed by a 
parallel array of NULL- terminated user name strings.

If there is no summary information, this function returns ERR_SPECIAL_ID.

This function returns information that is also available from the Notes user 
interface via the File/Database/Properties menu item, Information tab, Activity 
section, User Detail button selection.  

**Parameters :**
Input :
hDB  -  A handle to the open Domino database.

Flags  -  Reserved for future use.  Specify 0L.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully obtained user activity information

ERR_SPECIAL_ID - No user activity information was found in this database.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


retDbActivity  -  Pointer to the returned DBACTIVITY structure.  This structure contains the total of the usage statistics for the prior day, week, and month, and since user activity recording began.  This structure is allocated by the caller.

rethUserInfo  -  Handle to the returned user session activity information.  This information consists of the number of documents a user or server read or wrote during each session.  The rethUserInfo is an array of DBACTIVITY_ENTRY structures followed by a parallel array of NULL-terminated user name strings.  The number of returned DBACTIVITY_ENTRY structures is returned in *retUserCount.  Use OSLock() to obtain a pointer to the first structure in the array.  Use the NSFDbGetActivityUserNamePtr() macro for accessing the user name for each DBACTIVITY_ENTRY.  Be sure to free this memory by calling OSMemFree() when done.

retUserCount  -  Pointer to the returned number of database activity entries (DBACTIVITY_ENTRY structures).


**Sample Usage :**
```
  /* Get the database activity summary.  The database has already been opened. 
*/
{
   DBACTIVITY DbSummaryActivity;
   DBACTIVITY_ENTRY  *pDbUserActivity, DbUserActivity;
   DHANDLE hDbUserActivity;
   WORD wUserCount;
   char *szUserName;
   LONG lRptPeriod;

   error = NSFDbGetUserActivity (db_handle, 0L, &DbSummaryActivity,
                                 &hDbUserActivity, &wUserCount);
   if (error)
   {
      NSFDbClose (db_handle);
      LAPI_RETURN (ERR(error));
   }

  /* Obtain a pointer to the first structure in an array of
     DBACTIVITY_ENTRY structures.  The user names follow the array */

  pDbUserActivity = OSLock (DBACTIVITY_ENTRY, hDbUserActivity);
  for (i = 0; i < wUserCount; i++)
  {
    DbUserActivity = pDbUserActivity[i];
    error = ConvertTIMEDATEToText (NULL, NULL, &(DbUserActivity.Time),
                                 szTimedate, MAXALPHATIMEDATE, &wLen);
    if (error)
    {
      OSUnlock (hDbUserActivity);
      OSMemFree (hDbUserActivity);
      NSFDbClose (db_handle);
      LAPI_RETURN (ERR(error));
    }

    szTimedate[wLen] = '\0';
    szUserName = NSFDbGetActivityUserNamePtr (pDbUserActivity, i);
    /* print out DBACTIVITY_ENTRY Info */
    if (DbUserActivity.Reads)
       printf ("%s  %s read %d\n", szTimedate, szUserName,
               DbUserActivity.Reads);
    if (DbUserActivity.Writes)
       printf ("%s  %s wrote %d\n", szTimedate, szUserName,
               DbUserActivity.Writes);

  }

  OSUnlock (hDbUserActivity);
  OSMemFree (hDbUserActivity);
  /* Now print the DBACTIVITY summary info */
  printf ("\n\n");
  printf ("                 Uses         Reads        Writes\n");
  printf("Last Day        %5d         %5d         %5d\n",
          DbSummaryActivity.PrevDayUses,DbSummaryActivity.PrevDayReads,
          DbSummaryActivity.PrevDayWrites);
  printf("Last Week       %5d         %5d         %5d\n",
          DbSummaryActivity.PrevWeekUses,DbSummaryActivity.PrevWeekReads,
          DbSummaryActivity.PrevWeekWrites);
  printf("Last Month      %5d         %5d         %5d\n",
          DbSummaryActivity.PrevMonthUses,DbSummaryActivity.PrevMonthReads,
          DbSummaryActivity.PrevMonthWrites);
  lRptPeriod = TimeDateDifference (&(DbSummaryActivity.Last),
                                   &(DbSummaryActivity.First));
  /* Convert from seconds to days */
  if (lRptPeriod % (60*60*24))
    lRptPeriod = lRptPeriod / (60*60*24) + 1;
  else
    lRptPeriod = lRptPeriod / (60*60*24);

  printf("Last %lu days   %5d         %5d         %5d\n", lRptPeriod,
          DbSummaryActivity.Uses,DbSummaryActivity.Reads,
          DbSummaryActivity.Writes);

/* close the database when done. */
```
**See Also :**
[DBACTIVITY](/domino-c-api-docs/reference/Data/DBACTIVITY)
[DBACTIVITY_ENTRY](/domino-c-api-docs/reference/Data/DBACTIVITY_ENTRY)
[NSFDbGetActivityUserNamePtr](/domino-c-api-docs/reference/Func/NSFDbGetActivityUserNamePtr)
---

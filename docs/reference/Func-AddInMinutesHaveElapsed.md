##### Function : AddIn
##### AddInMinutesHaveElapsed - Determine if a number of minutes has elapsed.
---
##### #include <addin.h>
BOOL LNPUBLIC **AddInMinutesHaveElapsed(**

	DWORD  Minutes);
**Description :**
AddInMinutesHaveElapsed is used to schedule processing at regular intervals.  
Correct operation of this function depends on AddInIdle being called 
regularly.  The algorithm used is as follows:
     Let itime = the time at which the Add-In program was started
     Let mins = the specified # of minutes (argument 1)
     Let stime = the earliest time after itime that is evenly divisible by mins.
Then, this routine will return TRUE if the current time is later then stime, 
FALSE otherwise.

It is implemented as macro using AddInSecondsHaveElapsed:
#define AddInMinutesHaveElapsed(x) AddInSecondsHaveElapsed((DWORD)(x)*60L)
**Parameters :**
Input :
Minutes  -  The time interval to check for, in minutes.

Output :
(routine)  -  TRUE if the specified number of minutes has elapsed.  See long description for a definition of the algorithm used.


**Sample Usage :**
```
else if (AddInMinutesHaveElapsed(1))
{
  /* Execute the "every minute" instructions */
  min_double += 1.0;
  AddInSetStatus(MSG_SMKADDN_ONEMINUTE, 0L);
  AddInFormatError(error_msg, MSG_SMKADDN_ONEMINUTE, 0L);
  AddInLogMsg(MSG_SMKADDN_NAMESTUB, error_msg);
  DosSleep(5000L);

  /* Create a 3 string arg error_msg from 3 numeric values*/
  sprintf(scratch_str1, "%lf", day_double);
  sprintf(scratch_str2, "%lf", min_double);
  sprintf(scratch_str3, "%lf", sec_double/20.0);
  AddInFormatError(error_msg, MSG_SMKADDN_STATS,
                   scratch_str1, scratch_str2, scratch_str3);
  AddInLogMsg(MSG_SMKADDN_NAMESTUB, error_msg);
  if (min_double > 1L)
  {
    /* There might be several minutes worth of import    */
    /* activity initiated here and AddInShouldTerminate()*/
    /* calls could be blended in among buffered I/O calls*/
    if(AddInShouldTerminate())
      break;
    /* Application shuts itself off after 5 minutes     */
    /* A "Program" note in the server's Name & Address  */
    /* Book could be used to restart this AddIn on a    */
    /* regularly scheduled basis.                       */
    else if(min_double == 5L)
      break;
  }
}
```
**See Also :**
[AddInSecondsHaveElapsed](D:/md_files/AddInSecondsHaveElapsed.md)
[AddInDayHasElapsed](D:/md_files/AddInDayHasElapsed.md)
[AddInIdle](D:/md_files/AddInIdle.md)
---

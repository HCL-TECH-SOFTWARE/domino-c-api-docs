##### Function : AddIn
##### AddInSecondsHaveElapsed - Determine if a number of seconds has elapsed.
---
##### #include <addin.h>
BOOL LNPUBLIC **AddInSecondsHaveElapsed(**

	DWORD  Seconds);
**Description :**
AddInSecondsHaveElapsed is used to schedule processing at regular intervals.  
Correct operation of this function depends on AddInIdle being called 
regularly.  

	The algorithm used is as follows:
     Let itime = the time at which the Add-In program was started
     Let mins = the specified # of minutes (argument 1)
     Let stime = the earliest time after itime that is evenly divisible by 
seconds.
Then, this routine will return TRUE if the current time is later then stime, 
FALSE otherwise.
**Parameters :**
Input :
Seconds  -  The time interval to check for in seconds.

Output :
(routine)  -  TRUE if the specified interval (in seconds) has elapsed.


**Sample Usage :**
```

      else if (AddInSecondsHaveElapsed(20))
       {
           /* Execute the "every 20 seconds" instructions */
           sec_double += 20.0;
           AddInSetStatus(MSG_SMKADDN_TWENTYSECOND, 0L);
           AddInFormatError(error_msg, MSG_SMKADDN_TWENTYSECOND, 0L);
           AddInLogMsg(MSG_SMKADDN_NAMESTUB, error_msg);
           DosSleep(5000L);

           /* Create a 3 string arg error_msg from 3 numeric values*/
           sprintf(scratch_str1, "%lf", day_double);
           sprintf(scratch_str2, "%lf", min_double);
           sprintf(scratch_str3, "%lf", sec_double/20.0);
           AddInFormatError(error_msg, MSG_SMKADDN_STATS,
                           scratch_str1, scratch_str2, scratch_str3);
           AddInLogMsg(MSG_SMKADDN_NAMESTUB, error_msg);
       }
   
```
**See Also :**
[AddInIdle](D:/md_files/AddInIdle.md)
[AddInDayHasElapsed](D:/md_files/AddInDayHasElapsed.md)
[AddInShouldTerminate](D:/md_files/AddInShouldTerminate.md)
[AddInMinutesHaveElapsed](D:/md_files/AddInMinutesHaveElapsed.md)
---

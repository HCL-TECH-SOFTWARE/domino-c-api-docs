##### Function : AddIn
##### AddInDayHasElapsed - Return TRUE once a day.
---
##### #include <addin.h>
BOOL LNPUBLIC **AddInDayHasElapsed(**
void);
**Description :**
AddInDayHasElapsed is used primarily to check for when it is time to do daily 
housekeeping chores.  The routine will return TRUE the first time it is called 
after the AddIn has started, and then once each day (at 2:00 AM GMT) 
thereafter.  

Note: the routine AddInIdle must also be called regularly (at least as often as 
this API is called) in order for this API to work properly.

**Parameters :**

Output :
(routine)  -  TRUE the first time the routine is called, and thereafter, TRUE if it is the first call after 2:00 AM Greenwich Mean Time  (GMT) since the last time the routine returned TRUE.  FALSE otherwise.


**Sample Usage :**
```

       if (AddInDayHasElapsed())
       {
           day_double += 1.0;
           /* Execute the "daily" instructions */
           AddInSetStatus(MSG_SMKADDN_ONCEADAY, 0L);
           AddInFormatError(error_msg, MSG_SMKADDN_ONCEADAY, 0L);
           AddInLogMsg(MSG_SMKADDN_NAMESTUB, error_msg);
           DosSleep(5000L);

           /* Create a 3 string arg error_msg from 3 numeric values*/
           sprintf(scratch_str1, "%lf", day_double);
           sprintf(scratch_str2, "%lf", min_double);
           sprintf(scratch_str3, "%lf", sec_double/20.0);
           AddInFormatError(error_msg, MSG_SMKADDN_STATS,
                          scratch_str1, scratch_str2, scratch_str3);
           AddInLogMsg(MSG_SMKADDN_NAMESTUB, error_msg);
           sprintf(item_name, "%s", "AddInEvents");
           if (error_status = LogAddTextlistItem(log_entry,
                                            LOG_LEAVE_LOCKED,
                                            item_name, error_msg))
               goto Exit;
       }
```
**See Also :**
[AddInIdle](D:/md_files/AddInIdle.md)
[AddInSecondsHaveElapsed](D:/md_files/AddInSecondsHaveElapsed.md)
[AddInMinutesHaveElapsed](D:/md_files/AddInMinutesHaveElapsed.md)
[AddInShouldTerminate](D:/md_files/AddInShouldTerminate.md)
---

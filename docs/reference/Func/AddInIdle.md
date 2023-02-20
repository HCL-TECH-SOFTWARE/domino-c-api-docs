##### Function : AddIn
##### AddInIdle - Yield processor and check if termination required.
---
```
#include <addin.h>
BOOL LNPUBLIC AddInIdle(
void);
```
**Description :**

Use this function to control the main loop of a custom Lotus Domino Server 
add-in task. AddInIdle suspends the calling task and gives control to Domino. 
AddInIdle returns FALSE to indicate that the add-in task should continue.  
AddInIdle returns TRUE when the add-in task should terminate, normally after 
the Lotus Domino Server receives a "quit", "tell <taskname> quit", or "exit" 
command.  Add-in tasks must call AddInIdle in the main loop in order for the 
functions AddInDayHasElapsed, AddInSecondsHaveElapsed, and 
AddInMinutesHaveElapsed to work properly.  In addition, to ensure that "tell 
<taskname> quit" is processed properly and that a console operator does not 
have to wait for an extended period for a task to terminate, any other "delay" 
or "sleep" functions should not impose a delay of more than 5 seconds.  
Developers of server add-ins are responsible for checking the server status 
every 5 seconds to see if it is time to quit for every add-in. Using a single 
add-in task to do the checking and passing that info along to other processes 
is not sufficient as some process aren't responding to requests to dump memory 
or to terminate.

Use AddInShouldTerminate to test for the termination condition without 
suspending the calling task or returning control to Domino.

If you are writing messages to the Domino Server or Notes client log file, then 
you should call AddInIdle or AddInIdleDelay on a regular bases.  This will 
flush log entries from memory to disk and will free up memory.

**Parameters :**

Output :
(routine)  -  TRUE if addin should terminate, FALSE if OK to continue



**Sample Usage :**
```
while (!AddInIdle())
{
  /* Default idle in task stats */
  AddInSetStatus(MSG_SMKADDN_IDLE, 0L);

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
                                          item_name,
                                          error_msg))
      goto Exit;
  }
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
      /* There might be serveral minutes worth of import    */
      /* activity initiated here and AddInShouldTerminate() */
      /* calls could be blended in among buffered I/O calls */
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
}
```
**See Also :**
[AddInDayHasElapsed](/reference/Func/AddInDayHasElapsed)
[AddInMain](/reference/Func/AddInMain)
[AddInMinutesHaveElapsed](/reference/Func/AddInMinutesHaveElapsed)
[AddInSecondsHaveElapsed](/reference/Func/AddInSecondsHaveElapsed)
[AddInShouldTerminate](/reference/Func/AddInShouldTerminate)
[AddInIdleDelay](/reference/Func/AddInIdleDelay)
---

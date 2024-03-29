##### Function : AddIn
##### AddInIdleDelay - Yield processor for specified time, and check if termination required
---
```
#include <addin.h>
BOOL LNPUBLIC AddInIdleDelay(

	DWORD  Delay);
```
**Description :**

AddInIdleDelay checks to see if the add-in process should terminate, then 
suspends the process for the number of milliseconds specified by the Delay 
argument, giving other Lotus Domino Server tasks a chance to process.  
AddInIdleDelay returns TRUE if the add-in task should terminate and FALSE if 
the add-in task should continue.

AddInIdleDelay provides the same functionality as AddInIdle but with the added 
flexibility of the Delay argument.

Use AddInIdleDelay if your add-in task needs control over the amount of time it 
is suspended.  To ensure that "tell <taskname> quit" is processed properly and 
that a console operator does not have to wait for an extended period for a task 
to terminate, the delay should be limited to 1 to 5 seconds.  Developers of 
server add-ins are responsible for checking the server status every 5 seconds 
to see if it is time to quit for every add-in. Using a single add-in task to do 
the checking and passing that info along to other processes is not sufficient 
as some process aren't responding to requests to dump memory or to terminate.

AddInIdleDelay returns TRUE immediately, without suspending the calling task, 
if the calling task should terminate.

If you are writing messages to the Domino Server or Notes client log file, then 
you should call AddInIdle or AddInIdleDelay on a regular bases.  This will 
flush log entries from memory to disk and will free up memory.

**Parameters :**
Input :
Delay  -  Time, in milliseconds, to delay processing, giving other tasks a chance to process

Output :
(routine)  -  TRUE if addin should terminate, FALSE if OK to continue



**Sample Usage :**
```
/*If no events are pending, sleep for a while and check the quit flag.  */

if (DQNonePending)
{
  if (AddInIdleDelay(3000))
  {
    fEventShutdown = TRUE;
    break;
  }
  continue;
}
```
**See Also :**
[AddInIdle](/domino-c-api-docs/reference/Func/AddInIdle)
[AddInMain](/domino-c-api-docs/reference/Func/AddInMain)
[AddInShouldTerminate](/domino-c-api-docs/reference/Func/AddInShouldTerminate)
---

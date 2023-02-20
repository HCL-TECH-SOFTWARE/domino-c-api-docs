##### Function : AddIn
##### AddInCreateStatusLine - Creates a new status line for a server add-in task, returning a descriptor handle
---
```
#include <addin.h>
DHANDLE LNPUBLIC AddInCreateStatusLine(

	char far *TaskName);
```
**Description :**

This function creates a new status line for a server add-in task and returns 
the handle to the new status line descriptor.  This handle is used in calls to 
AddInSetDefaults(), AddInSetStatusLine(), and AddInDeleteStatusLine().  This 
function is only supported within the context of a server add-in.

A status line is one line of text displayed by the Lotus Domino Server console 
in response to the "show tasks" command.  Each status line consists of a task 
name (in the left column) and a status string (in the right column).  The 
TaskName input parameter  to AddInCreateStatusLine() becomes the task name that 
appears in the left column of the status line. The String input parameter to 
AddInSetStatusLine() becomes the status string in the right column of the 
status line.

Domino will create a default status line for those API server add-in tasks that 
use AddInMain() as the main entry point.  These programs need not create, set, 
or delete the default status line.  Server add-in tasks that do not use 
AddInMain() as the main entry point  must create a Lotus Domino Server's status 
line with this function after the Domino run time system is initalized.  
Alternatively, they may create a default status line by using 
AddInQueryDefaults(), AddInCreateStatusLine(), and AddInSetDefaults().  It is 
not mandatory for a server add-in task to have a default status line unless it 
must use routines, such as AddInSetStatus() or AddInSetStatusText(), that 
require a default status line.  In addition, server add-in tasks that do not 
use AddInMain() as the main entry point must call AddInDeleteStatusLine() upon 
termination in order to deallocate the status line created by 
AddInCreateStatusLine().

Use AddInQueryDefaults() to access the module handle and the default status 
line associated with the current server add-in task. Use AddInSetDefaults() to 
set or change the default status line.  Use AddInSetStatus() or 
AddInSetStatusText() to change the status string in the default status line.  
Use AddInSetStatusLine() to change the status string of a specified status 
line. 

The default status line for a server add-in task that does not use string 
resources and uses AddInMain() as the main entry point, uses the first 20 
characters of the program name as specified to the "load" command or in the 
ServerTasks line in notes.ini as the task name.  In order to change the task 
name, the program must call AddInQueryDefaults(), AddInDeleteStatusLine(), 
AddInCreateStatusLine(), and finally AddInSetDefaults().  It does not need to 
call AddInDeleteStatusLine() again because the bootstrap code that calls 
AddInMain() will deallocate the default status line.

Server add-in tasks under Windows that use AddInMain() as the main entry point 
may specify their task name for the default status line by defining a string 
table. Domino will set the task name in the default status line to the first 
string specified in the add-in module's string table. Therefore, server add-in 
tasks under Windows that use AddInMain() as the main entry point normally do 
not call AddInCreateStatusLine() unless multiple status lines are desired.

Server add-in tasks may create multiple status lines. The Lotus Domino Server 
"show tasks" command displays all status lines so created.  Call 
AddInDeleteStatusLine() before termination to deallocate additional status 
lines.

Note:  In Release 3.x, this function did not require any parameters on some 
platforms.  Beginning with Release 4.0, this function requires an input 
parameter on all platforms.

**Parameters :**
Input :
TaskName  -  The task name that appears in the left column of the status line.

Output :
(routine)  -  Status line descriptor handle



**Sample Usage :**
```
AddInQueryDefaults (&hMod, &hOldStatusDescriptor);

AddInDeleteStatusLine (hOldStatusDescriptor);

hStatusDescriptor = AddInCreateStatusLine ("Sample Addin");

AddInSetDefaults (hMod, hStatusDescriptor);

AddInSetStatusText ("Initializing");
```
**See Also :**
[AddInDeleteStatusLine](/reference/Func/AddInDeleteStatusLine)
[AddInQueryDefaults](/reference/Func/AddInQueryDefaults)
[AddInSetDefaults](/reference/Func/AddInSetDefaults)
[AddInSetStatus](/reference/Func/AddInSetStatus)
[AddInSetStatusLine](/reference/Func/AddInSetStatusLine)
[AddInSetStatusText](/reference/Func/AddInSetStatusText)
[AddInMain](/reference/Func/AddInMain)
---

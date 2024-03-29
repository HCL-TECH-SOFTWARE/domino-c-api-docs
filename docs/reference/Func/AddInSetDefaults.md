##### Function : AddIn
##### AddInSetDefaults - Set the calling task's module handle and default status line
---
```
#include <addin.h>
void LNPUBLIC AddInSetDefaults(

	HMODULE  hNewModule,
	DHANDLE  hDesc);
```
**Description :**

This function sets the calling task's module handle and default status line 
descriptor in the per-task data structure maintained by Domino.  This function 
is only supported within the context of a server add-in.

Domino maintains certain per-task data about each server add-in task. This 
per-task data includes the task's module handle and the default status line.  
AddInSetDefaults() allows a server add-in task to set the module handle and the 
default status line maintained by Domino in this per-task data structure.

A status line is one line of text displayed by the Lotus Domino Server console 
in response to the "show tasks" command.  Each status line consists of a task 
name (in the left column) and a status string (in the right column).  

Domino will create a default status line for those API server add-in tasks that 
use AddInMain() as the main entry point.  These programs need not create, set, 
or delete the default status line.  Server add-in tasks that do not use 
AddInMain() as the main entry point  must create must create a status line.  
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

The default status line for a server add-in task that does not use string 
resources and uses AddInMain() as the main entry point, uses the first 20 
characters of the program name as specified to the "load" command or in the 
ServerTasks line in notes.ini as the task name.  In order to change the task 
name, the program must call AddInQueryDefaults(), AddInDeleteStatusLine(), 
AddInCreateStatusLine(), and finally AddInSetDefaults().  It does not need to 
call AddInDeleteStatusLine() again because the bootstrap code that calls 
AddInMain() will deallocate the default status line.

A sub-task started by a server add-in task may call AddInSetDefaults() to set 
the sub-task's per-task data to that of the parent add-in task. Note that the 
parent server add-in task must pass this information as input to the sub-task 
initially in order for the sub-task to call this function. A sub-task may need 
to set its per-task data to that of its parent so that the sub-task may use the 
parent's string resources (for example, via AddInLogMsg) and to set the add-in 
task's status (via AddInSetStatus).

**Parameters :**
Input :
hNewModule  -  The module handle to save in the per-task data of the calling task.

hDesc  -  The status line descriptor to save as the default status line for the calling task.



**Sample Usage :**
```

AddInQueryDefaults (&hMod, &hOldStatusDescriptor);

AddInDeleteStatusLine (hOldStatusDescriptor);

hStatusDescriptor = AddInCreateStatusLine ("Sample Addin");

AddInSetDefaults (hMod, hStatusDescriptor);

AddInSetStatusText ("Initializing");
```
**See Also :**
[AddInQueryDefaults](/domino-c-api-docs/reference/Func/AddInQueryDefaults)
[AddInDeleteStatusLine](/domino-c-api-docs/reference/Func/AddInDeleteStatusLine)
[AddInCreateStatusLine](/domino-c-api-docs/reference/Func/AddInCreateStatusLine)
[AddInLogMsg](/domino-c-api-docs/reference/Func/AddInLogMsg)
[AddInSetStatus](/domino-c-api-docs/reference/Func/AddInSetStatus)
[AddInSetStatusText](/domino-c-api-docs/reference/Func/AddInSetStatusText)
[AddInMain](/domino-c-api-docs/reference/Func/AddInMain)
---

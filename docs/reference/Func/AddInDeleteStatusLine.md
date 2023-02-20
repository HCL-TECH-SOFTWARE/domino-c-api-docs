##### Function : AddIn
##### AddInDeleteStatusLine - Deletes an existing server add-in task status line
---
```
#include <addin.h>
void LNPUBLIC AddInDeleteStatusLine(

	DHANDLE  hDesc);
```
**Description :**

This function deletes the status line specified by the status descriptor 
handle. Obtain the status line descriptor handle by calling 
AddInQueryDefaults() or AddInCreateStatusLine().  This function is only 
supported within the context of a server add-in.

A status line is one line of text displayed by the Lotus Domino Server console 
in response to the "show tasks" command.  Each status line consists of a task 
name (in the left column) and a status string (in the right column).  Use 
AddInDeleteStatusLine() to delete a status line from the list displayed by the 
"show tasks" command.

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

**Parameters :**
Input :
hDesc  -  Status line descriptor handle.  Obtain this descriptor handle by calling  or AddInCreateStatusLine() or AddInQueryDefaults().
Note: NULL this HANDLE out after the AddInDeleteStatusLine(..) call if this HANDLE is to be used again within the server add-in task. 



**Sample Usage :**
```
AddInQueryDefaults (&hMod, &hOldStatusDescriptor);

AddInDeleteStatusLine (hOldStatusDescriptor);

hStatusDescriptor = AddInCreateStatusLine ("Sample Addin");

AddInSetDefaults (hMod, hStatusDescriptor);

AddInSetStatusText ("Initializing");
```
**See Also :**
[AddInQueryDefaults](/reference/Func/AddInQueryDefaults)
[AddInSetDefaults](/reference/Func/AddInSetDefaults)
[AddInCreateStatusLine](/reference/Func/AddInCreateStatusLine)
[AddInSetStatus](/reference/Func/AddInSetStatus)
[AddInSetStatusText](/reference/Func/AddInSetStatusText)
[AddInSetStatusLine](/reference/Func/AddInSetStatusLine)
[AddInMain](/reference/Func/AddInMain)
---

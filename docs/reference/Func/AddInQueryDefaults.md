##### Function : AddIn
##### AddInQueryDefaults - Get addin task's module handle and default status line
---
```
#include <addin.h>
void LNPUBLIC AddInQueryDefaults(

	HMODULE far *rethModule,
	DHANDLE far *rethDesc);
```
**Description :**

This function gets the module handle of the current add-in task, and the 
descriptor handle of the default status line of that task.

Call this function if you need the add-in task's module handle. If you use 
string tables, you may need the add-in task's module handle to load a string 
from the string table via OSLoadString().  

You may also call this function to obtain the handle to the default status 
line. You need the handle to the default status line if you want to change the 
task name.  Use AddInDeleteStatusLine(), AddInCreateStatusLine(), and 
AddInSetDefaults() to do this.

A status line is one line of text displayed by the Lotus Domino Server console 
in response to the "show tasks" command.  Each status line consists of a task 
name (in the left column) and a status string (in the right column). 

Domino will create a default status line for those API server add-in tasks that 
use AddInMain() as the main entry point.  A server add-in tasks that does not 
use AddInMain() as the main entry point must create a status line, but does not 
need to create a default one.  In this case, this function can still be used to 
get the add-in task's module handle.  The module handle is needed if the task 
is to create a default status line.

Use AddInQueryDefaults() to access the module handle and the default status 
line associated with the current server add-in task.  Use AddInSetDefaults() to 
set or change the default status line.  Use AddInSetStatus() or 
AddInSetStatusText() to change the status string in the default status line.

The default status line for a server add-in task that does not use string 
resources and uses AddInMain() as the main entry point, uses the first 20 
characters of the program name as specified to the "load" command or in the 
ServerTasks line in notes.ini as the task name.  In order to change the task 
name, the programs must call AddInQueryDefaults(), AddInDeleteStatusLine(), 
AddInCreateStatusLine(), and finally AddInSetDefaults().  It does not need to 
call AddInDeleteStatusLine() again because the bootstrap code that calls 
AddInMain() will deallocate the default status line.


**Parameters :**

Output :
rethModule  -  address of the returned module handle of the add-in task.

rethDesc  -  address of the returned descriptor handle to the current status line of the add-in task.


**Sample Usage :**
```
HMODULE hModule;
DHANDLE hDesc;
char Name[MAXNAMELEN];
char Version[MAXNAMELEN];

AddInQueryDefaults(&hModule, &hDesc);

if (!OSLoadString(hModule, PKG_ADDIN+0, Name, sizeof(Name)-1))
 Name[0] = 0;

if (!OSLoadString(hModule, PKG_ADDIN+1, Version, sizeof(Version)-1))
 Version[0] = 0;
```
**See Also :**
[AddInCreateStatusLine](/domino-c-api-docs/reference/Func/AddInCreateStatusLine)
[AddInDeleteStatusLine](/domino-c-api-docs/reference/Func/AddInDeleteStatusLine)
[OSLoadString](/domino-c-api-docs/reference/Func/OSLoadString)
[AddInMain](/domino-c-api-docs/reference/Func/AddInMain)
---

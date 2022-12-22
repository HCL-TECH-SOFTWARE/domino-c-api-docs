




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




 


**Function : AddIn**



**AddInDeleteStatusLine** **- Deletes
an existing server add-in task status line**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



void
LNPUBLIC **AddInDeleteStatusLine(**  

      DHANDLE  hDesc**);**



**Description :**



This
function deletes the status line specified by the status descriptor handle.
Obtain the status line descriptor handle by calling AddInQueryDefaults() or
AddInCreateStatusLine().  This function is only supported within the context of
a server add-in.  

  

A status line is one line of text displayed by the Lotus Domino Server console
in response to the "show tasks" command.  Each status line consists
of a task name (in the left column) and a status string (in the right column). 
Use AddInDeleteStatusLine() to delete a status line from the list displayed by
the "show tasks" command.  

  

Domino will create a default status line for those API server add-in tasks that
use AddInMain() as the main entry point.  These programs need not create, set,
or delete the default status line.  Server add-in tasks that do not use AddInMain()
as the main entry point  must create a Lotus Domino Server's status line with
this function after the Domino run time system is initalized.  Alternatively,
they may create a default status line by using AddInQueryDefaults(),
AddInCreateStatusLine(), and AddInSetDefaults().  It is not mandatory for a
server add-in task to have a default status line unless it must use routines,
such as AddInSetStatus() or AddInSetStatusText(), that require a default status
line.  In addition, server add-in tasks that do not use AddInMain() as the main
entry point must call AddInDeleteStatusLine() upon termination in order to
deallocate the status line created by AddInCreateStatusLine().


 


**Parameters :**



Input :  

hDesc  -  Status line descriptor handle.  Obtain this descriptor handle by
calling  or AddInCreateStatusLine() or AddInQueryDefaults().  

Note: NULL this HANDLE out after the AddInDeleteStatusLine(..) call if this
HANDLE is to be used again within the server add-in task.   

  




 


 **Sample Usage :**


AddInQueryDefaults
(&hMod, &hOldStatusDescriptor);  

  

AddInDeleteStatusLine (hOldStatusDescriptor);  

  

hStatusDescriptor = AddInCreateStatusLine ("Sample Addin");  

  

AddInSetDefaults (hMod, hStatusDescriptor);  

  

AddInSetStatusText ("Initializing");


 **See Also :**


**[AddInQueryDefaults](AddInQueryDefaults.md)**


**[AddInSetDefaults](AddInSetDefaults.md)**


**[AddInCreateStatusLine](AddInCreateStatusLine.md)**


**[AddInSetStatus](AddInSetStatus.md)**


**[AddInSetStatusText](AddInSetStatusText.md)**


**[AddInSetStatusLine](AddInSetStatusLine.md)**


**[AddInMain](AddInMain.md)**



----------------------------------------------------------------------------------------------------------


 






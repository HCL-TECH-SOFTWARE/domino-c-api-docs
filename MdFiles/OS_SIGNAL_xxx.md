




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Signal Handler**



**OS\_SIGNAL\_xxx** **-** Signal
handler IDs used by OSGetSignalHandler and OSSetSignalHandler.


**----------------------------------------------------------------------------------------------------------**



**#include <ossignal.h>**


 **Symbolic Values :**      OS\_SIGNAL\_MESSAGE       -  Return address of the function
that can be used to place a text string in the message/status area of the
Status Bar of the workstation's main window. See OSSIGMSGPROC for the prototype
of this function.  

  

      OS\_SIGNAL\_BUSY   -  Return address of the function that paints a busy
indicator on the screen. See OSSIGBUSYPROC for the prototype of this function.  

  

      OS\_SIGNAL\_CHECK\_BREAK           -  Returns a pointer to a function that
checks to see if the user cancelled some I/O. See OSSIGBREAKPROC for the
prototype of this function.  

  

      OS\_SIGNAL\_DIAL    -  Return address of the function that prompts the user
to dial a remote system. Notes calls the signal handler just prior to
initiating the process of an external dial. See OSSIGDIALPROC for the prototype
of this function.  

  

      OS\_SIGNAL\_PROGRESS     -  Put up and manipulate the system wide progress
indicator.  

  

      OS\_SIGNAL\_REPL   -  Signal the replication state.  

  




**Description :**



Type of
signal handler used by OSGetSignalHandler and OSSetSignalHandler to obtain
address of the function that handles the signal.


 **See Also :**


**[IXPostMessage](IXPostMessage.md)**


**[OSSIGMSGPROC](OSSIGMSGPROC.md)**


**[OSSIGBUSYPROC](OSSIGBUSYPROC.md)**


**[OSSIGBREAKPROC](OSSIGBREAKPROC.md)**


**[OSSIGDIALPROC](OSSIGDIALPROC.md)**


**[OSGetSignalHandler](OSGetSignalHandler.md)**


**[OSSetSignalHandler](OSSetSignalHandler.md)**



----------------------------------------------------------------------------------------------------------


 






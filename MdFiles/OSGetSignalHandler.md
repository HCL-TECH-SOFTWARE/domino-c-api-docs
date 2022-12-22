




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




 


**Function : Signal Handler**



**OSGetSignalHandler** **- Returns a
pointer to a signal handler.**


**----------------------------------------------------------------------------------------------------------**



**#include <ossignal.h>**



OSSIGPROC
LNPUBLIC **OSGetSignalHandler(**  

      WORD  SignalHandlerID**);**



**Description :**



This
function returns a pointer to a signal handler.  This function should only be
used in a GUI environment.  Signal handlers are identified by symbolic values; 
please see the description of "OS\_SIGNAL\_xxx" for a list of allowable
values.  

  

For example, "OSGetSignalHandler(OS\_SIGNAL\_MESSAGE)" will return a
valid pointer for the message signal handler only if the function call resides
in a DLL called by the Notes user interface.  Otherwise, NULL is returned.


 


**Parameters :**



Input :  

SignalHandlerID  -  Signal handler ID which can be one of the OS\_SIGNAL\_xxx
values.  

  




Output :  

(routine)  -  Pointer to a signal handler function.  If the signal handler
function is not available for the given signal handler ID, NULL is returned.  

  

  




 **See Also :**


**[IXPostMessage](IXPostMessage.md)**


**[OSSetSignalHandler](OSSetSignalHandler.md)**


**[OS\_SIGNAL\_xxx](OS_SIGNAL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 






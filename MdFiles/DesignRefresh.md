




<!--
 /\* Font Definitions \*/
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




**Initial Release 5.0.3**



**Function : Database**



**DesignRefresh** **- Refresh a
database design from a server's templates.**


**----------------------------------------------------------------------------------------------------------**



**#include <design.h>**



STATUS
LNPUBLIC **DesignRefresh(**  

      char \*Server,  

      DBHANDLE  hDB,  

      DWORD  dwFlags,  

      ABORTCHECKPROC  AbortCheck,  

      OSSIGMSGPROC  MessageProc**);**



**Description :**



This
function will refresh the database design, as allowed by the database/design
properties and access control of Domino,  from a server's templates.  The
refreshed database, if open in Domino or Notes at the time of refresh, must be
closed and reopened to view any changes.


 


**Parameters :**



Input :  

Server  -  A pointer to the null-terminated name of the Lotus Domino Server on
which the database template resides.  The string should be no longer than
MAXUSERNAME.  If you want to specify "no server" (the local machine),
pass a pointer to "" (the null string).  

  

hDB  -  Database handle of the file to be refreshed.  

  

dwFlags  -  Options, please see DESIGN\_xxx for possible values.  NOTE: If
dwFlags is set to 0, the database will be refreshed the first time database
design refresh is requested whether the Design Template has changed, the design
of the database itself has been modified or no changes have been made. 
Subsequent requests to refresh this same database, by calling the function
DesignRefresh with dwFlags set to 0, will take place only if its Design Template
has changed.  

  

AbortCheck  -  Pointer to a user defined callback function that will check
abort status.  NULL if none is desired.  See ABORTCHECKPROC.  

  

MessageProc  -  Pointer to a user defined callback function that will handle
the Message signal.  NULL if none is desired.  See OSSIGMSGPROC.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  




 **See Also :**


**[ABORTCHECKPROC](ABORTCHECKPROC.md)**


**[DESIGN\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/799E25E038F72A8A852568A9005C6050)**


**[OSSIGMSGPROC](OSSIGMSGPROC.md)**



----------------------------------------------------------------------------------------------------------


 






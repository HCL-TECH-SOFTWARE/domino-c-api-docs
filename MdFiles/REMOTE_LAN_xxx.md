




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




**Initial Release 4.5**



**Symbolic Value : Remote LAN adapter**



**REMOTE\_LAN\_xxx** **-** Type of
action that a remote LAN adapter can specify to a Notes status callback
routine.


**----------------------------------------------------------------------------------------------------------**



**#include <net.h>**


 **Symbolic Values :**      REMOTE\_LAN\_INIT\_THREAD         -  Make sure this thread is
known to Notes. Before any status messages can be displayed by Notes by a
thread that is different from the one Notes called the adapter on, you need to
call the Notes remote LAN adapter status callback routine with this Action.  

  

      REMOTE\_LAN\_TERM\_THREAD      -  Decrement the Notes use count on this
thread. If a remote LAN adapter called the Notes remote LAN adapter status
callback routine with the Action parameter set to REMOTE\_LAN\_INIT\_THREAD, once
the connection has been made or if the connection failed, you must call the
Notes remote LAN adapter status callback with the Action parameter set to this
value. The thread init and thread term actions may be called multiple times for
a thread, but the number of termination calls must match the number of init
calls before the thread is terminated.  

  

      REMOTE\_LAN\_DISPLAY\_STATUS   -  Map a Notes status message and display it.
The status message is specified in the StatusCode parameter of the Notes remote
LAN adapter callback routine and is one of the REMOTE\_LAN\_STATUS\_xxx values.  

  

      REMOTE\_LAN\_CHECK\_ABORT       -  Check for a user abort condition. The
Notes remote LAN adapter callback routine returns TRUE if the operation should
continue and FALSE if the user asked for an abort (e.g. ctl+break for a PC, or
command-period for a Macintosh).  

  

      REMOTE\_LAN\_DISPLAY\_ERR0R\_TEXT      -  Display an error message in the
language provided by the remote LAN service. The error string is specified in
the pErrText parameter of the Notes remote LAN adapter callback routine.  

  




**Description :**



These values
are used by a remote LAN adapter in calls to the Notes remote LAN adapter
status callback routine in order to specify what type of action is to be
performed by Notes.


 **See Also :**


**[PREMOTE\_LAN\_STATUS\_CALLBACK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/AF43F4D888713FA785256361003C0CB5)**


**[REMOTE\_LAN\_STATUS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B5DBC1F192673C8985256361003FD569)**



----------------------------------------------------------------------------------------------------------


 






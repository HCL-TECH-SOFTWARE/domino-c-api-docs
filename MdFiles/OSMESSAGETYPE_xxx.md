




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



**OSMESSAGETYPE\_xxx** **-** Message
signal handler specific definitions.


**----------------------------------------------------------------------------------------------------------**



**#include <ossignal.h>**


 **Symbolic Values :**      OSMESSAGETYPE\_OK       -  Display a dialog box with an OK
pushbutton. The Notes message signal handler will return ERR\_OSMESSAGE\_OK.  

  

      OSMESSAGETYPE\_OKCANCEL      -  Display a dialog box with OK and CANCEL
pushbuttons. The Notes message signal handler will return ERR\_OSMESSAGE\_OK if
the OK button was clicked, ERR\_OSMESSAGE\_CANCEL if the CANCEL button was
clicked.  

  

      OSMESSAGETYPE\_YESNO             -  Display a dialog box with YES and NO
pushbuttons. The Notes message signal handler will return ERR\_OSMESSAGE\_YES if
the YES button was clicked, ERR\_OSMESSAGE\_NO if the NO button was clicked.  

  

      OSMESSAGETYPE\_YESNOCANCEL           -  Display a dialog box with YES, NO,
and CANCEL pushbuttons. The Notes message signal handler will return
ERR\_OSMESSAGE\_YES if the YES button was clicked, ERR\_OSMESSAGE\_NO if the NO
button was clicked, ERR\_OSMESSAGE\_CANCEL if the CANCEL button was clicked.  

  

      OSMESSAGETYPE\_RETRYCANCEL           -  Display a dialog box with RETRY
and CANCEL pushbuttons. The Notes message signal handler will return
ERR\_OSMESSAGE\_RETRY if the RETRY button was clicked, ERR\_OSMESSAGE\_CANCEL if
the CANCEL button was clicked.  

  

      OSMESSAGETYPE\_POST  -  Display the server name and a given string in the
message/status area of the Notes Status bar. The Notes message signal handler
will return ERR\_OSMESSAGE\_OK.  

  

      OSMESSAGETYPE\_POST\_NOSERVER       -  Display a given string in the
message/status area of the Notes Status bar. The Notes message signal handler
will return ERR\_OSMESSAGE\_OK.  

  




**Description :**



These
symbolic constants define the type of the dialog box to be displayed when a
message signal handler function (OS\_SIGNAL\_MESSAGE) is called.


 **See Also :**


**[OSSIGMSGPROC](OSSIGMSGPROC.md)**


**[OS\_SIGNAL\_xxx](OS_SIGNAL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 











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




**Initial Release 4.0**



**Symbolic Value : Mail Gateway**



**MAIL\_LOG\_xxx** **-** Mail event
logging flags.


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**


 **Symbolic Values :**      MAIL\_LOG\_TO\_MISCEVENTS         -  Log message to
Miscellaneous Events view.  

  

      MAIL\_LOG\_TO\_MAILEVENTS          -  Log message to Mail Events view.  

  

      MAIL\_LOG\_TO\_EVENTS\_ONLY       -  Don't log messages to console.  

  

      MAIL\_LOG\_TO\_BOTH          -  Log message to both Miscellaneous Events and
Mail Events views.  

  

      MAIL\_LOG\_FORMATTED\_TEXT      -  Text already formatted  

  




**Description :**



Flags that
can be used in MailLogEvent and MailLogEventText to control mail logging.


 **See Also :**


**[MailLogEvent](MailLogEvent.md)**


**[MailLogEventText](MailLogEventText.md)**



----------------------------------------------------------------------------------------------------------


 






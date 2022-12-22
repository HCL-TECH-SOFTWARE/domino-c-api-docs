




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




 


**Symbolic Value : Mail Gateway**



**DELIVERY\_REPORT\_xxx** **-** Type of
delivery reporting option requested.


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**


 **Symbolic Values :**      DELIVERY\_REPORT\_NONE            -  No report requested.  

  

      DELIVERY\_REPORT\_BASIC            -  Basic report (only on failure report)
option requested. Report is sent only if the message could not be delivered.  

  

      DELIVERY\_REPORT\_CONFIRMED              -  Confirmation report option
requested (notify sender that the message was or was not delivered).  

  

      DELIVERY\_REPORT\_TRACE           -  Trace entire path delivery option
requested. A report is sent from each server the message is routed through. The
final report indicates whether Domino delivered the message successfully.  

  

      DELIVERY\_REPORT\_TRACE\_NO\_DELIVER            -  Trace a delivery failure.  

  

      DELIVERY\_REPORT\_CONFIRM\_NO\_DELIVER        -  Confirm a delivery failure.  

  




**Description :**



These
symbolic constants define the type of delivery reporting option requested. 
Used in MailGetMessageInfo function and MAILREC structure.


 **See Also :**


**[MailGetMessageInfo](MailGetMessageInfo.md)**


**[MAILREC](MAILREC.md)**



----------------------------------------------------------------------------------------------------------


 






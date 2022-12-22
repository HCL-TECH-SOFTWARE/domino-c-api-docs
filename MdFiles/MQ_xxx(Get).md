




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



**Symbolic Value : Message Queues**



**MQ\_xxx (Get)** **-** MQGet -
Options


**----------------------------------------------------------------------------------------------------------**



**#include <mq.h>**


 **Symbolic Values :**      MQ\_WAIT\_FOR\_MSG          -  If the specified message queue
is empty, wait for a message to appear in the queue. The Timeout argument to
the MQGet() function call specifies the amount of time to wait for a message.  

  




**Description :**



This is the
list of valid values for the Options argument in a call to the function
MQGet().


 **See Also :**


**[MQGet](MQGet.md)**



----------------------------------------------------------------------------------------------------------


 






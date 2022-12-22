




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




**Initial Release 6**



**Symbolic Value : Message Queues**



**xxxPRIORITY** **-** Signifies
the message priority in a message queue.


**----------------------------------------------------------------------------------------------------------**



**#include <mq.h>**


 **Symbolic Values :**      NOPRIORITY           -  This symbolic value defines the
lowest priority assignable to a message in a message queue. Specifying
NOPRIORITY as the Priority argument in a call to MQPut() means that the message
has no priority at all, and should be placed at the end of the message queue.
This avoids the need for MQPut() to perform a linear search in order to find
the correct position for this message.  

  

      LOWPRIORITY        -  This symbolic value defines the lowest priority
assignable to a message in a message queue. Same as NOPRIORITY.  

  

      HIGHPRIORITY        -  This symbolic value defines the highest priority
assignable to a message in a message queue.  

  




**Description :**



These
symbolic values defines the priorities assignable to a message in a message
queue.


 **See Also :**


**[MQPut](MQPut.md)**



----------------------------------------------------------------------------------------------------------


 











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




 


**Symbolic Value : Network**



**NETOPT\_xxx** **-** Option flags
for Network send and receive functions.


**----------------------------------------------------------------------------------------------------------**



**#include <net.h>**


 **Symbolic Values :**      NETOPT\_SEND\_NOW         -  Option for NetSend. Indicates
that data should be transmitted immediately. Omission of this flag allows data
to be buffered without necessarily being sent. However, buffered data may be
sent at anytime at the discretion of NetSend (or NetReceive).  

  

      NETOPT\_FLUSH      -  Option for NetSend. Indicates that any buffered data
(to be sent or received) should be flushed before this send commences.  

  

      NETOPT\_WAIT\_FOR\_SOME\_DATA             -  Option for NetReceive. Waits
until some data is available and returns as soon as some data is available.  

  

      NETOPT\_WAIT\_FOR\_ALL\_DATA     -  Option for NetReceive. Waits until the specified
amount of data is received. Not to be OR'd with NETOPT\_PEEK\_AT\_DATA.  

  

      NETOPT\_PEEK\_AT\_DATA   -  Option for NetReceive. Peek at the data without
actually removing it from the input stream. Not to be OR'd with
NETOPT\_WAIT\_FOR\_ALL\_DATA.  

  

      NETOPT\_STREAM\_MODE   -  Option for NetSetSessionMode. Places session into
stream mode. The absence of this flag places session into message mode.  

  




**Description :**



These option
flags are used with the Network send and receive functions.  

  

Unless indicated otherwise, the option flags that are appropriate for a
function may be or'd together (bitwise).


 **See Also :**


**[NetSend](NetSend.md)**


**[NetReceive](NetReceive.md)**


**[NetSetSessionMode](NetSetSessionMode.md)**



----------------------------------------------------------------------------------------------------------


 






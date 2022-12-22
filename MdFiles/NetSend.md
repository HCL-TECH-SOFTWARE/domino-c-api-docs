




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




 


**Function : Network Send and Receive**



**NetSend** **- Sends
data over a specified session.**


**----------------------------------------------------------------------------------------------------------**



**#include <net.h>**



STATUS
LNPUBLIC **NetSend(**  

      SESSIONID  SessionID,  

      void far \*Buffer,  

      WORD  Length,  

      WORD  Options**);**



**Description :**



This
function sends data over a specified session.


 


**Parameters :**



Input :  

SessionID  -   A Session ID obtained in a previous call to NetLink.  

  

Buffer  -  Address of buffer containing data to be sent.  

  

Length  -  Size of data to be sent.  

  

Options  -  One of the following flags or the bitwise OR of any of the
following flags:  

NETOPT\_SEND\_NOW - indicates data should be  transmitted immediately.  Omission
of this flag allows data to be buffered without necessarily being sent.  
However, buffered data may be sent at anytime at the discretion of NetSend (or
NetReceive).  

NETOPT\_FLUSH - indicates that any buffered data (to be sent or received) should
be flushed  before this send commences.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Function returned successfully.  

ERR\_TIMEOUT - Function timed out before all the data was transmitted.  Unless
this error is persistent, it should not be treated as a fatal error, and the
session should be continued to be used.  

ERR\_xxx - STATUS returned from a lower-level C API function.  This value can be
passed to OSLoadString to obtain a text string for the error.  This error should
be treated as fatal and the session should be closed by the application via
NetCloseSession.  

  

  




 **See Also :**


**[NetLink](NetLink.md)**


**[NetSetSessionMode](NetSetSessionMode.md)**


**[NetReceive](NetReceive.md)**


**[NetCloseSession](NetCloseSession.md)**



----------------------------------------------------------------------------------------------------------


 






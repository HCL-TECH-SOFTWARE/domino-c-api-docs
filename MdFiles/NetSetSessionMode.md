




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



**NetSetSessionMode** **- Sets
various modes for a network session.**


**----------------------------------------------------------------------------------------------------------**



**#include <net.h>**



STATUS
LNPUBLIC **NetSetSessionMode(**  

      SESSIONID  SessionID,  

      WORD  Options,  

      DWORD  SendTimeout,  

      DWORD  ReceiveTimeout,  

      WORD  NumBuffers,  

      WORD  BufferSize**);**



**Description :**



This
function sets various parameters and modes for sessions, as well as
preallocating a network buffer.  If this function is called more than once (for
a given session), the previous allocated  buffer is deallocated and a new one
allocated.  This means that any bytes being buffered for sends or receives are
lost.


 


**Parameters :**



Input :  

SessionID  -  A Session ID obtained in a previous call to NetLink.  

  

Options  -  One of the following:  

NETOPT\_STREAM\_MODE - Places session into stream mode.  

0 - Places session into message mode.  

  

SendTimeout  -  Default send timeout (10 ms. units).  

  

ReceiveTimeout  -  Default receive timeout (10 ms. units).  

  

NumBuffers  -  Number of network buffers to preallocate.  

  

BufferSize  -  Default buffer size (0 indicates use a driver selected size).  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Function returned successfully.  

ERR\_xxx - STATUS returned from a lower-level C API function.  This value can be
passed to OSLoadString to obtain a text string for the error.  This error
should be treated as fatal and the session should be closed by the application
via NetCloseSession.  

  

  




 **See Also :**


**[NetLink](NetLink.md)**


**[NetSend](NetSend.md)**


**[NetReceive](NetReceive.md)**


**[NetCloseSession](NetCloseSession.md)**



----------------------------------------------------------------------------------------------------------


 






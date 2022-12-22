




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



**NetReceive** **- Receives
data from a remote system.**


**----------------------------------------------------------------------------------------------------------**



**#include <net.h>**



STATUS
LNPUBLIC **NetReceive(**  

      SESSIONID  SessionID,  

      void far \*retBuffer,  

      WORD  Length,  

      WORD  Options,  

      WORD far \*retSize**);**



**Description :**



This
function receives data from a remote system.


 


**Parameters :**



Input :  

SessionID  -  A Session ID obtained in a previous call to NetLink.  

  

Length  -  Size of buffer where data should be returned.  

  

Options  -  One of the following flags or the bitwise OR of any of the
following flags::  

NETOPT\_WAIT\_FOR\_SOME\_DATA - If this flag is specified (and BufferSize > 0), 
this routine waits until some data is available.  However, it returns as soon
as some data is  available, even if the amount of data is less  than
BufferSize.  

NETOPT\_WAIT\_FOR\_ALL\_DATA - If this flag is specified, this routine waits (if
necessary) until BufferSize number of bytes are available.  

NETOPT\_PEEK\_AT\_DATA - This option returns the available data, but doesn't
update the internal count associated with returning the data.  In other words,
the caller can peek at the data, without actually removing it from the input
stream.  The next call will return the same data.  

  

Do not specify both NETOPT\_PEEK\_AT\_DATA and NETOPT\_WAIT\_FOR\_ALL\_DATA. To do so,
may return unpredictable results.  

  

If neither NETOPT\_WAIT\_FOR\_SOME\_DATA nor NETOPT\_WAIT\_FOR\_ALL\_DATA is specified,
this function returns immediately, even if no  data is available.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Function returned successfully.  Check retSize to determine the
number of bytes received (may be zero).  

ERR\_TIMEOUT - Function timed out before any data was received.  Unless this
error is persistent, it should not be treated as a fatal error, and the session
should be continued to be used.  

ERR\_NET\_FLAKEY - A transient network condition has occurred, possibly resulting
in the loss of some incoming data.    The session is still useable.  (Note: on
character mode connections, it is not always possible for the Domino or Notes
software to determine if data is lost, and hence not all instances of lost data
will result in an error being returned.)  

ERR\_xxx - STATUS returned from a lower-level C API function.  This value can be
passed to OSLoadString to obtain a text string for the error.  This error
should be treated as fatal and the session should be closed by the application
via NetCloseSession.  

  

  

retBuffer  -  Address of buffer where data should be returned.  It is the
responsibility of the caller to allocate space for this buffer.  

  

retSize  -  Pointer to returned buffer size.  It is set to number of bytes
received.  

  




 **See Also :**


**[NetLink](NetLink.md)**


**[NetSetSessionMode](NetSetSessionMode.md)**


**[NetSend](NetSend.md)**


**[NetCloseSession](NetCloseSession.md)**



----------------------------------------------------------------------------------------------------------


 






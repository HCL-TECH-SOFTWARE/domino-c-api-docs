




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



**NetLink** **- Creates a
network link to a remote system.**


**----------------------------------------------------------------------------------------------------------**



**#include <net.h>**



STATUS
LNPUBLIC **NetLink(**  

      char far \*pRemoteSystem,  

      char far \*pPortName,  

      char far \*pConnectInfo,  

      void far \*pReservedMustBeNull,  

      SESSIONID far \*pRetSessionId**);**



**Description :**



This
function makes a call to the remote system and establishes a character mode
connection. It binds this network link to a SessionID and returns this session
ID for use in subsequent calls to NetSetSessionMode, NetSend, NetReceive, and
NetCloseSession.   This call is currently supported only over COM ports. It is
intended for character mode connections to foreign systems, such as data
retrieval systems.  

  

Upon successful return from this function, you must call NetSetSessionMode once
to set the session operating parameters before calling NetSend or NetReceive. 
When you are finished with the network session, you must call NetCloseSession
to hangup the phone call and free the resources associated with the session.


 


**Parameters :**



Input :  

pRemoteSystem  -  Pointer to a zero-terminated string naming the remote system
to link to.  May be NULL if both pPortName specifies a port and pConnectInfo
specifies a phone number. If non-NULL, pRemoteSystem must specify the name of a
Lotus Domino Server for which there is a Connection record in the Address book.  

  

pPortName  -  Pointer to a zero-terminated string naming the port to use. If
NULL, NetLink searches the Address Book for the first Connection record
matching the name specified by pRemoteSystem.   

  

pConnectInfo  -  Pointer to a zero-terminated string containing the connection
information (e.g., the phone number) to be used to create a link to the remote
system.  If NULL, NetLink searches the Address Book for the first Connecton
record matching the name specified by pRemoteSystem.   

  

pReservedMustBeNull  -  Reserved for future use.  Must be specified as NULL.  

  




Output :  

(routine)  -   Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Function returned successfully.  

ERR\_xxx - STATUS returned from a lower-level C API function.  This value can be
passed to OSLoadString to obtain a text string for the error.  The session was
not created and does not need to be closed by the application.  

  

  

pRetSessionId  -  Pointer to the returned SESSIONID used to identify the link
to the remote system, and to be used in subsequent calls to NetSetSessionMode,
NetSend,  NetReceive, and NetCloseSession.  This value is valid only if the
routine returns without error.  

  




 **See Also :**


**[NetSetSessionMode](NetSetSessionMode.md)**


**[NetSend](NetSend.md)**


**[NetReceive](NetReceive.md)**


**[NetCloseSession](NetCloseSession.md)**



----------------------------------------------------------------------------------------------------------


 






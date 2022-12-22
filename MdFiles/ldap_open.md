




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



**Function : LDAP**



**ldap\_open** **-
Initialize a session with an LDAP server.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



LDAP
\* LNPUBLIC **ldap\_open(**  

      const char \*host,  

      int  port**);**



**Description :**



This
function initializes a session with an LDAP server and returns a "session
handle," a pointer to an opaque structure that MUST be passed to
subsequent calls pertaining to the session. This routine returns a NULL if the
session cannot be initialized.


 


Unlike
ldap\_init, ldap\_open attempts to make a server connection before returning to
the caller.  A more complete description can be found in RFC 1823.


 


Implemented
as a macro:


 


#define
ldap\_open(host, port)          ND\_ldap\_open((host), (port))


 


**Parameters :**



Input :  

host  -  A space-separated list of hostnames or dotted strings representing the
IP address of hosts running an LDAP server to connect to. Each hostname in the
list MAY include a port number which is separated from the host itself with a
colon (:) character.  The hosts will be tried in the order listed, stopping
with the first one to which a successful connection is made.  

  

Note: A suitable representation for including a literal IPv6[10] address in the
hostname parameter is desired, but has not yet been determined or implemented
in practice.  

  

port  -  The TCP port number to connect to. The default LDAP port of 389 can be
obtained by supplying the value zero (0) or the macro LDAP\_PORT (389).  If a
host includes a port number then this parameter is ignored.  

  




Output :  

(routine)  -  A pointer to a session handle.  

  

NULL - If the session cannot be initialized.  

  

  




 **See Also :**


**[ldap\_init](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D1141CD8AEBBBA9885256F5C00488A5D)**



----------------------------------------------------------------------------------------------------------


 






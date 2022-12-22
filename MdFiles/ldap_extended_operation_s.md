




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



**ldap\_extended\_operation\_s** **- Allow
sychronous extended LDAP operations to be passed to the server.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_extended\_operation\_s(**  

      LDAP \*ld,  

      const char \*exoid,  

      const struct berval \*exdata,  

      LDAPControl \*\*serverctrls,  

      LDAPControl \*\*clientctrls,  

      char \*\*retoidp,  

      struct berval \*\*retdatap**);**



**Description :**



This
function will allow sychronous extended LDAP operations to be passed to the
server, providing a general protocol extensibility mechanism.


 


Implemented
as a macro:


 


#define
ldap\_extended\_operation\_s(ld, exoid, exdata, serverctrls, clientctrls, retoidp,
retdatap) \  

              ND\_ldap\_extended\_operation\_s((ld), (exoid), (exdata),
(serverctrls), (clientctrls), (retoidp), (retdatap))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

exoid  -  The dotted-OID text string naming the request.  

  

exdata  -  The arbitrary data needed by the operation (if NULL, no data is sent
to the server).  

  

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server
controls are to be used.  

  

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no server
controls are to be used.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  

retoidp  -  Pointer to a character string that will be set to an allocated,
dotted-OID text string returned by the server.  This string SHOULD be disposed
of using the ldap\_memfree function.  If an API error occurs or no OID is
returned by the server, \*retoidp is set to NULL.  

  

retdatap  -  Pointer to a berval structure pointer that will be set to an
allocated copy of the data returned by the server.  This struct berval SHOULD
be disposed of using ber\_bvfree.  If an API error occurs or no data is returned
by the server, \*retdatap is set to NULL.  

  




 **See Also :**


**[ber\_bvfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6E60A0A308298A3985256F5C00486F08)**


**[ldap\_memfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F11748459A77A7EE85256F5C00488A7A)**



----------------------------------------------------------------------------------------------------------


 











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



**Function : User Registration**



**SECTokenGenerate** **- Generate
a Single Sign-On Token.**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



STATUS
LNPUBLIC **SECTokenGenerate(**  

      char \*ServerName,  

      char \*OrgName,  

      char \*ConfigName,  

      char \*UserName,  

      TIMEDATE \*Creation,  

      TIMEDATE \*Expiration,  

      MEMHANDLE \*retmhToken,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



Use this
function to generate an authentication token for interoperability with Domino
protocols that support Single Sign-On (IE: HTTP and DIIOP), as well as IBM
WebSphere Advanced Server. The return value retmhToken is a MEMHANDLE that
references an SSO\_TOKEN structure when locked with OSMemoryLock. See SSO\_TOKEN
for more information.


 


Note: this
function will be remoted in a future release.


 


**Parameters :**



Input :  

ServerName  -  Domino server to ask to generate the token (reserved as NULL).  

  

OrgName  -  Organization that the server belongs to (OPTIONAL: Specify NULL if
not using 'Internet Sites' view for configuration)  

  

ConfigName  -  Name of Web SSO Configuration to use.  

  

UserName  -  Canonicalized Notes username to encode in the token.  

  

Creation  -  Creation time to set for the token (specify NULL to use the
current time).  

  

Expiration  -  Expiration time to set for the token (specify NULL to use
expiration from specified Web SSO Configuration).  

  

dwReserved  -  Must be 0 or fSECToken\_EnableRenewal.  If
fSECToken\_EnableRenewal is passed, and vpReserved is not NULL, then the routine
will write to a TIMEDATE pointed to by vpReserved the time at which the Token
does its IdleTimeout (which may be sooner than the value returned by Expiration
if idle timeout is enabled for this LTPA token).  Idle timeout can only be
enabled for Domino style tokens. The Websphere format does not support them. 
See fSECToken\_xxx.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_xxx - Errors returned by lower level functions.  Call OSLoadString to
interpret the error code for display.  

  

  

retmhToken  -  MEMHANDLE to an SSO\_TOKEN structure.  

  

vpReserved  -  If not NULL (see dwReserved), then the routine will write to a
TIMEDATE pointed to by vpReserved the time at which the Token does its
IdleTimeout (which may be sooner than the value returned by Expiration if idle
timeout is enabled for this LTPA token).  Idle timeout can only be enabled for
Domino style tokens. The Websphere format does not support them.    

  




 **See Also :**


**[fSECToken\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8FF777107F660D7B85256D7B005B82BE)**


**[SECTokenFree](SECTokenFree.md)**


**[SECTokenValidate](SECTokenValidate.md)**


**[SSO\_TOKEN](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/ABE1F48EEAFAA02E85256BC10067CE9E)**



----------------------------------------------------------------------------------------------------------


 






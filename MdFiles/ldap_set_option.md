




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**ldap\_set\_option** **- Used to
set LDAP session preferences.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_set\_option(**  

      LDAP \*ld,  

      int  optionToSet,  

      void \*optionValue**);**



**Description :**



This
function is used to set the current value of various session-wide parameters.


 


Note that if
automatic referral following is enabled (the default), any connections created
during the course of following referrals will inherit the options associated
with the session that sent the original request that caused the referrals to be
returned.


 


Implemented
as a macro:


 


#define
ldap\_set\_option(ld, optionToSet, optionValue)           ND\_ldap\_set\_option((ld),
(optionToSet), (optionValue))


 


**Parameters :**



Input :  

ld  -  The session handle.  If this is NULL, a set of global defaults is
accessed.  New LDAP session handles created with ldap\_init or ldap\_open inherit
their characteristics from these global defaults.  

  

optionToSet  -  The name of the option being accessed.  See LDAP\_OPT\_xxx.  

  

optionValue  -  A pointer to the value the option is to be given. The actual
type of this parameter depends on the setting of the option parameter.  

  




Output :  

(routine)  -  0 - Success.  

  

-1 - Error: If -1 is returned by this function, a specific result code MAY be
retrieved by calling ldap\_get\_option() with an option  

value of LDAP\_OPT\_RESULT\_CODE.  Note that there is no way to retrieve a more
specific result code if a call to ldap\_get\_option() with an option  

value of LDAP\_OPT\_RESULT\_CODE fails. When a call to ldap\_set\_option() fails, it
MUST NOT change the state of the LDAP session handle or the state of the
underlying implementation in a way that affects the behavior of future LDAP API
calls.  

  

  




 **Sample Usage :**



    WORD       ldap\_debug\_level
= 0;


 


   
ldap\_debug\_level = LDAP\_DEBUG\_API;


   
ldap\_set\_option (NULL, LDAP\_OPT\_DEBUG\_LEVEL, &ldap\_debug\_level);


 **See Also :**


**[ldap\_get\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/611E3525171346C185256F5C00488A5E)**


**[LDAP\_OPT\_xxx](LDAP_OPT_xxx.md)**



----------------------------------------------------------------------------------------------------------


 






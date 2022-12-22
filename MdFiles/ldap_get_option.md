




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



**ldap\_get\_option** **- Used to
get LDAP session preferences.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_get\_option(**  

      LDAP \*ld,  

      int  optionToGet,  

      void \*optionValue**);**



**Description :**



This
function is used to access the current value of various session-wide
parameters.


 


Note that if
automatic referral following is enabled (the default), any connections created
during the course of following referrals will inherit the options associated
with the session that sent the original request that caused the referrals to be
returned.


 


Implemented
as a macro:


 


#define
ldap\_get\_option(ld, optionToGet, optionValue)          ND\_ldap\_get\_option((ld),
(optionToGet), (optionValue))


 


**Parameters :**



Input :  

ld  -  The session handle.  

  

optionToGet  -  The name of the option being accessed.  See LDAP\_OPT\_xxx.  

  




Output :  

(routine)  -  0 - Success: The implementation MUST NOT change the state of the
LDAP session handle or the state of the underlying implementation in a way that
affects the behavior of future LDAP API calls.  When a call to ldap\_get\_option
fails, the only session handle change permitted is setting the LDAP result code
(as returned by the LDAP\_OPT\_RESULT\_CODE option.)  

  

-1 - Error: If -1 is returned by this function, a specific result code MAY be
retrieved by calling ldap\_get\_option() with an option  

value of LDAP\_OPT\_RESULT\_CODE.  Note that there is no way to retrieve a more
specific result code if a call to ldap\_get\_option() with an option  

value of LDAP\_OPT\_RESULT\_CODE fails.   

  

  

optionValue  -  The address of a place to put the value of the option. The
actual type of this parameter depends on the setting of the option parameter. 
For optionValues of type char \*\* and LDAPControl \*\*, a copy of the data that is
associated with the LDAP session ld is returned; callers should dispose of the
memory by    calling ldap\_memfree or ldap\_controls\_free, depending on the type
of data returned.  

  




 **See Also :**


**[ldap\_controls\_free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA728E830A49FDFD85256F5C00488A7C)**


**[ldap\_memfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F11748459A77A7EE85256F5C00488A7A)**


**[ldap\_set\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9E2625CD7E72282B85256F5C00488A88)**


**[LDAP\_xxx\_INFO\_VERSION](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/817F026AAA38D55B85256ACE006D9D3D)**



----------------------------------------------------------------------------------------------------------


 






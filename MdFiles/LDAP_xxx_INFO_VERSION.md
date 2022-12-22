




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



**Symbolic Value : LDAP**



**LDAP\_xxx\_INFO\_VERSION** **-** LDAP
execution information.


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      LDAP\_API\_INFO\_VERSION              -  A number that
identifies the version of the LDAPAPIInfo structure. See LDAPAPIInfo.  

  

      LDAP\_FEATURE\_INFO\_VERSION   -  A number that identifies the version of
the LDAPAPIFeatureInfo structure. See LDAPAPIFeatureInfo.  

  




**Description :**



When
LDAP\_OPT\_API\_INFO is passed to ldap\_get\_option (see ldap\_get\_option and
LDAP\_OPT\_xxx), the ldapai\_info\_version field of the LDAPAPIInfo or
LDAPAPIFeatureInfo structures SHOULD be set to one of the appropriate values
below, before calling ldap\_get\_option so that it can be checked for
consistency.  


 **See Also :**


**[LDAPAPIFeatureInfo](LDAPAPIFeatureInfo.md)**


**[LDAPAPIInfo](LDAPAPIInfo.md)**


**[ldap\_get\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/611E3525171346C185256F5C00488A5E)**


**[LDAP\_OPT\_xxx](LDAP_OPT_xxx.md)**



----------------------------------------------------------------------------------------------------------


 






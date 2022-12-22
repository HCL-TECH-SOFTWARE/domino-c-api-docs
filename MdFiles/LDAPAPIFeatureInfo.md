




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



**Data Type : LDAP**



**LDAPAPIFeatureInfo** **-** LDAP
structure containing LDAP API feature information.


**----------------------------------------------------------------------------------------------------------**



**#include
<ldap.h>**



**Definition :**



typedef struct
ldap\_apifeature\_info {


        int     ldapaif\_info\_version;


        char    \*ldapaif\_name;


        int     ldapaif\_version;


} LDAPAPIFeatureInfo;


 


**Description :**



LDAP
structure containing some feature information about the LDAP API.


 


The function
ldap\_get\_option can be used with an option parameter value of
LDAP\_OPT\_API\_FEATURE\_INFO to retrieve more feature information about the LDAP
API.  When LDAP\_OPT\_API\_FEATURE\_INFO is passed to ldap\_get\_option, the option
value returned SHOULD be the address of an LDAPAPIFeatureInfo structure.  

  

Note that the ldapaif\_info\_version field of the LDAPAPIFeatureInfo structure SHOULD
be set to the value LDAP\_FEATURE\_INFO\_VERSION and the ldapaif\_name field SHOULD
be set to the extension name string as described below before ldap\_get\_option
is called.  When LDAP\_OPT\_API\_FEATURE\_INFO is passed to ldap\_get\_option, the 
value returned for the ldapaif\_version  field of the LDAPAPIFeatureInfo
structure will be set.  

  

The members of the LDAPAPIFeatureInfo structure are:  

  

ldapaif\_info\_version - A number that identifies the version of the
LDAPAPIFeatureInfo structure.  This SHOULD be set to the value          
LDAP\_FEATURE\_INFO\_VERSION before calling ldap\_get\_option.  If the value
received is not recognized by the LDAP API implementation, the ldap\_get\_option
function sets ldapaif\_info\_version to a valid value that would be recognized
and returns an error without filling in the ldapaif\_version field in the
LDAPAPIFeatureInfo structure.  

  

ldapaif\_name                      - The name of an extension, as returned in
the ldapai\_extensions array of the LDAPAPIInfo structure and as specified in
the document that describes the extension.  See LDAPAPIInfo.  

  




ldapaif\_version                   -
This field will be set as a result of calling ldap\_get\_option with the
LDAP\_OPT\_API\_FEATURE\_INFO option.


 **See Also :**


**[LDAPAPIInfo](LDAPAPIInfo.md)**


**[ldap\_get\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/611E3525171346C185256F5C00488A5E)**


**[LDAP\_xxx\_INFO\_VERSION](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/817F026AAA38D55B85256ACE006D9D3D)**



----------------------------------------------------------------------------------------------------------


 











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



**LDAPAPIInfo** **-** LDAP
structure containing LDAP API information.


**----------------------------------------------------------------------------------------------------------**



**#include
<ldap.h>**



**Definition :**



typedef struct
ldapapiinfo {


        int 
ldapai\_info\_version;     /\* version of this struct (1) \*/


        int 
ldapai\_api\_version;      /\* revision of API supported \*/


        int 
ldapai\_protocol\_version; /\* highest LDAP version supported \*/


        char
\*\*ldapai\_extensions;     /\* names of API extensions \*/


        char
\*ldapai\_vendor\_name;     /\* name of supplier \*/


        int 
ldapai\_vendor\_version;   /\* supplier-specific version times 100 \*/


} LDAPAPIInfo;


 


**Description :**



LDAP
structure containing some basic information about the LDAP API and about the
specific implementation being used.


 


The function
ldap\_get\_option can be used with an option parameter value of LDAP\_OPT\_API\_INFO
to retrieve this basic information about the LDAP API.  The ld parameter to
ldap\_get\_option can be either NULL or a valid LDAP session handle which was
obtained by calling ldap\_init.  When LDAP\_OPT\_API\_INFO is passed to
ldap\_get\_option, the option value returned SHOULD be the address of an
LDAPAPIInfo structure.  

  

Note that the ldapai\_info\_version field of the LDAPAPIInfo structure SHOULD be
set to the value LDAP\_API\_INFO\_VERSION before calling ldap\_get\_option so that
it can be checked for consistency.  All other fields are set by the
ldap\_get\_option function.  

  

The members of the LDAPAPIInfo structure are:  

  

ldapai\_info\_version             - A number that identifies the version of the
LDAPAPIInfo structure.  This SHOULD be set to the value LDAP\_API\_INFO\_VERSION
before calling ldap\_get\_option.  If the value received is not recognized by the
API implementation, the ldap\_get\_option function sets ldapai\_info\_version to a
valid value that would be recognized, sets the ldapai\_api\_version to the
correct value, and returns an error without filling in any of the other fields
in the LDAPAPIInfo structure.


  

ldapai\_api\_version              - A number that matches that assigned to the C
LDAP API RFC supported by the API implementation.  This SHOULD match the value
of the LDAP\_API\_VERSION macro defined earlier.  

  

ldapai\_protocol\_version       - The highest LDAP protocol version supported by
the implementation.  For example, if LDAPv3 is the highest version supported
then this field will be set to 3.  

  

ldapai\_vendor\_name           - A zero-terminated string that contains the name
of the party that produced the LDAP API implementation.  This field may be set
to NULL if no name is available.  If non-NULL, the caller  is responsible for
disposing of the memory occupied by passing this pointer to ldap\_memfree.  

This value SHOULD match the value of the LDAP\_VENDOR\_NAME.  See
LDAP\_VENDOR\_xxx.  

  

ldapai\_vendor\_version        - An implementation-specific version number multiplied
by 100.  For example, if the implementation version is 4.0 then this field will
be set to 400.  If no version information is available, this field will be set
to 0.  This value SHOULD match the value of the LDAP\_VENDOR\_VERSION.  See
LDAP\_VENDOR\_xxx.


 **See Also :**


**[ldap\_get\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/611E3525171346C185256F5C00488A5E)**


**[LDAP\_VENDOR\_xxx](LDAP_VENDOR_xxx.md)**


**[LDAP\_xxx\_INFO\_VERSION](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/817F026AAA38D55B85256ACE006D9D3D)**



----------------------------------------------------------------------------------------------------------


 






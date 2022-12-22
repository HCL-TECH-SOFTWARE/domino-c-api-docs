




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



**LDAPControl** **-** Structure
for holding ldapv3 controls.


**----------------------------------------------------------------------------------------------------------**



**#include
<ldap.h>**



**Definition :**



typedef struct
ldapcontrol {


        char           
\*ldctl\_oid;


        struct
berval   ldctl\_value;


        char           
ldctl\_iscritical;


}  LDAPControl;


 


 


 


**Description :**



LDAPv3
operations can be extended through the use of controls.  Controls can be sent
to a server or returned to the client with any LDAP message. These controls are
referred to as server controls.


 


The LDAP API
also supports a client-side extension mechanism through the use of client
controls. These controls affect the behavior of the LDAP API only and are never
sent to a server.  The LDAPControl data structure is used to represent both types
of controls


 


The fields
in the LDAPControl structure are:  

  

ldctl\_oid                  - The control type, represented as a string.  See
LDAP\_CONTROL\_xxx.  

  

ldctl\_value              - The data associated with the control (if any).  To 
specify a zero-length value, set ldctl\_value.bv\_len to zero and
ldctl\_value.bv\_val to a zero-length string.  To indicate that no data is
associated with the con trol, set ldctl\_value.bv\_val to NULL.  Alternatively,
when the ldctl\_oid is set to LDAP\_CONTROL\_REFERRALS, the flags value can be set
to the value LDAP\_CHASE\_SUBORDINATE\_REFERRALS or to the value
LDAP\_CHASE\_EXTERNAL\_REFERRALS, or the logical OR of the two flag values.  To
create a referrals client control with "automatic chasing".  See
LDAP\_CHASE\_xxx.  

  

ldctl\_iscritical          - Indicates whether the control is critical of not.
If this field is non-zero, the operation will only be carried out if the
control is recognized by the server and/or client.  Note that the LDAP unbind
and abandon operations have no server response, so clients SHOULD NOT mark server
controls critical when used with these two operations.  

  




 **See Also :**


**[LDAP\_CHASE\_xxx](LDAP_CHASE_xxx.md)**


**[LDAP\_CONTROL\_xxx](LDAP_CONTROL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 






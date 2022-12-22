




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



**LDAPMod** **-** Modify an
existing LDAP entry.


**----------------------------------------------------------------------------------------------------------**



**#include
<ldap.h>**



**Definition :**




typedef struct ldapmod 


{


 


    int                           mod\_op;


 


#define LDAP\_MOD\_ADD              0x00


#define LDAP\_MOD\_DELETE   0x01


#define
LDAP\_MOD\_REPLACE  0x02


#define
LDAP\_MOD\_BVALUES  0x80


 


    char                   \*mod\_type;


    mod\_vals\_u\_t   mod\_vals;


 


#define mod\_values mod\_vals.modv\_strvals


#define mod\_bvalues       mod\_vals.modv\_bvals


 


    struct ldapmod \*mod\_next;


 


}  LDAPMod;


 


**Description :**



This
structure is used to modify an existing LDAP entry.


 **See Also :**


**[LDAP\_MOD\_xxx](LDAP_MOD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 






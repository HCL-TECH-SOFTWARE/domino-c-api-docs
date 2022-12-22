




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



**ldap\_explode\_dn** **- Break up
a distinguished name into its component parts.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



char
\*\*LNPUBLIC **ldap\_explode\_dn(**  

      const char \*dn,  

      int  notypes**);**



**Description :**



This
function is used to break up a distinguished name into its component parts.


 


Implemented
as a macro:


 


#define
ldap\_explode\_dn(dn, notypes)         ND\_ldap\_explode\_dn((dn), (notypes))


 


**Parameters :**



Input :  

dn  -  The dn to explode, such as returned by ldap\_get\_dn.  If NULL, a zero
length DN is used.  

  

notypes  -  A boolean parameter.  If non-zero, the dn  components are to have
their type information stripped off (i.e., "cn=Babs" would become
"Babs").  

  




Output :  

(routine)  -  A NULL terminated char \* array containing the RDN components of
the DN supplied, with or without types as indicated by the notypes parameter.
The components are returned in the order they appear in the dn.  The array
returned SHOULD be freed when it is no longer in use by calling
ldap\_value\_free.  

  

  




 **See Also :**


**[ldap\_get\_dn](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BDD0B880523CEAF385256F5C00488A63)**


**[ldap\_value\_free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/69925F36F6F9779185256F5C00488A6D)**



----------------------------------------------------------------------------------------------------------


 






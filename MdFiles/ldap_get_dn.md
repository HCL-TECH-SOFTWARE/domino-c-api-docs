




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



**ldap\_get\_dn** **- Retrieve
the name of an entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



char
\*LNPUBLIC **ldap\_get\_dn(**  

      LDAP \*ld,  

      LDAPMessage \*entry**);**



**Description :**



This
function is used to retrieve the distinguished name of an entry.


 


Implemented
as a macro:


 


#define
ldap\_get\_dn(ld, entry)         ND\_ldap\_get\_dn((ld), (entry))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

entry  -  The entry whose name is to be retrieved, as returned by
ldap\_first\_entry or ldap\_next\_entry.  

  




Output :  

(routine)  -  A pointer to newly allocated space containg the DN.  The caller
SHOULD free this space by calling ldap\_memfree when it is no longer in use. 
Note the root DN is returned as a zero length string ("").  

  

NULL - If there is some error parsing the dn, setting error parameters in the
session handle ld to indicate the error.  

  

  




 **Sample Usage :**



      if (
(sdn = ldap\_get\_dn( ld, e )) != NULL )


      {


         
printf( "\tdn: %s\n", sdn );


         
ldap\_memfree( sdn );


      }


 


 **See Also :**


**[ldap\_dn2ufn](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/61D3E9E91221D46985256F5C00488A64)**


**[ldap\_explode\_dn](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4B8F8D5AFEF02FE285256F5C00488A65)**


**[ldap\_explode\_rdn](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D80DF1F69B345F1885256F5C00488A66)**


**[ldap\_first\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0238B4B4403930DA85256F5C00488A5F)**


**[ldap\_next\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/838CF92EE872121885256F5C00488A60)**



----------------------------------------------------------------------------------------------------------


 






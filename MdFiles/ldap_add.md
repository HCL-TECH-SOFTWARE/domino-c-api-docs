




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



**ldap\_add** **- Initiate
an asynchronous ldap add operation.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_add(**  

      LDAP \*ld,  

      const char \*dn,  

      LDAPMod \*\*attrs**);**



**Description :**



This
function will initiate an asynchronous ldap add operation.


 


Note that
the parent of the entry being added must already exist or the parent must be
empty (i.e., equal to the root DN) for an add to succeed.


 


Implemented
as a macro:


 


#define
ldap\_add(ld, dn, attrs)         ND\_ldap\_add((ld), (dn), (attrs))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

dn  -  The distinguished name of the entry to add.  If NULL, a zero length DN
is sent to the server.  

  

attrs  -  The entry's attributes, specified using the LDAPMod structure defined
for ldap\_modify. The mod\_type and mod\_vals fields MUST be filled in.  The
mod\_op field is ignored unless ORed with the constant LDAP\_MOD\_BVALUES, used to
select the mod\_bvalues case of the mod\_vals union. (See: ldap\_modify, mod\_xxx;
LDAP\_MOD\_xxx)  

  




Output :  

(routine)  -  Message ID - This ID can be used in subsequent calls to
ldap\_result to obtain the result(s) of the operation.  

  

-1 - If an error occurs.  

  

  




 **Sample Usage :**



LDAPMod    \*attrs[] = {



                      
{ 0, "cn", { "babs jensen", "babs", 0 } },


                      
{ 0, "sn", { "jensen", 0 } },


                      
{ 0, "objectClass", { "person", 0 } },


                      
0


                    }


 


msgid = ldap\_add( ld,
dn, attrs );


 **See Also :**


**[ldap\_modify](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8A4248301D5126A885256F5C00488A58)**


**[LDAP\_MOD\_xxx](LDAP_MOD_xxx.md)**


**[mod\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/982355D82C2BB9E585256ACE006C08CC)**



----------------------------------------------------------------------------------------------------------


 






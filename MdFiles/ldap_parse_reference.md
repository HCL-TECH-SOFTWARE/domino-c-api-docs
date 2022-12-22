




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



**ldap\_parse\_reference** **- Extract
referrals and controls.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_parse\_reference(**  

      LDAP \*ld,  

      LDAPMessage \*ref,  

      char \*\*\*referralsp,  

      LDAPControl \*\*\*serverctrls,  

      int  freeit**);**



**Description :**



This
function is used to extract referrals and controls from a SearchResultReference
message.


 


Implemented
as a macro:


 


#define
ldap\_parse\_reference(ld, ref, referralsp, serverctrls, freeit)\


             
ND\_ldap\_parse\_reference((ld), (ref), (referralsp), (serverctrls), (freeit))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

ref  -  The reference to parse, as returned by ldap\_result,
ldap\_first\_reference, or ldap\_next\_reference.  

  

freeit  -  A boolean that determines whether the ref parameter is disposed of
or not.  Any non-zero value will free ref after extracting the requested
information.  A zero will not free ref and ldap\_msgfree can be used to free the
result later.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the reference was successfully parsed, or
another LDAP result code if the value of the referrals and controls are
undefined.  

  

  

referralsp  -  An allocated array of character strings.  The elements of the
array are  the referrals (typically LDAP URLs).  The array SHOULD be freed when
no longer in used by calling ldap\_value\_free.  NULL, if the referral URLs are
not returned.  

  

serverctrls  -  An allocated array of controls copied out of the entry. The
control array  SHOULD be freed by calling ldap\_controls\_free.  NULL, if no
controls were returned.  

  




 **See Also :**


**[ldap\_controls\_free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA728E830A49FDFD85256F5C00488A7C)**


**[ldap\_first\_reference](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/01E57F4C687A7B8285256F5C00488A84)**


**[ldap\_msgfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/ACE588BDB8F4BD8C85256F5C00488A70)**


**[ldap\_next\_reference](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/744AB45C6395CFE785256F5C00488A85)**


**[ldap\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5FCB8AF5BD5605D85256F5C00488A6F)**


**[ldap\_value\_free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/69925F36F6F9779185256F5C00488A6D)**



----------------------------------------------------------------------------------------------------------


 






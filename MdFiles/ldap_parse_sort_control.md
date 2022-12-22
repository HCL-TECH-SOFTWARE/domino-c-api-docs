




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



**ldap\_parse\_sort\_control** **- Decode
the server-side sort control return information.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_parse\_sort\_control(**  

      LDAP \*ld,  

      LDAPControl \*\*ctrls,  

      unsigned long  \*returnCode,  

      char \*\*attribute**);**



**Description :**



This
function will decode the server-side sort control return information.


 


Implemented
as a macro:


 


#define
ldap\_parse\_sort\_control(ld, ctrls, returnCode, attribute)\


             
ND\_ldap\_parse\_sort\_control((ld), (ctrls), (returnCode), (attribute))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

ctrls  -  The address of a NULL terminated array of LDAPControl structures,
typically obtained by a call to ldap\_parse\_result.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the sort control was successfully parsed, or
another LDAP result code if not.  

  

  

\*returnCode  -  The sort control result code.  This parameter MUST not be NULL.  

  

attribute  -  If an error occured the server may return a string indicating the
first attribute in the sortkey list that was in error.  If a string is
returned, the memory should be freed with ldap\_memfree.  If NULL, no string is
returned.  

  




 **See Also :**


**[ldap\_memfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F11748459A77A7EE85256F5C00488A7A)**


**[ldap\_parse\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E8CA6F020C2423F385256F5C00488A71)**



----------------------------------------------------------------------------------------------------------


 











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



**LDAP\_xxx\_ATTRS** **-** LDAP return
attributes.


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      LDAP\_ALL\_OPERATIONAL\_ATTRS             -  All operational
attributes are to be returned ("+"). This allows the request that all
operational attributes in addition to any user attributes be returned.  

  

      LDAP\_ALL\_USER\_ATTRS    -  All user attributes are to be returned
("\*"). This allows the request that all user attributes in addition
to any operational attributes be returned  

  

      LDAP\_NO\_ATTRS    -  No attribute types are to be returned by the server.  

  




**Description :**



A list of
attributes to be returned from each entry which matches the search filter.


 **See Also :**


**[ldap\_search](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E36C1C3B5ECB1ED185256F5C00488A76)**


**[ldap\_search\_ext](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B873F652191EC86185256F5C00488A8E)**


**[ldap\_search\_ext\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BECF6A533E7DE04E85256F5C00488A8F)**


**[ldap\_search\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/27CC129059B9B36C85256F5C00488A77)**


**[ldap\_search\_st](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7BF13039F88BCC4185256F5C00488A8D)**



----------------------------------------------------------------------------------------------------------


 











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




**Initial Release 7.0**



**Function : User Registration**



**SECGetSSONameMappingConfig** **- Get name
mapping information from an SSO configuration Document.**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



STATUS
LNPUBLIC **SECGetSSONameMappingConfig(**  

      char \*ServerName,  

      char \*OrgName,  

      char \*ConfigName,  

      BOOL \*retbNameMapping,  

      DWORD  dwReserved,  

      void \*vpReserved**);**



**Description :**



 This
function gets name mapping information from an SSO configuration document if
name mapping is turned on.


 


**Parameters :**



Input :  

ServerName  -  Reserved, must be NULL.  

  

OrgName  -  Optional.  Organization for internet site configuration.  Null if
no organization name is desired.  

  

ConfigName  -  Configuration name, usually "LtpaToken".  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.  

  

  

retbNameMapping  -  TRUE is SSO configuration document has name mapping
enabled.  

  

dwReserved  -  Reserved for future use.  

  

vpReserved  -  Reserved for future use.  

  




 **See Also :**


**[SECTokenGenerate](SECTokenGenerate.md)**


**[SSO\_TOKEN](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/ABE1F48EEAFAA02E85256BC10067CE9E)**



----------------------------------------------------------------------------------------------------------


 






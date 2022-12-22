




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



**Function : ASP; Database**



**NSFGetOrgDir** **- Get an
organization's data directory (Domino ASP environment).**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFGetOrgDir(**  

      char \*UserName,  

      char \*retDir**);**



**Description :**



This
function determines the current organization from the UserName which is passed
in and returns the data directory for that organization.  This function is for
use on a Domino ASP server only.


 


**Parameters :**



Input :  

UserName  -  Pointer to a user's name in canonical format.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully got the path to the organization's data directory.  

  

  

retDir  -  Pointer to a buffer in which the path of the data directory for a
particular user's organization is returned.  Declared buffer must be at least
MAXPATH characters in length.  

  




 




----------------------------------------------------------------------------------------------------------


 






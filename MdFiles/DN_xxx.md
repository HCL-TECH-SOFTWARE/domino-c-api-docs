




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Symbolic Value : Distinguished Name**



**DN\_xxx** **-** Distinguished
name flags.


**----------------------------------------------------------------------------------------------------------**



**#include <dname.h>**


 **Symbolic Values :**      DN\_NONSTANDARD            -  Distinguished name includes
non-standard components.  

  

      DN\_NONDISTINGUISHED    -  Name is a non-distinguished name.  

  

      DN\_CN\_OU\_RDN     -  Obsolete. CN plus OU components of the distinguished
name are relative.  

  

      DN\_O\_C\_RDN          -  Obsolete. O plus C components of the distinguished
name are relative.  

  

      DN\_NONABBREV     -  Name includes components that cannot be abbreviated.  

  




**Description :**



These values
are used in the DN\_COMPONENTS structure to describe a distinguished name.  A
value of 0L means that the distinguished name does not have any of the DN\_xxx
attributes.


 **See Also :**


**[DN\_COMPONENTS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/24D9907B9ECC4FFF8525667700438CC1)**



----------------------------------------------------------------------------------------------------------


 











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



**NAME\_ERROR** **- Check for
naming error.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



Int **NAME\_ERROR(**  

      int  n**);**



**Description :**



This macro
returns zero if the input is NOT one of the possible returned naming error codes
and non-zero if it is.  See LDAP\_xxx(1) 


 


This macro
is defined as follows:


 


#define
NAME\_ERROR(n)   ((n & 0xf0) == 0x20)


 


**Parameters :**



Input :  

n  -  The result of an LDAP operation as returned by ldap\_result or one of the
synchronous API operation calls.  

  




Output :  

(routine)  -  Zero if the input is NOT one of the possible returned naming
error codes and non-zero if it is.    

  

  




 




----------------------------------------------------------------------------------------------------------


 






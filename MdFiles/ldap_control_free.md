




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



**ldap\_control\_free** **- Dispose
of a single control.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



void
LNPUBLIC **ldap\_control\_free(**  

      LDAPControl \*ctrl**);**



**Description :**



This
function is used to dispose of a single control.


 


Implemented
as a macro:


 


#define
ldap\_control\_free(ctrl)         ND\_ldap\_control\_free((ctrl))


 


**Parameters :**



Input :  

ctrl  -  Pointer to an LDAPControl structure.  See LDAPControl.  If NULL, this
call does nothing.  

  




 


 




----------------------------------------------------------------------------------------------------------


 






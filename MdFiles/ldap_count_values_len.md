




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



**ldap\_count\_values\_len** **- Count the
number of berval structures.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_count\_values\_len(**  

      struct berval \*\*vals**);**



**Description :**



This
function is used to count the number of berval structures in the array.


 


Implemented
as a macro:


 


#define
ldap\_count\_values\_len(vals)            ND\_ldap\_count\_values\_len((vals))


 


**Parameters :**



Input :  

vals  -  The values returned by a previous call to ldap\_get\_values\_len.  

  




Output :  

(routine)  -  Number of berval structures in the array.  

  

-1 - If an error occurs such as an invalid input for values.  

  

  




 **See Also :**


**[ldap\_get\_values\_len](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DF025868229D9A2E85256F5C00488A6A)**



----------------------------------------------------------------------------------------------------------


 






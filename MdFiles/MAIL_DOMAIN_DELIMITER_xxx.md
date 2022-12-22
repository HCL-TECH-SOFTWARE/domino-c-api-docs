




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




 


**Symbolic Value : Mail**



**MAIL\_DOMAIN\_DELIMITER\_xxx** **-** Domain name
delimiters.


**----------------------------------------------------------------------------------------------------------**



**#include <mail.h>**


 **Symbolic Values :**      MAIL\_DOMAIN\_DELIMITER             -  Domain name delimiter
string for a Domino mail address.  

  

      MAIL\_DOMAIN\_DELIMITER\_CHAR   -  Domain name delimiter character for a
Domino mail address.  

  

      MAIL\_DOMAIN\_DELIMITER\_SPACES          -  Domain name delimiter string for
a Domino mail address. Whether or not this string has spaces depends on the
value of MAIL\_DOMAIN\_DELIMITER\_NOSPACES.  

  

      MAIL\_DOMAIN\_DELIMITER\_NOSPACES     -  A value set to 1 so that there are
no spaces in the string defined by MAIL\_DOMAIN\_DELIMITER\_SPACES; for SMTP
compatibility.  

  




**Description :**



These are
the delimiters used to specify a domain name.


 **See Also :**


**[MAIL\_SERVER\_DELIMITER\_CHAR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA8EAF77F5D0DAD18525620A005888B2)**



----------------------------------------------------------------------------------------------------------


 






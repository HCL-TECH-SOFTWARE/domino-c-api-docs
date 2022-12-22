




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




 


**Symbolic Value : Access Control List**



**ACL\_BITPRIVxxx** **-** Release 2
access privileges.


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**


 **Symbolic Values :**      ACL\_BITPRIVCOUNT           -  Number of bits dedicated to
Release 2 privileges.  

  

      ACL\_BITPRIVS        -  Bit mask for Release 2 privileges.  

  

      ACL\_BITPRIV\_LEFT\_PAREN           -  Opening delimiter for Release 2
privilege names.  

  

      ACL\_BITPRIV\_RIGHT\_PAREN         -  Closing delimiter for Release 2
privilege names.  

  




**Description :**



Originally,
Notes supported 5 access privileges.  Beginning with Release 3 of Notes, those
privileges are stored as 5 of the bits in the privileges bit array in an Access
Control List.  Names of privileges are enclosed in parenthesis.


 **See Also :**


**[ACL\_PRIVCOUNT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5E96D013CF3AC495852561E0006F157D)**


**[ACL\_PRIVILEGES](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0007004A00E8002385255E3F00027E24)**


**[ACL\_PRIVNAMEMAX](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8421D8769B42A715852561E0006F157F)**


**[ACL\_PRIVSTRINGMAX](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/62408E64FB7B3CD8852561E0006F157C)**



----------------------------------------------------------------------------------------------------------


 






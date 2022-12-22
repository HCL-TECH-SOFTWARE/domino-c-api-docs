




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




 


**Symbolic Value : Error Handling**



**NETPKG\_xxx** **-** Offsets
within PKG\_NETDRVLCL for local network drivers.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**


 **Symbolic Values :**      NETPKG\_TCP          -  TCP status code offset.  

  

      NETPKG\_ATALK      -  ATALK status code offset  

  

      NETPKG\_NWSPX    -  SPX status code offset.  

  




**Description :**



These are
the offsets within PKG\_NETDRVLCL status codes used for local network drivers. 
On Unix, since tcp is compiled into Domino, their strings must have unique
IDs.  There is a separate package for all drivers which are optional and each
optional driver package has its own offsets for first string.


 **See Also :**


**[PKG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/32ECB9B5852E43FE85256984004DEC2B)**



----------------------------------------------------------------------------------------------------------


 






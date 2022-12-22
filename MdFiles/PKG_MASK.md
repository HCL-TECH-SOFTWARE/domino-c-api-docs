




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



**PKG\_MASK** **-** Mask to
obtain package code.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



**Description :**



The 16-bit
value of a STATUS error code consists of the following fields:


 


1 bit:     Flag
bit - status message has been displayed


1 bit:     Flag
bit - status message came from a remote machine (i.e., a server)


6 bits:   "Package"
code or partial package code


8 bits:   Status
value or partial package code plus status value


 


This mask is
used to obtain the 6 bit package or subsystem code from a STATUS value.  This
mask is useful only with package codes that use the designated 6 bits of the
status code.  Newer package codes may use more than 6 bits (leaving fewer than
8 bits for the status value).  


 **See Also :**


**[PKG](PKG.md)**


**[STATUS](STATUS.md)**



----------------------------------------------------------------------------------------------------------


 





